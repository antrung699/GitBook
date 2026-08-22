---
description: '#Activity, #Timeline, #MultipleRecords'
---

# Activities with multiple related records

Hello friends,

Today i wold like to share the new feature of the Release Wave 2 - this is [**Associate activities with multiple related record**](https://learn.microsoft.com/en-us/power-platform/release-plan/2023wave2/data-platform/associate-activities-multiple-related-records). Hopefully can be help... :smile:&#x20;

As before, an Activity just only regarding to 1 related record and my client who always asked me how we can show this activity record in multiple timeline.

The example: \
&#x20;  We have the **Opportunity 1** and this **Opps** record is belong to **Contact A1** and **Account A.** Now, when the Sales man who did interaction on **Opps 1** by create activity record (Task, Appointment, Email). \
&#x20;  Then the Sales man want to see the all **Opps 1's activities** on Timeline of **Contact A1** and **Account A.**

So now, how we can configure that?&#x20;

## My previous solution

I create 1 custom entity called **"History"** to store the interaction histories for Contact/ Account in case by case.

As the above example, I had created some **Workflow** which was applied on **Task, Appointment, Email created from Opportunity.**\
This Workflow will create record **History** for **Activity. Contact** and **Activity. Account** when activities record created (of course: Regarding. Opportunity <> null).

After that, on the Timeline of Contact/ Account will be displayed these **History records** instead of Activities record.

**Okay, so now, with the new feature, how we can do ???**

## ... With new feature

Actually, Microsoft has updated for your environment and you just open Form then configure. :smile:

I back to my solution and open **Main form of Contact**&#x20;

<figure><img src="../../.gitbook/assets/image (69).png" alt=""><figcaption><p>Contact's Main Form</p></figcaption></figure>

Now, you select the **Timeline** area >> in the right panel, scroll down and find **Related records** as above.

<figure><img src="../../.gitbook/assets/image (70).png" alt="" width="563"><figcaption><p>Enable Activity rollup of related record</p></figcaption></figure>

After that, choose the Related record. As my sample, so I will click to select **Opportunity >>** click **Enable** to show Opportunity's activity records into **Contact timeline**

{% hint style="info" %}
Currently, the Entity (OOB) that applied this functionality is based on the application that you installed. I also checked but cannot enable it for another custom entity.&#x20;

* D365 CE: Account, Contact, Case, Order, Quote, Opportunity, Lead
* Power Platform: Account, Contact
{% endhint %}

## Checking now...

On Opportunity, I created 1 Task and 1 Appointment record as bellow:

<figure><img src="../../.gitbook/assets/image (71).png" alt=""><figcaption><p>Opportunity and activity records</p></figcaption></figure>

Now, I will open the Customer (Contact) record and all Opportunity's activity will be shown on Contact Timeline as my expectation.

<figure><img src="../../.gitbook/assets/image (72).png" alt=""><figcaption><p>Contact with opportunity's activity record</p></figcaption></figure>

Hopefully, we can enable and configure for any custom entity that we want in the near future. Please Microsoft... !!! I'm still waiting ... :tada:\
\
**\[NTD]yns.asia**
