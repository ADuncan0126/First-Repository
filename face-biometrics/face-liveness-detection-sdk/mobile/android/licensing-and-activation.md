---
icon: key
---

# Licensing & Activation

Request a license for the exact `applicationId` in `app/build.gradle`.

| Edition | Launcher name | Application ID | Workflows |
| --- | --- | --- | --- |
| Core | Face Verify | `tech.truverion.face.core` | Face recognition and liveness-gated recognition |
| Pro | Face Verify & Analyze | `tech.truverion.face.pro` | Core workflows plus face analysis |

Both face projects use the source namespace `tech.truverion.face`. Use the edition’s application ID when requesting the license.

Save the license as `app/src/main/assets/license` with no extension, then rebuild the app. The sample reads that asset at startup, calls `FaceSDK.setActivation(license)`, then initializes the SDK after activation succeeds. Check the home screen for SDK status before testing.

| Symptom | Check |
| --- | --- |
| License asset missing | Check the asset path and confirm the file is named `license`. |
| Activation fails | Confirm that the license matches both the exact application ID and the engine release. Check whether the license has expired. |
| Activation succeeds but initialization fails | Check the engine file, its assets, and device ABI. Use the initialization code shown by the app when requesting support. |

Keep license files and activation values out of public repositories and logs.
