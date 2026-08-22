---
description: '#ModelDrivenApp, #Help, #UserGuide'
cover: ../../.gitbook/assets/_user_manual_image.png
coverY: -41.120000000000005
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

# "Custom Help" - Is it help?

Hola.. :relaxed:

My friends!

Last month, my client announced the system run GO-LIVE. My client is using Power Platform to build their core system.&#x20;

The PM had asked me how we could create a document to guide or support the user use the system. The user will interact with the system to get support while still using the system seamlessly.

I found the **Custom Help** functionality on D365 and Power Platform and then tried using this.

## Enable "Help" functionality

We must enable Custom Help Pane and Guided Task in the System Admin setting as below.

<figure><img src="../../.gitbook/assets/image (152).png" alt=""><figcaption><p>Enable Custom Help Pane and Guided Task</p></figcaption></figure>

If the option is disabled, please make sure the option **Custom help for customizable entities** has been turned off. (_Path: Power Platform Admin Center > Feature > under Help features)._

<figure><img src="../../.gitbook/assets/image (156).png" alt="" width="375"><figcaption><p>Custom help for customizable entities: Turn Off</p></figcaption></figure>

{% hint style="info" %}
You can enable custom help panes or customizable help, but not both at the same time.
{% endhint %}

After enabling, click on the "help" icon <img src="../../.gitbook/assets/image (153).png" alt="" data-size="line">>> The **Custom Help** pane will be opened.

<figure><img src="../../.gitbook/assets/image (157).png" alt=""><figcaption><p>Open Custom Help pane</p></figcaption></figure>

## Creating "Custom Help" form App

Now, we can create a new custom help to guide the user using Lead Processing.

On the Application, you open the **Entity** and click on the "help" icon<img src="../../.gitbook/assets/image (153).png" alt="" data-size="line">. The Custom Help pane will be shown that's mean, you are creating Custom Help for this entity. \
As my sample, I will create Custom Help to entity **Lead.**

{% hint style="info" %}
The Custom Help is available for **View** and **Form.** If you want to show Custom help on view, you should open the main list view of a specific entity and then click icon<img src="../../.gitbook/assets/image (153).png" alt="" data-size="line"> to begin creating content.
{% endhint %}

After that, on the Custom Help Pane >> click on the icon <...> and then click **Edit**

<figure><img src="../../.gitbook/assets/image (158).png" alt="" width="563"><figcaption><p>Edit Custom Help</p></figcaption></figure>

On Custom Help, you can input the content by yourself with many components and functionalities:

* Free form text
* Add a bulleted list and a numbered list
* Can insert Link, Image, Video
* Add a section to group the content

After clicking **Edit  >** the new pane will be opened. Then, you can input the content on that >> And click **Save** after finishing.

<figure><img src="../../.gitbook/assets/image (159).png" alt=""><figcaption><p>Creating Custom Help on Lead entity</p></figcaption></figure>

## Security & Privilege

The Custom Help is an entity in Dataverse, that why you can set _**global permission (4/4 or Organization)**_ for the user: create, read, write, delete, append and append to privileges on the **Help Page** entity.

<figure><img src="../../.gitbook/assets/image (64).png" alt="" width="563"><figcaption><p>Security role for Help Page entity</p></figcaption></figure>

## How to deploy to another?

After creating the necessary Custom Help on the DEV environment, you just add these custom help records to your solution and prepare to deploy for another environment.

<figure><img src="../../.gitbook/assets/image (63).png" alt="" width="563"><figcaption><p>Help page component in solution</p></figcaption></figure>

After adding to the solution, you can click open the Help page record and edit as below.

<figure><img src="../../.gitbook/assets/image (65).png" alt=""><figcaption><p>Help page record</p></figcaption></figure>

## Check the result...

Now, I will log in with a different user will open the Lead form then use the custom help.

<figure><img src="../../.gitbook/assets/_help_checking.gif" alt=""><figcaption><p>Using Custom Help on Lead form</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (61).png" alt=""><figcaption><p>Help 1</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (62).png" alt=""><figcaption><p>Help 2</p></figcaption></figure>

Hoping well...  :tada:

For more details from Microsoft as the [link](https://learn.microsoft.com/en-us/power-apps/maker/data-platform/create-custom-help-pages).

Thank you.\
**\[NTD]yns.asia**\
<mark style="color:red;">...</mark>[<mark style="color:red;">invite me a cup.</mark>](https://ko-fi.com/ntdyns/?ref=qr\&amp;v=2) :coffee: Thank you. :heart:
