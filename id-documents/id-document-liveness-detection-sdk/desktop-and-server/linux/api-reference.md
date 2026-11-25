---
icon: code
---

# API Reference

Check a single identify document image for signs of spoofing.

### <i class="fa-link">:link:</i> E**ndpoints**

| Method | Endpoint                | Description       |
| ------ | ----------------------- | ----------------- |
| `GET`  | /health                 | SDK configuration |
| `POST` | /api/v1/check           | File upload       |
| `POST` | /process\_image         | File upload alia  |
| `POST` | /process\_image\_base64 | Base64 JSON       |

### <i class="fa-image">:image:</i> Check a document image

Send one image using multipart form data or Base64 JSON

{% tabs %}
{% tab title="File Upload" %}
<table><thead><tr><th width="86">Field</th><th width="97">Type</th><th width="102">Required</th><th>Description</th></tr></thead><tbody><tr><td><code>image</code></td><td>File</td><td>Yes</td><td>JPEG, PNG, WebP, BMP, or TIFF</td></tr></tbody></table>

{% hint style="info" %}
Maximum 15 MB and 25 megapixels. Default threshold is 0.5.
{% endhint %}
{% endtab %}

{% tab title="Base64 JSON" %}
<table><thead><tr><th width="86">Field</th><th width="97">Type</th><th width="102">Required</th><th>Description</th></tr></thead><tbody><tr><td><code>base64</code></td><td>File</td><td>Yes</td><td>Base64 image bytes or an image data URL.</td></tr></tbody></table>

{% hint style="info" %}
Send application/json. Maximum decoded size is 15MB.
{% endhint %}


{% endtab %}
{% endtabs %}

### <i class="fa-brackets-curly">:brackets-curly:</i> **Response fields**

The API returns a JSON object for both genuine and spoof outcomes.

<table><thead><tr><th width="260"></th><th width="114"></th><th></th></tr></thead><tbody><tr><td><code>status</code></td><td>String</td><td>Returns ok for a completed check</td></tr><tr><td><code>result</code></td><td>String</td><td>Genuine or Spoof</td></tr><tr><td><code>threshold</code></td><td>Number</td><td>Threshold applied to all three integrity scores.</td></tr><tr><td><code>scores.screen_replay</code></td><td>Number</td><td>Screen replay integrity score.</td></tr><tr><td><code>scores.portrait_replacement</code></td><td>Number</td><td>Portrait replacement integrity score.</td></tr><tr><td><code>scores.printed_copy</code></td><td>Number</td><td>Printed copy integrity score.</td></tr><tr><td><code>raw_sdk_result</code></td><td>Object</td><td>Original SDK response.</td></tr></tbody></table>

Any score below the threshold produces a spoof result.

### <i class="fa-wave-pulse">:wave-pulse:</i> **SDK status**

**`GET  /health` &#x20;**&#x20;   Reports whether the engine, model, and license are configured.

### <i class="fa-triangle-exclamation">:triangle-exclamation:</i> **Errors**

<table><thead><tr><th width="145">HTTP Status</th><th>Description</th></tr></thead><tbody><tr><td> <mark style="color:$danger;background-color:$danger;">413</mark> </td><td>Image exceeds the byte limit.</td></tr><tr><td> <mark style="color:$danger;background-color:$danger;">415</mark> </td><td>Unsupported upload content type.</td></tr><tr><td> <mark style="color:$danger;background-color:$danger;">422</mark> </td><td>Request validation failed, image is empty, or Base64 is invalid</td></tr><tr><td> <mark style="color:$danger;background-color:$danger;">503</mark> </td><td>SDK or worker error, including image decoding or unreadable documents.</td></tr></tbody></table>

