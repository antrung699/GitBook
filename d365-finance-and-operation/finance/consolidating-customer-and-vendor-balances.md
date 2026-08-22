---
description: '#NettingCustomerVendor, #D365Finance, #D365FO'
---

# Consolidating Customer & Vendor Balances

Checking the new functionality of D365 Finance (D365FO) -[ **Net Customer and Vendor Balances.**](https://learn.microsoft.com/en-us/dynamics365/finance/cash-bank-management/net-customer-and-vendor-balances)

{% hint style="info" %}
Currently, this feature is a preview feature in **D365 Finance** **version&#x20;**_**10.0.38**_ and is available only in the _**Sandbox**_ environment (as of today 06-Jan-2024).
{% endhint %}

Please make sure the feature has been enabled

<figure><img src="../../.gitbook/assets/image (187).png" alt=""><figcaption><p>Enable the netting feature</p></figcaption></figure>

&#x20;  When your organization engages with a company that serves **both** as a **Customer** and a **Vendor**, there's a remarkable opportunity to streamline financial transactions and optimize savings. By **consolidating** the **balances** between **your organization** and **the company**, you can eliminate unnecessary payments or receipts, effectively minimizing transaction fees. \
&#x20;  This approach creates a win-win scenario, enhancing financial management efficiency while reducing costs significantly.

The **Net Customer and Vendor Balance** functionality serves as the solution to achieve this objective seamlessly.

## Configure: Journal name & Bridging account

The bridging account is for netting purposes.

_**Path: GL > Journal Setup > Journal Name**_

<figure><img src="../../.gitbook/assets/image (189).png" alt=""><figcaption><p>Journal Name</p></figcaption></figure>

## Configure: Netting agreement

The purpose of the Netting Agreement is to enable the management of paired customer and vendor accounts for netting within a specified and effective timeframe.

_**Path: Account Payable > Payments > Netting > Netting agreement**_

<figure><img src="../../.gitbook/assets/image (188).png" alt=""><figcaption><p>Netting Agreement</p></figcaption></figure>

* Journal name (1): select the Customer and Vendor netting journal name.
* Account (2): select a bridging account that is used for netting balance purposes.
* Parties (3): configure the mapping Customer Account and Vendor Account within the effective timeframe. This configuration will be used in the Netting functionality.

## Doing...

In our organization, have a company named **NTD Asia Group** that serves as **both** a **Customer** and a **Vendor** within our systems.

The current Customer Balance and Vendor Balance:

* Customer:  **100003350** - NTD Asia Group - Balance:  **110,000,000 VND.**
* Vendor     :  **202439**        - NTD Asia Group - Balance:  **30,000,000 VND.**

<figure><img src="../../.gitbook/assets/image (186).png" alt=""><figcaption><p>Customer and Vendor Balance: NTD Asia Group</p></figcaption></figure>

I will run the **Customer and vendor balance netting** to net off the balances between our customers and vendors.

_**Path: Account Payable > Payments > Netting >** Then click the menu **Customer and vendor balance netting** ==>_ This functionality will be run automatically.&#x20;

<figure><img src="../../.gitbook/assets/image (190).png" alt="" width="375"><figcaption><p>Run Customer and vendor balance netting</p></figcaption></figure>

The system will automatically calculate the minimal amount between the Customer invoice balance and the Vendor invoice balance as the netting amount.&#x20;

<figure><img src="../../.gitbook/assets/image (191).png" alt=""><figcaption><p>Minial Customer Balance and Vendor Balance</p></figcaption></figure>

{% hint style="info" %}
The subgrid will show all the pairs of customer accounts and vendor accounts that are available for netting.
{% endhint %}

After that, we need to select a paired record, and then select **Create Netting**.

<figure><img src="../../.gitbook/assets/image (192).png" alt=""><figcaption><p>Create Netting</p></figcaption></figure>

In the Netting journal, we need to **Mark Select** the Open Customer Invoice and Open Vendor Invoice first. Then, we must input the **Netting Date** and click **Post** as the final step.

<figure><img src="../../.gitbook/assets/image (193).png" alt=""><figcaption><p>Create Netting</p></figcaption></figure>

Check the posted netting

<figure><img src="../../.gitbook/assets/image (194).png" alt=""><figcaption><p>Posted Netting History</p></figcaption></figure>

Finally, we will check the Customer and Vendor balance after netting.

The balances after netting:

* Customer:  **100003350** - NTD Asia Group - Balance: **80,000,000 VND**
* Vendor     :  **202439**        - NTD Asia Group - Balance:  **0 VND**

<figure><img src="../../.gitbook/assets/image (195).png" alt=""><figcaption><p>The Balance after netting</p></figcaption></figure>

For more details at the [link.](https://learn.microsoft.com/en-us/dynamics365/finance/cash-bank-management/net-customer-and-vendor-balances)

Thank you & Hopping well.\
**\[NTD]yns.asia**\
<mark style="color:red;">...</mark>[<mark style="color:red;">invite me a cup.</mark>](https://ko-fi.com/ntdyns/?ref=qr\&amp;v=2) :coffee: Thank you. :heart:
