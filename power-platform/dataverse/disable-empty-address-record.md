---
description: '#CustomerAddres, #Address, #Dataverse, #PowerPlatform, #D365CE'
---

# Disable Empty Address record

Hi guys,

Nowadays, I did a walkthrough in the Power Platform Admin Center and saw the new feature setting for **Customer Address (Address)**.&#x20;

The feature setting: _**Disable Empty Address Record Creation.**_ This setting prevents the system from creating empty Address records. If the create payload does not contain any address information, the system will ignore it.

{% hint style="info" %}
**NOTE:** Just only takes effect on 3 entities: Account, Contact, Lead, and will NOT affect any other entities address table behavior.
{% endhint %}

<figure><img src="../../.gitbook/assets/image (206).png" alt=""><figcaption><p>Disable empty address record creation</p></figcaption></figure>

## Lookback: the previous functionality

The previous time, if have no this setting...

Behind the scenes, when you create an **Account/Contact/Lead** record and input or do not input any value into the OOB address fields (includes:  Address 1, Address2, Address3), the system will create 3 corresponding Empty Address records automatically and store them in the table **Address (customeraddress).**&#x20;

<figure><img src="../../.gitbook/assets/_before_enable_AddressSetting.gif" alt=""><figcaption><p>Before enable setting: 3 address records created</p></figcaption></figure>

## Enable setting: "Disable empty address record creation"

After enabling the setting...

<figure><img src="../../.gitbook/assets/image (207).png" alt=""><figcaption><p>Enable setting</p></figcaption></figure>

Now checking... -> Have no empty address records created. :tada:

<figure><img src="../../.gitbook/assets/_after_enable_AddressSetting.gif" alt=""><figcaption><p>After enable setting: Have no empty record created</p></figcaption></figure>

Thank you and hoping well... :innocent:\
**\[NTD]yns.asia**\
<mark style="color:red;">...</mark>[<mark style="color:red;">invite me a cup.</mark>](https://ko-fi.com/ntdyns/?ref=qr\&amp;v=2) :coffee: Thank you. :heart:
