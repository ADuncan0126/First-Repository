---
icon: users
description: Enroll photos in a PostgreSQL gallery and run 1:N face searches with the Truverion Linux demo.
---

# Implement 1:N Face Identification

Enroll reference photos once, then search the saved gallery with a **probe photo**. The Linux demo extracts a face embedding for each enrolled photo and stores it in PostgreSQL with pgvector. Streamlit and FastAPI use the same gallery. For a claimed identity with one reference portrait, use [1:1 selfie-to-ID comparison](match-a-selfie-to-an-id-portrait.md).

![Enrollment stores reference embeddings in PostgreSQL. A probe embedding searches the saved gallery and returns ranked candidates.](../.gitbook/assets/face-identification-workflow.svg)

## <i class="fa-box">:box:</i> Set up the Linux demo

Use **Ubuntu 22.04 x86-64**. Obtain `Truverion-Face-Identification-Demo.zip` through [Contact & Support](../resources-and-support/contact-and-support.md) and extract it.

1. Copy the compatible Face Identification SDK's complete `engine/` and `dependency/` directories into the project root. The adapter uses Recognito's `engine.header.detect_face_api(image)` and reads its 2048-byte template as 512 little-endian float32 values.
2. From the extracted project directory, run `./install.sh`.
3. Place an authorized offline `license.txt` at the project root or set `FR_LICENSE_KEY` for online activation.

### Configure PostgreSQL and pgvector

Use matching server and extension versions. For PostgreSQL 16 on Ubuntu, enable the [official PostgreSQL APT repository](https://www.postgresql.org/download/linux/ubuntu/) if needed, then run:

```bash
sudo apt update
sudo apt install postgresql-16 postgresql-16-pgvector
sudo systemctl enable --now postgresql
```

For a fresh local setup, run these commands from the extracted project directory as your regular Linux user. Skip role or database creation if it already exists and verify that the role owns the database or has the necessary privileges.

```bash
sudo -u postgres createuser "$(id -un)"
sudo -u postgres createdb --owner="$(id -un)" truverion
sudo -u postgres psql --dbname=truverion --set=ON_ERROR_STOP=1 -c 'CREATE EXTENSION IF NOT EXISTS vector;'
psql --dbname=truverion --set=ON_ERROR_STOP=1 --file=database/schema.sql
```

Both services default to the local `truverion` database as the current Linux user. Set `TRUVERION_DATABASE_URL` before launch if you use another database, role, or port. If you have multiple PostgreSQL clusters, use the same cluster for schema setup and application launch.

### Launch and verify

- Run `./run_all.sh` for both services, `./run_all.sh -s` for Streamlit only, or `./run_all.sh -f` for FastAPI only.
- Open Streamlit at `http://127.0.0.1:8501` or the API docs at `http://127.0.0.1:8000/docs`.
- Check SDK activation at `http://127.0.0.1:8000/health`. Check database connectivity separately with `GET /api/gallery`. An empty gallery on a fresh install is expected.

## <i class="fa-images">:images:</i> Enroll and search

1. In Streamlit, select reference photos with one clear face per photo and click **Enroll photos**. The database stores the embedding, filename, preview, and a stable photo ID.
2. Confirm the enrolled photos appear in the gallery. Use **Manage enrolled photos** to remove an entry.
3. Upload a probe photo and run the search. Review the enrolled filename, similarity score, and threshold decision in the ranked results. Try a photo of someone whose reference is enrolled, then try a photo of someone absent from the gallery.
4. If you used an earlier SQLite or Qdrant gallery, re-enroll the original photos to populate PostgreSQL.

Enroll up to **50 photos or 49 MiB per batch**. Each photo can be up to **15 MiB and 20 megapixels**. These upload limits apply to a batch, while the saved gallery can contain photos from multiple batches.

## <i class="fa-code">:code:</i> Use the FastAPI endpoints

| Endpoint | Purpose |
| --- | --- |
| `POST /api/gallery` | Enroll photos using repeated multipart `gallery` fields. Returns the new photo UUIDs. |
| `GET /api/gallery` | List enrolled photos. Pass the returned `next_cursor` as `cursor` for the next page. |
| `DELETE /api/gallery/{photo_id}` | Remove an enrolled photo by UUID. |
| `POST /api/search` | Search the saved gallery with one multipart `probe` file. |

```bash
curl http://127.0.0.1:8000/api/gallery \
  -F 'gallery=@portrait-a.jpg' \
  -F 'gallery=@portrait-b.jpg'

curl http://127.0.0.1:8000/api/search \
  -F 'probe=@probe.jpg' \
  -F 'threshold=0.67' \
  -F 'top_k=5'
```

The saved search defaults to a threshold of `0.67` and returns up to five candidates. Set `top_k` from 1 to 50. Each candidate includes `gallery_id`, `label`, `similarity`, and `meets_threshold`. `gallery_size` counts all enrolled photos, and `match_count` counts qualifying candidates in the returned list.

For a one-off search, send repeated `gallery` fields with the probe to `POST /api/search`. This uses pairwise SDK scoring and has a **64 MiB** combined upload limit. Calibrate the two search modes separately because their scores come from different methods.

## <i class="fa-sliders">:sliders:</i> Interpret results and calibrate

Saved-gallery search ranks embeddings by exact cosine similarity and normalizes the score with `(cosine + 1) / 2`. A candidate passes when its score is **strictly greater than** the threshold.

| Outcome | What to check |
| --- | --- |
| `match` | At least one returned candidate exceeds the threshold. Review the ranked candidates before making an identity decision. |
| `no_match` | No returned candidate exceeds the threshold. Below-threshold candidates can still appear. |
| HTTP `409` | The saved gallery is empty. Enroll reference photos first. |
| HTTP `413` or `422` | Check upload limits, image quality, and request fields. |
| HTTP `503` | Check SDK status and database connectivity separately. Verify the license, database role, pgvector extension, and schema. |

Calibrate with enrolled and unenrolled probes under representative capture conditions and gallery sizes. Measure false positive and false negative identification rates at the selected threshold and rank. See [NIST FRTE 1:N Identification](https://pages.nist.gov/frvt/html/frvt1N.html).

Restrict gallery access, define retention and deletion for embeddings and previews, and keep biometric data and credentials out of routine logs.
