---
icon: code
---

# API Reference

## Calls used by the Android sample

| Call | Role in ID Scan |
| --- | --- |
| `IDSDK.setActivation(license)` | Activates the engine. Continue when the return code is `SDK_SUCCESS`. |
| `IDSDK.init(context)` | Initializes the engine after activation. The sample passes its activity. |
| `IDSDK.yuv2Bitmap(image, width, height, orientation)` | Converts a camera frame to a bitmap. A gallery image can be decoded directly to a bitmap. |
| `IDSDK.idcardRecognition(bitmap)` | Processes one document image. The app parses the SDK response for document information and available images. |

The Kotlin sample imports `com.bio.idsdk.IDSDK`. Handle unknown documents and recognition errors before displaying extracted results. Use the licensed engine’s release reference for the full response schema and supported document types.

## <i class="fa-arrow-right">:arrow-right:</i> Test the call sequence

Run the sample with one usable input and one unusable input. Confirm the app handles processing errors separately from recognition results. [Sample Application](sample-application.md).
