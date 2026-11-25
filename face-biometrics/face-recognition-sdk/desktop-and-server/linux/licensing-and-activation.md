---
icon: key
---

# Licensing & Activation

## **Licensing & Activation**

Request a license and activate the Face Recognition SDK on your target Linux machine.

### **1. Request a license**

Run get\_device\_id() on the targe Linux host or inside its VM. Include the returned hardware ID, SDK version, and intended use in your request.

<a href="../../../../resources-and-support/contact-and-support.md" class="button primary">Contact Truverion for Licensing →</a>

### **2. Configure activation**

Use the activation method specified with your license.

{% columns %}
{% column width="50%" %}
#### **Online key**

Set the key in the terminal used to run the SDK

{% code overflow="wrap" %}
```
export FR_LICENSE-KEY="<license-key>"
```
{% endcode %}
{% endcolumn %}

{% column width="50%" %}
#### Offline license file

Place the license file in the demo directory

{% code overflow="wrap" %}
```
license.txt
```
{% endcode %}
{% endcolumn %}
{% endcolumns %}

{% code overflow="wrap" %}
```
Online: init_sdk("engine/bin", key)
Offline: init_sdk_offline("engine/bin", "license.txt")
```
{% endcode %}

### **3. Verify activation**

Run a standalone SDK smoke test. Check initialization  successeds, then extract one template from an approved sample image.<br>

### **Troubleshooting**

<table><thead><tr><th width="247">Symptom</th><th>What to check</th></tr></thead><tbody><tr><td>Key missing</td><td>Set it in the current shell</td></tr><tr><td>File missing</td><td>Check the path and read permissions</td></tr><tr><td>Hardware ID mismatch</td><td>Check the ID on the target host</td></tr></tbody></table>
