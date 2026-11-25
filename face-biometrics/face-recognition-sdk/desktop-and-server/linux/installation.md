# Installation

## **Installation**

Install the Face Recognition SDK demo on Ubuntu.

{% embed url="https://drive.google.com/file/d/1wYg0n7q7mqkXGTgZkhw9XR-dXGjTPRJ1/view?usp=sharing" %}

### Prepare the SDK files

Extract the demo archive and copy the authorized SDK files in the project.

{% hint style="info" %}
<mark style="color:$primary;">**engine/header.py                                        engine/bin/                                                dependency/openvino/**</mark>
{% endhint %}

<table><thead><tr><th width="192">Ubuntu</th><th>Compatibility library</th></tr></thead><tbody><tr><td>Ubuntu 22.04 LTS</td><td>libimutils.so_for_ubuntu22</td></tr></tbody></table>

### **Install dependencies**

```bash
chmod +x *.sh
./install.sh
```

### **Verify the SDK**

<mark style="color:$primary;">Run a standalone SDK smoke test from the command line. Initialize the SDK, extract a template from an approved single-face image, and confirm the template contains 512 float32 values.</mark>

