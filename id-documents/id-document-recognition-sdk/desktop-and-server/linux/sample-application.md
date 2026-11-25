---
icon: play
---

# Sample Application

## **ID Document Recognition sample application**

Run the ID Document Recognition demo on Ubuntu 22.04 LTS.

To obtain the demo package, [contact Truverion](../../../../resources-and-support/contact-and-support.md).

### Before you begin

Complete [Installation](installation.md) and [Licensing & Activation](licensing-and-activation.md). Open a terminal in the demo directory.

{% code overflow="wrap" %}
```
chmod +x *.sh
./install.sh
```
{% endcode %}

### Run the demo

{% tabs %}
{% tab title="Streamlit" icon="browser" %}
{% code overflow="wrap" %}
```
./run_all.sh -s
```
{% endcode %}

1. Open the Local URL shown in the terminal
2. Upload or Capture the front image. Add the back image if needed
3. Run recognition and review the extracted fields.

<figure><img src="../../../../.gitbook/assets/3_1.jpg" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/3_2.jpg" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="FastAPI" icon="bolt" %}
{% code overflow="wrap" %}
```
./run_all.sh -f
```
{% endcode %}

1. Copy the Server URL shown in the terminal.
2. In Poastman, send `Post /api/read_idcard` with the front image in `image` and the optional back image in `image2`.
3. Review the extracted document fields.

<figure><img src="../../../../.gitbook/assets/3_3.jpg" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

