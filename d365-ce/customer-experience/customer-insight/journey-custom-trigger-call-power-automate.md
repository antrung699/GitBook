---
description: '#journey, #powerauotmate, #customtrigger'
---

# Journey - Custom Trigger - Call Power Automate

Ciao Friends,&#x20;

Back again after being excited by Customer Insight and especially, **Journey** functionality.

In a recent proof-of-concept (PoC) session for my client, I showcased the D365 Customer Insight Journey. During this session, I demonstrated a scenario **where a lead is created when an anonymous user submits a form on the client's Loan Program webpage.**

My journey is below, in that I used the OOB action "**Created a Lead"** and noticed that the system just supported _<mark style="color:green;">02 OOB actions: "Create a Lead" and "Create an Opportunity".</mark>_

<figure><img src="../../../.gitbook/assets/CleanShot 2024-12-15 at 11.11.02@2x.png" alt=""><figcaption><p>Journey - Trigger Contact us from submitted - Create Lead action</p></figcaption></figure>

02 OOB Actions in the Journey.

<figure><img src="../../../.gitbook/assets/CleanShot 2024-12-15 at 11.18.19@2x.png" alt=""><figcaption><p>2 OOB Actions - Create Lead &#x26; Create Opportunity</p></figcaption></figure>

I wonderin&#x67;**,&#x20;**<mark style="color:red;">**How I can create a record for any custom entity based on this trigger...**</mark> :thinking:

## :rocket: :bulb:Process my question

**Scenario**: <mark style="color:green;">When an anonymous user submits the "Contact Us" form on the website, a Loan Request record should be created instead of a Lead record, as outlined in the above journey.</mark>

### 1. Using Components

To demonstrate this scenario, I used **Custom Trigger** and **Power Automate.**

{% code overflow="wrap" %}
```markup
Steps:
1. Create a Custom Trigger in the D365 Customer Insight - Journey
2. Create a Power Automate was triggered by the Custom Trigger to run the action.
3. Create & configure a Journey: Use the Custom Trigger to trigger the Power Automate
```
{% endcode %}

### 1.1 Create   Custom Trigger in the D365 Customer Insight - Journey

My custom trigger

<figure><img src="../../../.gitbook/assets/CleanShot 2024-12-15 at 20.02.04@2x.png" alt="" width="563"><figcaption><p> Custom Trigger - "New Contact Us Submitted"</p></figcaption></figure>

{% hint style="info" %}
For more details about Custom Trigger in D365 Customer Insight -Journey, you can refer to this link: [Create custom triggers in Customer Insights - Journeys](https://learn.microsoft.com/en-us/dynamics365/customer-insights/journeys/real-time-marketing-custom-triggers)
{% endhint %}

I also created a new page for the Loan Program and Contact Us form on this page as below.

<figure><img src="../../../.gitbook/assets/CleanShot 2024-12-15 at 20.08.26@2x.png" alt=""><figcaption><p>Landing Page for quick demo</p></figcaption></figure>

### 1.2 Create Power Automate

Use Custom Action **"When an action is performed"**, and then fill in the required fields as follows:

* Set **Catalog** to "**Cxp**"
* Set **Category** to "**Custom**"
* Set **Table name** to "**(none)**"
* Set the **Action name** to the name of the custom trigger you activated in your customer journey.\
  In my scenario, **Action Name = "**_**New Contact Us Submitted"**_

<figure><img src="../../../.gitbook/assets/CleanShot 2024-12-15 at 19.55.15@2x.png" alt=""><figcaption><p>1-Add step "When an action is performed"</p></figcaption></figure>

{% hint style="info" %}
You can find the details at this link: [Trigger Power Automate flows from journeys](https://learn.microsoft.com/en-us/dynamics365/customer-insights/journeys/real-time-marketing-custom-actions#trigger-power-automate-flows-from-journeys)
{% endhint %}



### 1.3 Create and Configure Journey: Using the "Activate a Custom Trigger" step

<figure><img src="../../../.gitbook/assets/CleanShot 2024-12-16 at 11.49.21@2x.png" alt=""><figcaption><p>Create Journey and using "Activate a Custom Trigger" step</p></figcaption></figure>

For my scenarios, I create a Journey for Loyalty Member: These members will receive a pre-approved loan email.

* If the client opens an email and clicks on the email's link, the system will create a Task activity and assign it to the Member owner.
* If the client opens the landing page and submits the "Contact Us" form (**use: Activate a Custom Trigger)** - the system will be triggered and run the Power Automate (in the above picture) to create a **Loan record**&#x20;

### :rocket: Checking now...

Checking my testing videos

{% embed url="https://youtu.be/KRu4ALAIFj0" %}

Thank you & regards,\
**\[NTD]yns.asia**
