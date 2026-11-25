---
icon: layer-group
---

# Platform Compatibility

| SDK | Documented Linux demo | Android demo | iOS |
| --- | --- | --- | --- |
| Face Recognition | Ubuntu 22.04 | [Core and Pro](../face-biometrics/face-recognition-sdk/mobile/android/README.md) | Confirm package availability |
| Face Liveness Detection | Ubuntu 22.04 | [Core and Pro](../face-biometrics/face-liveness-detection-sdk/mobile/android/README.md) | Confirm package availability |
| ID Document Recognition | Ubuntu 22.04 | [ID Scan](../id-documents/id-document-recognition-sdk/mobile/android/README.md) | Confirm package availability |
| ID Document Liveness Detection | Ubuntu 22.04 | No demo documented | No demo documented |

Android samples target physical ARM devices running Android 7.0 or newer. The face projects use SDK Platform 33, and ID Scan uses SDK Platform 34. ID Scan requires a separate licensed engine.

Use native assets matching the package architecture and operating-system release. Use vendor-compatible OpenSSL libraries for Linux demos. Use the release materials to confirm availability for other integration targets.
