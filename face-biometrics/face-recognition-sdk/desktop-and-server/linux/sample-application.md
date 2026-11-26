---
icon: play
---

# Sample Application

Run the Linux demo to compare two face images and review the similarity score.

<a href="https://drive.google.com/file/d/1wYg0n7q7mqkXGTgZkhw9XR-dXGjTPRJ1/view?usp=sharing" class="button primary">Download the Linux Demo →</a>

### Before you begin

Complete [Installation](installation.md) and [Licensing & Activation](licensing-and-activation.md). Open a terminal in the demo directory.

{% code overflow="wrap" %}
```
chmod +x *.sh
./install.sh
```
{% endcode %}

### Run the Demo

{% tabs %}
{% tab title="Streamlit" icon="browser" %}
{% code overflow="wrap" %}
```
./run_all.sh -s
```
{% endcode %}

1. Open the Local URL shown in the terminal.
2. Select a reference image and a comparison image.
3. Run the comparison and review the similarity score and math result.

<figure><img src="../../../../.gitbook/assets/1_1.jpg" alt="Face Recognition Streamlit demo"><figcaption>Face Recognition Streamlit demo.</figcaption></figure>

<figure><img src="../../../../.gitbook/assets/1_2.jpg" alt="Face Recognition demo walkthrough screenshot 2"><figcaption>Face Recognition demo walkthrough screenshot 2.</figcaption></figure>
{% endtab %}

{% tab title="FastAPI" icon="bolt" %}
{% code overflow="wrap" %}
```
./run_all.sh -f
```
{% endcode %}

1. Copy the server URL shown in the terminal.
2. In Postman, open the face comparison and attach both image as from-data files.
3. Send the request and review the math result and similarity score

<figure><img src="../../../../.gitbook/assets/1_3.jpg" alt="Face Recognition demo walkthrough screenshot 3"><figcaption>Face Recognition demo walkthrough screenshot 3.</figcaption></figure>
{% endtab %}
{% endtabs %}

## <i class="fa-circle-check">:circle-check:</i> Check the result

Expect a similarity score and comparison outcome. Check each input for one usable face. For the request fields and error responses, see the [API reference](api-reference.md).
