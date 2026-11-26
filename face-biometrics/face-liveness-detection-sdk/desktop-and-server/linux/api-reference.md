---
icon: code
---

# API Reference

Check face liveness from a single image.

### <i class="fa-link">:link:</i> **Endpoints**

<table><thead><tr><th width="88">Method</th><th width="260">Endpoint</th><th>Description</th></tr></thead><tbody><tr><td><code>GET</code></td><td>/health</td><td>SDK metadata</td></tr><tr><td><code>POST</code></td><td>/api/check_liveness</td><td>File upload</td></tr><tr><td><code>POST</code></td><td>/api/check_liveness_base64</td><td>Base64 JSON</td></tr></tbody></table>

### <i class="fa-image">:image:</i> **Check face liveness**

Submit one face image and review the liveness result and score.

{% tabs %}
{% tab title="File Upload" icon="upload" %}
<table><thead><tr><th width="128">Field</th><th width="108">Type</th><th>Required</th><th>Description</th></tr></thead><tbody><tr><td><strong>image</strong></td><td>File</td><td>Yes</td><td>Image to analyze</td></tr><tr><td><strong>threshold</strong></td><td>Number</td><td>No</td><td>Defaults to 0.5</td></tr></tbody></table>

{% hint style="info" %}
Maximum 15MB and 25 megapixels.
{% endhint %}
{% endtab %}

{% tab title="Base64 JSON" icon="code" %}
**`POST`            /api/check\_liveness\_base64**&#x20;

{% code overflow="wrap" %}
```
{
    "image1":"<base64-encoded image>",
    "threshold": 0.5
}   
```
{% endcode %}

Use raw Base64 or a data URL. The threshold is optional.

{% hint style="info" %}
Maximum 15MB and 25 megapixels.
{% endhint %}
{% endtab %}
{% endtabs %}

### <i class="fa-brackets-curly">:brackets-curly:</i> **Response fields**

<table><thead><tr><th width="226">Field</th><th width="195">Type</th><th>Description</th></tr></thead><tbody><tr><td><strong>data.result</strong></td><td>String</td><td>Liveness outcome</td></tr><tr><td><strong>data.liveness_score</strong></td><td>Number or null</td><td>Liveness score</td></tr><tr><td><strong>data.threshold</strong></td><td>Number</td><td>Threshold used</td></tr><tr><td><strong>data.processing_time_ms</strong></td><td>Number</td><td>SDK call duration in ms</td></tr><tr><td><strong>data.face_rect</strong></td><td>Object or null</td><td>Face bounding box</td></tr><tr><td><strong>data.angles</strong></td><td>Object or null</td><td>Head pose</td></tr></tbody></table>

### <i class="fa-triangle-exclamation">:triangle-exclamation:</i> **Errors**

The API may return the following error responses.

<table><thead><tr><th width="128">HTTP Status</th><th>Description</th></tr></thead><tbody><tr><td> <mark style="color:red;background-color:$danger;">400</mark> </td><td>Invalid input</td></tr><tr><td> <mark style="color:red;background-color:$danger;">413</mark> </td><td>Image exceeds byte limit</td></tr><tr><td> <mark style="color:red;background-color:$danger;">422</mark> </td><td>Request validation failed</td></tr><tr><td> <mark style="color:red;background-color:$danger;">503</mark> </td><td>SDK or activation error</td></tr></tbody></table>

## <i class="fa-play">:play:</i> Try the API

Start FastAPI from the [sample guide](sample-application.md) and use the URL printed by the launcher. Check service readiness first, then submit an authorized sample. Ask for a new capture if the face is obscured or missing.
