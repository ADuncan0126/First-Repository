---
icon: code
---

# API Reference

Extract data from identify document images.

### <i class="fa-id-card">:id-card:</i> Identify document recognition

Submit fron and back images to read an identify document.

{% hint style="info" %}
**Default limit:** 15MB per image.
{% endhint %}

### <i class="fa-image">:image:</i> File upload

{% code overflow="wrap" %}
```
POST   /api/read_idcard
```
{% endcode %}

Send multipart/form-data with `image` (front), `image2` (back), or both

### <i class="fa-code">:code:</i> **Base64 JSON**

{% code overflow="wrap" %}
```
POST   /api/read_idcard_base64
```
{% endcode %}

Send application/json with Base64-encoded `image` (required) and `image2` (optional).

### <i class="fa-brackets-curly">:brackets-curly:</i> Response fields

<table><thead><tr><th width="274">Field</th><th>Type</th><th>Description</th></tr></thead><tbody><tr><td><code>status</code></td><td>String</td><td>API response status</td></tr><tr><td><code>data</code></td><td>Object</td><td>SDK response</td></tr></tbody></table>

### <i class="fa-wave-pulse">:wave-pulse:</i> **SDK status**

`Get  /health`            Reports SDK read and activation state.

### <i class="fa-triangle-exclamation">:triangle-exclamation:</i> **Errors**

<table><thead><tr><th width="154">HTTP Status</th><th>Description</th></tr></thead><tbody><tr><td><code>400</code></td><td>Invalid input.</td></tr><tr><td><code>413</code></td><td>Image exceeds size limit.</td></tr><tr><td><code>422</code></td><td>Request validation failed.</td></tr><tr><td><code>500</code></td><td>Recogniton error.</td></tr><tr><td><code>503</code></td><td>SDK or activation error.</td></tr></tbody></table>

### <i class="fa-link">:link:</i> Additional e**ndpoints**

| Operation        | File upload (POST) | Base64 JSON (POST)         |
| ---------------- | ------------------ | -------------------------- |
| Payment card OCR | /api/read\_credit  | /api/read\_credit\_base64  |
| Barcode reading  | /api/read\_barcode | /api/read\_barcode\_base64 |
