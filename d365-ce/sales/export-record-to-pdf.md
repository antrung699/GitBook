---
description: '#D365CE, #Sales, #PDF, #WordTemplate'
cover: ../../.gitbook/assets/image (29).png
coverY: 0
layout:
  width: default
  cover:
    visible: true
    size: hero
    mask: none
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
---

# Export record to PDF

Today, I came back to the old functionality - <mark style="color:purple;">**Export to PDF**</mark>.

Previously, this feature only supported out-of-the-box entities like **Account**, **Contact**, **Lead**, **Opportunity**, **Quote**, **Order**, and **Invoice** but did not extend to <mark style="color:green;">**Custom entities**</mark><mark style="color:purple;">**.**</mark>

It's gratifying to see that this functionality has <mark style="color:green;">**now**</mark> been <mark style="color:green;">**implemented**</mark> for the <mark style="color:green;">**Custom Entity**</mark>**.**

<figure><img src="../../.gitbook/assets/image (28).png" alt=""><figcaption><p>Configure "Export to PDF" for entities</p></figcaption></figure>

{% hint style="success" %}
The **Export to PDF** functionality is available on D365 for Sales.

For configuration, Open the **Sales Hub >** move to **App Setting** area > **Productivity tools.** Then choose the **"Conver to PDF"** and configure these entities to apply this functionality.
{% endhint %}

## Scenario: Create a Device Card

My case: I must create a Device Card to show Device information. The user will export it to PDF and send it to the customer.

I have a custom entity called **Device** that stores the device information of customers.

**Involve Steps**

<figure><img src="../../.gitbook/assets/image (29).png" alt=""><figcaption><p>Configure Export to PDF</p></figcaption></figure>

### 1. Configure Word Template - "Device Card"

My sample Word Template "Device Card" is below.

<figure><img src="../../.gitbook/assets/image (31).png" alt=""><figcaption><p>Sample "Device Card" - Thank you</p></figcaption></figure>

### 2. Enable "Export to PDF" for entity Device

Configure in **Sales Hub > App Setting >** under **Productivity Tools**, click menu **"Convert to PDF"** then **select entity Device** > click **Save** to enable.

<figure><img src="../../.gitbook/assets/image (28).png" alt=""><figcaption><p>Enable function for entity "Device"</p></figcaption></figure>

### **3. Check the "Export to PDF" button on the Device entity:**

<figure><img src="../../.gitbook/assets/image (30).png" alt=""><figcaption><p>Button "Export to PDF" is visible</p></figcaption></figure>

Ya.. here, I completed enabling the functionality "Export to PDF" for the custom entity "Device". :tada:

<figure><img src="../../.gitbook/assets/image (32).png" alt=""><figcaption><p>Screenshot - Export to PDF</p></figcaption></figure>

<mark style="background-color:green;">**Live Testing on Sales Hub:**</mark>

<figure><img src="../../.gitbook/assets/_Test_Export_PDF_Device.gif" alt=""><figcaption><p>Live check - Export to PDF</p></figcaption></figure>

## Send email "Device Card.pdf" to customer

In "Export to PDF" screen > click on **\[Email]** icon to send this Device Card.pdf file to the customer via email.

* The Email record will be created
* This Email will be shown on the Timeline are of the customer.

<figure><img src="../../.gitbook/assets/Send_email_device_card.gif" alt=""><figcaption><p>Send email on "Export to PDF"</p></figcaption></figure>

Check **Email** record on Timeline area of **Contact - John John**

<figure><img src="../../.gitbook/assets/image (214).png" alt=""><figcaption><p>Email Record on Contact</p></figcaption></figure>

Hoping well. :heart\_hands:

Thank you for your reading.\
**\[NTD]yns.Asia**\
<mark style="color:red;">...</mark>[<mark style="color:red;">invite me a cup.</mark>](https://ko-fi.com/ntdyns/?ref=qr\&amp;v=2) :coffee: Thank you. :heart:
