---
description: '#configuration, #security, #permission, #crossBU'
icon: shield-check
---

# Use case for the feature of Record ownership across Business Unit

Today, I would like to share an existing configuration on the Power Platform Admin Center. This feature is regarding record ownership impact on the permission of the user.

## Scenario

Firstly, let's see my scenarios as picture here

<figure><img src="../../.gitbook/assets/CleanShot 2024-08-29 at 09.03.13@2x.png" alt=""><figcaption><p>Scenario</p></figcaption></figure>

User A is working for 2 BU: **BU1** and **BU2.** However, as my scenario flows, this User was assigned different roles for each BU.

## How to enable & configure it?

Go to the Power Platform Admin Center > select environment > into the **Feature** area, turning on the feature **"Record ownership across Business Unit".**

<figure><img src="../../.gitbook/assets/CleanShot 2024-08-29 at 09.12.07@2x.png" alt=""><figcaption><p>Enable feature</p></figcaption></figure>

{% hint style="success" %}
Once enabled:

* Allows you to assign security roles from different business units to a user.
* Users can have different roles for each BU assigned.
{% endhint %}

## Assign Security Roles for the User

To assign security role for a User for different BUs, you go to the Power Platform Admin Center. After that, go to **User + permission** area >> click **User** >> then select specified User (ex: **TEST HS)** and click Manage security role, then select BU and assign roles for the user.

<figure><img src="../../.gitbook/assets/CleanShot 2024-08-29 at 09.26.10@2x.png" alt=""><figcaption><p>Assign roles for different BUs</p></figcaption></figure>

{% hint style="success" %}
Activating the _**Record ownership across BU**_ feature resulted in the **Business Unit** field being enabled, whereas it was previously disabled.
{% endhint %}

Please review the test security roles listed below. Following that, I will present the testing results for this feature. My test role: **Salesperson-X** and **Salesperson-Y**

<figure><img src="../../.gitbook/assets/CleanShot 2024-08-29 at 09.36.09@2x.png" alt=""><figcaption></figcaption></figure>

## Checking permission of the User

First, I logged in by user Admin and checked the data of Account entity as bellow.

* Total account records: 33
* Accounts of BU1: 04
* Accounts of BU2: 5

<figure><img src="../../.gitbook/assets/CleanShot 2024-08-29 at 10.07.02@2x.png" alt=""><figcaption><p>Data of Account entity - View by Admin role</p></figcaption></figure>

Now, my expectation when log-in by user **TEST HS:**

* Can see 9 Accounts of Child BU 1 & Child BU 2&#x20;
* Can Edit Account of Child BU 1&#x20;
* Cannot Edit Account of Child BU 2

... and then my testing Result

<figure><img src="../../.gitbook/assets/CleanShot 2024-08-29 at 10.17.05@2x.png" alt=""><figcaption><p>Total Accounts = 9 record</p></figcaption></figure>

Open the account record of each BU for permission testing&#x20;

<figure><img src="../../.gitbook/assets/Record_Cross_BU.gif" alt=""><figcaption><p>Testing Permission result - of TEST HS user</p></figcaption></figure>

## How to enable the field "Owning Business Unit" on the form for all entities?

I will now reveal a concealed setting that activates the Owning Business Unit field on the form for all entities. Once this field is enabled, users can create an Account record and then assign it to a different Business Unit to which they are assigned.

Before enabling this hidden setting - the field **Owning Business Unit** was set **Read-Only.** So, the user does not assign this record to a different BU.

<figure><img src="../../.gitbook/assets/CleanShot 2024-08-29 at 10.46.21@2x.png" alt="" width="563"><figcaption><p>Before - enable hidden feature</p></figcaption></figure>

After that, we will enable the hidden setting of the [**Environment Database Setting**](https://learn.microsoft.com/en-us/power-platform/admin/environment-database-settings)**.** You must install a solution -  **OrgDBSettings tool** at the [**link**](https://github.com/seanmcne/OrgDbOrgSettings/releases)**.**

After installation, navigate to the solution within the configuration area and set the '<mark style="color:green;">**RecomputeOwnershipAcrossBusinessUnits**</mark>' setting to <mark style="color:green;">**'true'.**</mark> This will enable the _**'Owning Business Unit**_' field to be modified and the user can assign account records to a different BU.

<figure><img src="../../.gitbook/assets/image (234).png" alt=""><figcaption><p>Set “RecomputeOwnershipAcrossBusinessUnits” = true</p></figcaption></figure>

Let checking.....

<figure><img src="../../.gitbook/assets/CleanShot 2024-08-29 at 11.00.59@2x.png" alt=""><figcaption><p>Testing - after enable hidden setting</p></figcaption></figure>

Tadaaaa... :tada: That's all today.

Hoping well and thank you!\
**\[NTD]yns.Asia**
