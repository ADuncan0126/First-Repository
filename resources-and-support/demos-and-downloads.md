---
icon: download
description: Run local Truverion samples for each SDK workflow.
---

# Demos & Downloads

## Linux demos

Choose one of the four Ubuntu 22.04 sample guides below. Each guide explains what the demo does and how to run its Streamlit or FastAPI interface. If you need a package, an engine, or a license, [contact Truverion](contact-and-support.md).

{% content-ref url="../face-biometrics/face-recognition-sdk/desktop-and-server/linux/sample-application.md" %}
[sample-application.md](../face-biometrics/face-recognition-sdk/desktop-and-server/linux/sample-application.md)
{% endcontent-ref %}

{% content-ref url="../face-biometrics/face-liveness-detection-sdk/desktop-and-server/linux/sample-application.md" %}
[sample-application.md](../face-biometrics/face-liveness-detection-sdk/desktop-and-server/linux/sample-application.md)
{% endcontent-ref %}

{% content-ref url="../id-documents/id-document-recognition-sdk/desktop-and-server/linux/sample-application.md" %}
[sample-application.md](../id-documents/id-document-recognition-sdk/desktop-and-server/linux/sample-application.md)
{% endcontent-ref %}

{% content-ref url="../id-documents/id-document-liveness-detection-sdk/desktop-and-server/linux/sample-application.md" %}
[sample-application.md](../id-documents/id-document-liveness-detection-sdk/desktop-and-server/linux/sample-application.md)
{% endcontent-ref %}

Each demo needs matching native assets and a valid license. Run `./install.sh` once, then start Streamlit with `./run_all.sh -s` and FastAPI separately with `./run_all.sh -f`.

## Android demos

| Project archive | Setup guide |
| --- | --- |
| `Truverion-Face-Android-SDK(Core).zip` | [Face Verify](../face-biometrics/face-recognition-sdk/mobile/android/installation.md) |
| `Truverion-Face-Android-SDK(Pro).zip` | [Face Verify & Analyze](../face-biometrics/face-recognition-sdk/mobile/android/installation.md) |
| `Truverion-ID-Recognition-Android.zip` | [ID Scan](../id-documents/id-document-recognition-sdk/mobile/android/installation.md) |

Request the project ZIP and matching license through your authorized package channel. The face ZIPs include their edition’s engine. Obtain the ID Scan engine separately and place it at `libidsdk/idsdk.aar`.
