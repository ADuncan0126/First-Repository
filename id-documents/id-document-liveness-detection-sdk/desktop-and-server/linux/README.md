---
icon: terminal
---

# Linux

## ID Document Liveness Detection SDK for Linux

Analyze one identify document image for signs of a presentation attack.

### **SDK capabilities**

<table><thead><tr><th width="215">Capability</th><th>Description</th></tr></thead><tbody><tr><td><strong>Image input</strong></td><td>One identity document image per check.</td></tr><tr><td><strong>Liveness assessment</strong></td><td>Checks for signs of screen replay, portrait replacement, and printed copies.</td></tr><tr><td><strong>Browser demo</strong></td><td>Upload or capture an image in Streamlit</td></tr><tr><td><strong>API demo</strong></td><td>Submit a file upload or Base64 JSON through FastAPI</td></tr></tbody></table>

### Presentation attack examples

<table><thead><tr><th width="271">Attack type</th><th>Examples</th></tr></thead><tbody><tr><td><strong>Screen replay</strong></td><td>A document image displayed on a phone, tablet, or monitor.</td></tr><tr><td><strong>Printed copy</strong></td><td>A paper reproduction presented as the original document</td></tr><tr><td><strong>Portrait replacement</strong></td><td>An identity document with an overlaid or subsituted portrait.</td></tr></tbody></table>

### Reference performance

{% hint style="info" %}
**Native SDK processing**\
The Streamlit demo reports processing time separately from model initialization.
{% endhint %}

### Recommended system configuration

<table><thead><tr><th width="280">Component</th><th>Configuration</th></tr></thead><tbody><tr><td>Operating system</td><td>Ubuntu 22.04 LTS</td></tr><tr><td>CPU</td><td>8 cores</td></tr><tr><td>Memory</td><td>8 GB RAM</td></tr><tr><td>Storage</td><td>8 GB</td></tr></tbody></table>
