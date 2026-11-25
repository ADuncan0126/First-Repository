---
icon: key
---

# Licensing & Activation

Activate the ID Document Recognition SDK after completing Installation.

### **Request a license**

Include your SDK version and intended use in your request.

<a href="../../../../resources-and-support/contact-and-support.md" class="button primary">Contact Truverion for licensing →</a>

### **Configure activation**

{% columns %}
{% column %}
**Online key**

Set the key in the terminal used to run the SDK

{% code overflow="wrap" %}
```
export FR_LICENSE-KEY="<license-key>"
```
{% endcode %}
{% endcolumn %}

{% column %}
**Offline license file**

Place the license file in the demo directory

{% code overflow="wrap" %}
```
license.txt
```
{% endcode %}
{% endcolumn %}
{% endcolumns %}

{% hint style="info" %}
The demo tries the online key first when both credential are configured.
{% endhint %}

### Verify activation

In Streamlit, look for `Recognition Engine Active`

In FastAPI, send a sample recognition request, then check `GET /health` for `ready: true` and `state: "active".`



### **Troubleshooting**

<table><thead><tr><th width="271">Symptom</th><th>What to check</th></tr></thead><tbody><tr><td><strong>No license configured</strong></td><td>Check <code>LICENSE_KEY</code> or <code>license.txt</code>.</td></tr><tr><td><strong>License activation failed</strong></td><td>Verify the license and record the SDK error code.</td></tr><tr><td><strong>SDK initialization failed</strong></td><td>Check <code>engine/bin/</code> and the native libraries.</td></tr></tbody></table>
