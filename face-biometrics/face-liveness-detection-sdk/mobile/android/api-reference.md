---
icon: code
---

# API Reference

## Calls used by the Android sample

| Call | Role in the face demo |
| --- | --- |
| `FaceSDK.setActivation(license)` | Activates the selected edition. Continue when the return code is `SDK_SUCCESS`. |
| `FaceSDK.init(context.assets)` | Initializes the engine with the Android asset manager. |
| `FaceSDK.yuv2Bitmap(image, width, height, orientation)` | Converts a camera frame to a bitmap. |
| `FaceSDK.faceDetection(bitmap, params)` | Returns face detections. Enable `FaceDetectionParam.check_liveness` in the liveness flow to read the detection’s `liveness` score. |
| `FaceSDK.templateExtraction(bitmap, face)` | Creates a template for a detected face. |
| `FaceSDK.similarityCalculation(template, enrolledTemplate)` | Compares two templates and returns a similarity score. |

The Kotlin samples import `com.bio.facesdk.FaceSDK` and `com.bio.facesdk.FaceDetectionParam`. Require one usable face for enrollment. The demo checks the liveness score against its configured threshold before template comparison. Treat recapture, failure to match, and SDK errors as separate outcomes.

Use the selected engine’s release reference for additional parameters and return codes.

## <i class="fa-arrow-right">:arrow-right:</i> Test the call sequence

Run the sample with one usable input and one unusable input. Confirm the app handles processing errors separately from recognition results. [Sample Application](sample-application.md).
