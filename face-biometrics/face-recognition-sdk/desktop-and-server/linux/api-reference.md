---
icon: code
---

# API Reference

Compare two images with the Linux demo API.

### <i class="fa-link">:link:</i> **Endpoints**

<table><thead><tr><th width="75">Route</th><th width="260">EndPoint</th><th>Description</th></tr></thead><tbody><tr><td><code>GET</code></td><td>/health</td><td>Check the service status.</td></tr><tr><td><code>POST</code></td><td>/api/compare_face</td><td>Compare two images using file upload<br>(multipart/form-data).</td></tr><tr><td><code>POST</code></td><td>/api/compare_face_base64</td><td>Compare two images using Base64-encoded images(JSON).</td></tr></tbody></table>

### <i class="fa-image">:image:</i> **Compare images**

Use the Linux demo API to compare two face images and get a similarity score.

{% tabs %}
{% tab title="File Upload" icon="upload" %}
<table><thead><tr><th width="128">Field</th><th width="108">Type</th><th>Description</th></tr></thead><tbody><tr><td>image1</td><td><code>file</code></td><td>First face image (e.g., JPG, PNG).</td></tr><tr><td>image2</td><td><code>file</code></td><td>Second face image (e.g., JPG, PNG).</td></tr></tbody></table>

{% hint style="info" %}
**Note:** The default threshold is 0.67
{% endhint %}
{% endtab %}

{% tab title="Base64 JSON" icon="code" %}
`POST`            /api/compare\_face\_base64          `application/json`   &#x20;

{% code overflow="wrap" %}
```
{
    "image1":"<base64 reference image>",
    "image2":"<base64 comparison image>",
    "threshold": 0.67
}   
```
{% endcode %}

{% hint style="info" %}
**Note:** Both images are required. The default threshold is 0.67
{% endhint %}
{% endtab %}
{% endtabs %}

### <i class="fa-brackets-curly">:brackets-curly:</i> Response fields

The compare endpoints return a JSON object with the following fields.

<table><thead><tr><th width="219">Field</th><th width="87">Type</th><th>Description</th></tr></thead><tbody><tr><td>data.result</td><td><code>string</code></td><td>Recognition outcome.</td></tr><tr><td>data.similarity</td><td><code>number</code></td><td>Score when available.</td></tr><tr><td>data.threshold</td><td><code>number</code></td><td>The threshold used for the comparison (e.g., 0.67).</td></tr><tr><td>data.processing_time_ms</td><td><code>number</code></td><td>Processing time in milliseconds.</td></tr></tbody></table>

### <i class="fa-triangle-exclamation">:triangle-exclamation:</i> **Errors**

The API may return the following error responses.

<table><thead><tr><th width="128">HTTP Status</th><th>Description</th></tr></thead><tbody><tr><td> <mark style="color:red;background-color:$danger;">413</mark> </td><td><strong>File upload</strong> limit exceeded.</td></tr><tr><td> <mark style="color:red;background-color:$danger;">422</mark> </td><td><strong>Invalid input.</strong> Missing, empty, or unsupported image data.</td></tr><tr><td> <mark style="color:red;background-color:$danger;">503</mark> </td><td><strong>SDK unavailable.</strong> The face recognition SDK is not available or not initialized.</td></tr></tbody></table>

