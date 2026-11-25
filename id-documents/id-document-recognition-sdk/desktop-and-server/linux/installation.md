# Installation

## **Installation**

Install the ID Document Recognition SDK demo on Ubuntu 22.04 LTS

{% embed url="https://drive.google.com/file/d/1a649A0x754oN7SQ3qESYLJCkRbT4EmlA/view?usp=sharing" %}

### **Prepare the SDK files**

Extract the demo ZIP and copy the authorized engine/ and dependency/ folders into the demo directory.\
Preserve subfolders and symbolic  links.

<table><thead><tr><th width="341">Required path</th><th>Purpose</th></tr></thead><tbody><tr><td><strong><code>engine/header.py</code></strong></td><td>Python interface to the OCR engine</td></tr><tr><td><strong><code>engine/bin/</code></strong></td><td>SDK engine files</td></tr><tr><td><strong><code>dependency/libimutils.so_for_ubuntu22</code></strong></td><td>Ubuntu 22.04 runtime library</td></tr></tbody></table>

### **Install dependencies**

{% code overflow="wrap" %}
```
chmod +x *.sh
./install.sh
```
{% endcode %}

### **Check the Python environment**

{% code overflow="wrap" %}
```
.venv/bin/python -m pip check
```
{% endcode %}

{% hint style="info" %}
**Expected output:** No broken requirements found.
{% endhint %}

### **Troubleshooting**

<table><thead><tr><th width="231">Symptom</th><th>What to check</th></tr></thead><tbody><tr><td><strong>Missing SDK path</strong></td><td>Check engine/ and dependency/ beside install.sh</td></tr><tr><td><strong>Missing libttvcore.so</strong></td><td>Keep the matching library under dependency/ or engine/</td></tr><tr><td><strong>Missing libcrypto.so.1.1</strong></td><td>Use the matching SDK runtime dependency/</td></tr></tbody></table>

