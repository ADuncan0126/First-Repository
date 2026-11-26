---
icon: play
---

# Sample Application

| Edition | Launcher name | Application ID | Workflows |
| --- | --- | --- | --- |
| Core | Face Verify | `tech.truverion.face.core` | Face recognition and liveness-gated recognition |
| Pro | Face Verify & Analyze | `tech.truverion.face.pro` | Core workflows plus face analysis |

Follow [Installation](installation.md) and [Licensing & Activation](licensing-and-activation.md), then launch the app and check the SDK status.

1. Register one face with the registration camera or a selected photo, then save the profile under a name.
2. Choose **Face recognition** to compare the camera input with saved profiles. Choose **Liveness + recognition** to require a passing liveness check before matching.
3. Review the matched profile and similarity score. In the liveness-enabled flow, the preview also shows the liveness score when available.
4. On **Pro**, open **Face analysis** to inspect the additional attributes available from a camera capture or photo.

Obtain the Core or Pro project ZIP through your authorized package channel. Each archive includes its edition’s face engine and requires its own license.

## <i class="fa-arrow-right">:arrow-right:</i> Connect the demo to your integration

Use the API reference to trace which calls produce the result on the demo screen. [API Reference](api-reference.md).
