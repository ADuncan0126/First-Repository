---
icon: play
---

# Sample Application

## ID Document Liveness sample application

Run the Linux demo to check an ID document image and review the liveness result.

<a href="https://drive.google.com/file/d/1h3wTWf0ujf6sJPvcQDIQ97qbwW0CIAlJ/view?usp=sharing" class="button primary">Download the Linux Demo →</a>

### Before you begin

Complete <mark style="color:$primary;">installation</mark> and <mark style="color:$primary;">Licensing & Activation</mark>. Open a terminal in the demo direcotory.

### Run the demo

{% tabs %}
{% tab title="Streamlit" icon="browser" %}
{% code overflow="wrap" %}
```
./run_all.sh -s
```
{% endcode %}

1. Open the Local URL shown in the terminal.
2. Upload a sample ID document image.
3. Run the check and review the liveness result.

<figure><img src="../../../../.gitbook/assets/4_1.jpg" alt="ID Document Liveness Detection Streamlit demo"><figcaption>ID Document Liveness Detection Streamlit demo.</figcaption></figure>

<figure><img src="../../../../.gitbook/assets/4_2.jpg" alt="ID Document Liveness Detection demo walkthrough screenshot 2"><figcaption>ID Document Liveness Detection demo walkthrough screenshot 2.</figcaption></figure>
{% endtab %}

{% tab title="FastAPI" icon="bolt" %}
{% code overflow="wrap" %}
```
./run_all.sh -f
```
{% endcode %}

1. Copy the Server URL shown in the terminal.
2. In Postman, send `POST /process_image` with the image of ID in `image`.
3. Review the result.

<figure><img src="../../../../.gitbook/assets/4_3.jpg" alt="ID Document Liveness Detection demo walkthrough screenshot 3"><figcaption>ID Document Liveness Detection demo walkthrough screenshot 3.</figcaption></figure>
{% endtab %}
{% endtabs %}

## <i class="fa-circle-check">:circle-check:</i> Check the result

Expect a document liveness assessment when the image can be processed. Use a sharp image with the entire document visible. For the request fields and error responses, see the [API reference](api-reference.md).
