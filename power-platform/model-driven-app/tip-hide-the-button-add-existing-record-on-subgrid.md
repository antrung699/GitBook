---
description: '#ModelDrivenApp, #MDA, #Dataverse, #PowerPlatform, #Subgrid'
---

# Tip: Hide the button "Add Existing Record" on subgrid

&#x20;   Today, I'm excited to share a helpful tip on concealing the "Add Existing Record" button within a specific subgrid on a Main Form.

&#x20;   I've established a one-to-many relationship between the "**Account**" entity and the "**Deal**" entity. Within the "**Deal**" entity, I've created a lookup field called "_Account (ntd\_account\_id)_," linking it to the "**Account**" entity. \
&#x20;   Following that setup, I proceeded by including the "**Deals**" **subgrid** onto the **main form** of the "**Account**" entity. _On the subgrid, I select the option "Show related record" via the field Account ID relationship._

<figure><img src="../../.gitbook/assets/image (57).png" alt=""><figcaption><p>Customize entity: Deal &#x26; Account</p></figcaption></figure>

Now, we back to the Application and try to create a new Deal for Account.&#x20;

<figure><img src="../../.gitbook/assets/image (58).png" alt=""><figcaption><p>"Add existing Deal" button on subgrid</p></figcaption></figure>

When the user creates new Deals for this Account, users encounter the "Add existing Deal" button, which often leads to confusion due to its presence.&#x20;

At this time, previously, I will ask the Dev Team to hide this button immediately by using code. \
However, now, I discovered that the reason behind its visibility is **the Account ID field being set to an Option** attribut&#x65;**.**

<figure><img src="../../.gitbook/assets/image (59).png" alt=""><figcaption><p>Change the attribute of field: Option to Required</p></figcaption></figure>

{% hint style="info" %}
Set **Required = "Business required"** for a field that is being used to show related records on Subgrid.
{% endhint %}

Yup ... I did change the attribute of the **Account ID field - from "Option" to "Required".**&#x20;

Okay .. Let's go ... back to the Application and check now..... :relaxed:

<figure><img src="../../.gitbook/assets/image (60).png" alt=""><figcaption><p>The "Add existing Deal" hidden</p></figcaption></figure>

Tada :tada: The button was hidden.&#x20;

Hopping well!\
**\[NTD]yns.asia**
