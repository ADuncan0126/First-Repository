---
icon: users
description: Run the Truverion 1:N Face Identification demo and interpret ranked gallery search results.
---

# Implement 1:N Face Identification

Search a gallery of face photos using one **probe photo**, the image you want to identify. The Linux demo compares the probe with each decodable gallery photo and ranks usable results by similarity. Use 1:N search when the identity is unknown. When you already have a claimed identity and one reference photo, use [1:1 selfie-to-ID comparison](match-a-selfie-to-an-id-portrait.md).

![One probe photo is compared with each gallery photo, then usable scores are ranked.](../.gitbook/assets/face-identification-workflow.svg)

The demo accepts **1–50 gallery photos per search**. Each request supplies its own gallery. A persistent enrollment database and its access controls belong in your application.

## <i class="fa-box">:box:</i> Set up the Linux demo

1. Obtain `Truverion-Face-Identification-Demo.zip` through [Contact & Support](../resources-and-support/contact-and-support.md) and extract it on **Ubuntu 22.04 x86-64**.
2. Copy the compatible Linux Face Recognition SDK’s complete `engine/` and `dependency/` directories to the project root. The adapter uses `engine.header.compare_face(image1, image2, threshold)`.
3. From the project root, run `./install.sh`. Add the authorized offline `license.txt` at the project root or set `FR_LICENSE_KEY` for online activation.
4. Run `./run_all.sh` to start both services, `./run_all.sh -s` for Streamlit only, or `./run_all.sh -f` for FastAPI only.

Streamlit runs on `http://127.0.0.1:8501`. With FastAPI running, use `http://127.0.0.1:8000/health` to check readiness and `http://127.0.0.1:8000/docs` to explore the request and response.

## <i class="fa-images">:images:</i> Search a gallery

1. Upload approved gallery photos using one clear face per image. Preview the gallery before running the search.
2. Add one probe photo. Use a sharp, evenly lit image with the face in frame.
3. Run the search and review the probe and top candidate side by side. Check the ranked cards for similarity and threshold decisions, including any skipped comparisons.
4. Use one known same-person probe and one probe from someone absent from the gallery to exercise both match and no-match cases before integration.

## <i class="fa-code">:code:</i> Call the search API

Send a multipart `POST /api/search` request with one `probe` file and one `gallery` field per gallery photo.

```bash
curl http://127.0.0.1:8000/api/search \
  -F 'probe=@probe.jpg' \
  -F 'gallery=@portrait-a.jpg' \
  -F 'gallery=@portrait-b.jpg' \
  -F 'threshold=0.67' \
  -F 'top_k=5'
```

| Input | Demo behavior |
| --- | --- |
| `threshold` | Optional, from 0 to 1. Defaults to `0.67`. A candidate meets the threshold when its score is at or above it. |
| `top_k` | Optional, from 1 to 50. Defaults to `5`. Limits the returned list after ranking. |
| Images | Up to 15 MiB and 20 megapixels per photo, and up to 64 MiB for the probe and gallery combined. |

Each returned candidate includes a 1-based `gallery_index`, `label`, `similarity`, and `meets_threshold`. The index distinguishes photos with the same filename. Use `scored_count` to see how many pairs had usable scores and `skipped` to see why entries were excluded. `match_count` counts all qualifying comparisons before the `top_k` limit.

## <i class="fa-code-branch">:code-branch:</i> Interpret the result

| Result | Meaning and next action |
| --- | --- |
| `match` | At least one gallery photo reached the threshold. Treat the ranked results as candidates. Send ambiguous results to review or request another verification method. |
| `no_match` | At least one comparison was scored, but none reached the threshold. The candidate list can still contain below-threshold scores. |
| `no_usable_comparisons` | The engine returned no usable pair scores. Inspect the skipped reasons and try suitable images before drawing a conclusion. |
| HTTP `413` or `422` | Check upload limits, whether the probe can be decoded, and the submitted form fields. |
| HTTP `503` | Check SDK readiness, native dependencies, and activation. Retry only after resolving the cause or when the failure is transient. |

## <i class="fa-sliders">:sliders:</i> Evaluate before deployment

- Calibrate the threshold with enrolled and unenrolled probes. Evaluate on separate identities and use representative gallery sizes, capture devices, and lighting. The demo default is a starting value for testing.
- Report **false positive identification rate (FPIR)** for unenrolled probes that return at least one candidate above the threshold and **false negative identification rate (FNIR)** for enrolled probes whose correct candidate is missed at the configured threshold and rank. Track unusable captures and service errors separately. See [NIST FRTE 1:N Identification](https://pages.nist.gov/frvt/html/frvt1N.html).
- For a persistent gallery, enroll only authorized subjects, restrict access, define retention and deletion, and keep face images and templates out of routine logs. Validate recognition performance again when the engine, capture process, or gallery changes.
