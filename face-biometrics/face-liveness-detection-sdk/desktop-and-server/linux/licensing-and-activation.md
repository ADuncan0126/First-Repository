# Licensing & Activation

## Licensing & Activation

Activate the Linux SDK after completeting Installation.

### **1. Request a license**

If required, retrieve the hardware ID on the target Linux machine.

Include the SDK version and intended use in your request.

<a href="../../../../resources-and-support/contact-and-support.md" class="button primary">Contact Truverion for Licensing →</a>

### **2. Configure activation**

{% columns %}
{% column width="50%" %}
#### **Online key**

Set the key in the terminal used to run the SDK

{% code overflow="wrap" %}
```
export FL_LICENSE-KEY="<license-key>"
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

If the online key is unsuccessful, the SDK tries the offline file when present.

### **3. Verify activation**

Run the SDK initializer directly from the demo directory.

#### <mark style="color:$primary;">**`SDK activation successful`**</mark>

This check run without launching Streamlit or FastAPI.

### **Troubleshooting**

<table><thead><tr><th width="247">Symptom</th><th>What to check</th></tr></thead><tbody><tr><td>Import fails</td><td>SDK files and runtime libraries</td></tr><tr><td>Online activation fails</td><td><code>FL_LICENSE_KEY</code> in the current terminal</td></tr><tr><td>Offline activation fails</td><td><code>license.txt</code> location and read permissions</td></tr></tbody></table>

