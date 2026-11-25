---
icon: box
---

# Installation

Set up the Linux demo and install its dependencies.

### 1. Prepare the demo

{% embed url="https://drive.google.com/file/d/1h3wTWf0ujf6sJPvcQDIQ97qbwW0CIAlJ/view?usp=sharing" %}

Extract the demo ZIP and open the extracted folder in a terminal. Add the native SDK files to the paths below.

<table><thead><tr><th width="307">Path</th><th>Contents</th></tr></thead><tbody><tr><td>engine/header.py</td><td>SDK Python entry point</td></tr><tr><td>engine/model/</td><td>SDK model files</td></tr><tr><td>dependency/</td><td>Native SDK libraries</td></tr></tbody></table>

{% hint style="info" %}
The demo archive requires the native SDK files supplied separately.
{% endhint %}

### **2. Install dependencies**

{% code overflow="wrap" %}
```
chmod +x *.sh
./install.sh
```
{% endcode %}

The installer uses sudo to install Ubuntu packages and copy native libraries into /usr/lib.\
It also installs the Python dependencies from requirments.txt.



### **3. Verify Python dependencies**

Run from the demo directory with the virtualenvironment active.

{% code overflow="wrap" %}
```
python3 -c "import cv2, streamlit, fastapi; import engine.header; print('Imports OK')"
```
{% endcode %}

{% hint style="info" %}
**Expected output:** Imports OK
{% endhint %}
