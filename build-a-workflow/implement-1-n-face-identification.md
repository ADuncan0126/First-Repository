# Implement 1:N Face Identification

## Implement 1:N Face Identification

Detect one face, create a template, then search an enrolled gallery. Store templates with consent, retention, and deletion controls.

Treat a candidate as a result, not an identity decision. Apply a calibrated threshold and handle no-candidate, multiple-candidate, and processing-error outcomes.

For an unusable capture, request a new image before creating a template. On a processing error, retain no partial decision and retry only after resolving the error.
