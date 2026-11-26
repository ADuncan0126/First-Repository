---
icon: key
---

# Licensing & Activation

Request a license for the exact `applicationId` in `app/build.gradle`.

The sample uses `tech.truverion.id.rec`. Its namespace is also `tech.truverion.id.rec`.

Save the license as `app/src/main/assets/license` with no extension, then rebuild the app. The sample reads that asset at startup, calls `IDSDK.setActivation(license)`, then initializes the SDK after activation succeeds. Check the home screen for SDK status before testing.

| Symptom | Check |
| --- | --- |
| License asset missing | Check the asset path and confirm the file is named `license`. |
| Activation fails | Confirm that the license matches both the exact application ID and the engine release. Check whether the license has expired. |
| Activation succeeds but initialization fails | Check the engine file, its assets, and device ABI. Use the initialization code shown by the app when requesting support. |

Keep license files and activation values out of public repositories and logs.

## <i class="fa-arrow-right">:arrow-right:</i> Verify your license

Check that the home screen reports the SDK ready after rebuilding. Run one authorized sample before integrating. [Sample Application](sample-application.md).
