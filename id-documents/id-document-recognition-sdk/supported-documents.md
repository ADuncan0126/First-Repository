# Supported Documents

## Supported Documents

The adapter provides ID-card, credit-card, and barcode operations. Countries, document types, sides, scripts, and extracted fields depend on the engine build.

For each release, use its vendor coverage list, then test approved front and back fixtures. Record the returned field names and confidence or error conditions. Do not assume a field exists because another document returned it. Request the front image first; include a back image only when available. Send uncertain classification, missing fields, or unreadable images to recapture or manual review.

The adapter calls `ocr_id_card`, `ocr_credit_card`, and `ocr_barcode`. Sources: `shared/sdk.py`, `engine/header.py`.
