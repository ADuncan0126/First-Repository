---
icon: box
---

# Installation

## **Installation**

Install the Face Liveness Detection SDK demo on Ubuntu 22.04 LTS.g

{% embed url="https://drive.google.com/file/d/1jQHhBssZCnzbcEeBczk03OjLRJOzrhcB/view?usp=sharing" %}

### **Prepare the SDK files**

Extract the demo archive. Copy the SDK's engine/ and dependency/ folders into the demo directory.

<table><thead><tr><th width="318">Path</th><th>Purpsoe</th></tr></thead><tbody><tr><td>engine/header.py</td><td>Python interface</td></tr><tr><td>engine/bin/</td><td>SDK engine files</td></tr><tr><td>dependency/libmutils.so_for_ubuntu22</td><td>Ubuntu 22.04 runtime library</td></tr><tr><td>dependency/openvino/</td><td>Runtime libraries, when included</td></tr></tbody></table>

### **Install dependencies**

{% code overflow="wrap" %}
```
chmod +x *.sh
./install.sh
```
{% endcode %}

The installer creates .venv and installs the demo dependencies.<br>

### **Verify Python dependencies**

{% code overflow="wrap" %}
```
.venv/bin/python -m pip check
```
{% endcode %}

{% hint style="info" %}
**Expected output:** No broken requirments found.
{% endhint %}
