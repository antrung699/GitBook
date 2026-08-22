---
description: '#SecurityRole, #ModelDrivenApp, #MDA, #MinimumPrevilege, #PowerPlatform'
cover: >-
  https://images.unsplash.com/photo-1630783204556-649cc187d778?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHNlYXJjaHwyfHxwZXJtaXNzaW9ufGVufDB8fHx8MTcxMDc3MjI1NHww&ixlib=rb-4.0.3&q=85
coverY: -131
layout:
  width: default
  cover:
    visible: true
    size: full
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

# 💡 Tip: Create a Security Role with "App Opener" minimum privileges

Hello, my friends,

I recently conducted a training session on the **"Security Role model"** within Dataverse. During the session, I utilized the modern interface of the Power Platform Admin Center to create a new Security Role. I discovered a new option _<mark style="color:green;">**"**</mark>_:ballot\_box\_with\_check: _<mark style="color:green;">**Include App Opener privileges for running Model-Driven apps".**</mark>_

<figure><img src="../../.gitbook/assets/image (2).png" alt="" width="563"><figcaption><p>New Option: Include App Opener privileges for running Model-Driven apps</p></figcaption></figure>

Once created, the Security Role will be automatically configured with all the essential permissions to operate Model-driven applications efficiently.

{% hint style="info" %}
For further: [Minimum privileges for common tasks](https://learn.microsoft.com/en-us/power-platform/admin/create-edit-security-role#minimum-privileges-for-common-tasks) in Model-Driven App.
{% endhint %}

Previously, I preferred the legacy interface for creating a new Security Role or customizing the application. This preference led me to switch to the legacy interface to check... and **HAVE NO** this option.

<figure><img src="../../.gitbook/assets/image (3).png" alt="" width="563"><figcaption><p>The Legacy Interface - Create a Security Role</p></figcaption></figure>

Okay... for now, checking my new Security Role with the option: _**Include App Opener privileges for running Model-Driven apps.**_ \
-> By selecting this option, this security role has been granted a wide range of permissions. This ensures the user will have seamless access to the Model-driven application with their new security role as below.

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption><p>The new Security Role - Included "App Opener" privileges</p></figcaption></figure>

Without this option, once created, the new Security Role is almost empty permission configuration as below.

<figure><img src="../../.gitbook/assets/CleanShot 2024-03-18 at 21.01.18@2x.png" alt=""><figcaption><p>The new Security Role - Excluded "App Opener" privileges</p></figcaption></figure>

Thank you for reading and hoping well. :tada:\
**\[NTD]yns.Asia**\
<mark style="color:red;">...</mark>[<mark style="color:red;">invite me a cup.</mark>](https://ko-fi.com/ntdyns/?ref=qr\&amp;v=2) :coffee: Thank you. :heart:
