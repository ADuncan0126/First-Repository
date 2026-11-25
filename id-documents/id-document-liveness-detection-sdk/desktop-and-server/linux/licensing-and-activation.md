---
icon: key
---

# Licensing & Activation

Include the SDK version and intended use in your request.

<a href="../../../../resources-and-support/contact-and-support.md" class="button primary">Contact Truverion for licensing →</a>

### **Configure activation**

#### **Offline license file**

Copy the issued license.txt into the demo directory.

#### Online key (optional)

Set the key in the same terminal you use to run the demo.

{% code overflow="wrap" %}
```
export LICENSE_KEY="<license-key>"
```
{% endcode %}

{% hint style="info" %}
When both are configured, the demo tries LICENSE\_KEY first.
{% endhint %}

### **Troubleshooting**

<table><thead><tr><th width="237">Symptom</th><th>What to check</th></tr></thead><tbody><tr><td><strong>Licensing missing</strong></td><td>Check that <code>license.txt</code> is next to <code>run_all.sh</code>.</td></tr><tr><td><strong>Activation failed</strong></td><td>Verify the issued license and native dependencies.</td></tr><tr><td><strong>Initilization failed</strong></td><td>Check the model files in <code>engine/model/</code>.</td></tr></tbody></table>
