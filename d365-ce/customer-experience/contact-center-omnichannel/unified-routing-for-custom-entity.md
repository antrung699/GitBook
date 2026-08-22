---
description: '#UnifiedRouting, #Distribution, #Workstream, #D365ContactCenter, #ideas'
cover: ../../../.gitbook/assets/Joint+Venture+Partnership.jpg
coverY: 100.96069223000062
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

# Unified Routing for custom entity

Ciao friends, how are you? :relaxed:

In this blog post, we'll explore how to activate **Unified Routing** for a **Custom Entity.**

## **My idea**

<mark style="background-color:green;">Utilize the Unified Routing feature to efficiently distribute work items to team members.</mark>&#x20;

{% hint style="success" %}
**Scenario**

The client has a QC team with multiple members. A Quality Order is created daily and should be assigned to the QC team members accordingly, based on the capacity of each member.

My client is using the D365 Customer Service and Contact Center. And the QC Team is going to these apps.

To address this requirement, I aim to leverage the **Unified Routing** capability to **distribute Quality Orders** to QC team members.&#x20;

\--

These are just my thoughts, and I believe there are many approaches:bulb:to this case. :heart\_eyes:
{% endhint %}

&#x20;     Now, let's explore how to enable **Unified Routing** for the custom entity **Quality Order** in the D365 Contact Center/ Customer Service.

## How to set up Unified Routing for Custom Entity?

{% hint style="warning" %}
I'm using the D365 Contact Center trial environment for this blog post&#x20;
{% endhint %}

To implement my solution, I need to enable **Unified Routing** and create a custom entity called **Quality Order**. This entity serves as a request item that will be distributed to a QC team for work.

### Overall step

<figure><img src="../../../.gitbook/assets/Steps-Unified-Routing.png" alt=""><figcaption><p>Overall Steps</p></figcaption></figure>

### Detail step

{% stepper %}
{% step %}
**Provision unified routing in the D365 Customer Service/ D365 Contact Center**

{% tabs %}
{% tab title="1.Enable Unified routing" %}
In the apps **Contact Center Admin center,** go to the **Routing** menu.

Ensure the **Unified routing** capacity was enabled by default. If not, please turn it on.

<figure><img src="../../../.gitbook/assets/1.EnableUnifiedRouting.png" alt=""><figcaption><p>Enable unified routing</p></figcaption></figure>
{% endtab %}

{% tab title="2.Enable Queue capability for Entity" %}
Go to the solution, then turn on the **Queue** capability for the Quality Order entity.

<figure><img src="../../../.gitbook/assets/2.Enable_Queue-QualityOrder.png" alt=""><figcaption><p>Enable Queue capability for Entity</p></figcaption></figure>

{% hint style="success" %}
As the OOB functionalities, only the Case entity was applied to the Unified Routing capacity.

So, for another entity, you must enable **Queue** capability to use this feature.&#x20;
{% endhint %}
{% endtab %}
{% endtabs %}
{% endstep %}

{% step %}
**Necessary Unified Routing Configurations**

{% tabs %}
{% tab title="1.Add a new Routing Record" %}
In the **Routing** page, go to the **Setup record routing**

<figure><img src="../../../.gitbook/assets/image.png" alt=""><figcaption><p>Setup record routing</p></figcaption></figure>

After that, click **<+Add>** button and select the **Quality Order** entity to use the unified routing feature.

<figure><img src="../../../.gitbook/assets/3.Add Record Routing.png" alt=""><figcaption><p>Add Quality Order in the record routing</p></figcaption></figure>

... after validation, the system will add the Quality Order entity into this list

<figure><img src="../../../.gitbook/assets/3.1.RecordRouting-QualityOrder.png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="2.Create Queue" %}
Move on, creating a **Queue** for the QC Team, and add the Member for this queue.

The **Queue** is used in the Workstream Record of the Quality Order. Furthermore, in the Queue, we also define the distribution method, which is the engine that distributes the Work Item (Quality Order) to the queue members.

In the **Queue** page, open the **Advanced queues.** Then, click **<+New>** to create QC Team queue as below.&#x20;

<figure><img src="../../../.gitbook/assets/4.CreateQueue-QC Team.png" alt=""><figcaption><p>Create QC Team Queue</p></figcaption></figure>

After creating the QC Queue, we must add the member to the Queue and define the distribution method.

<figure><img src="../../../.gitbook/assets/4.1Queue-Configuration.png" alt=""><figcaption><p>Queue configuration.</p></figcaption></figure>

{% hint style="success" %}
For the testing, I used the standard method provided by the system - **Highest capacity.**

For more information, you can check the [link](https://learn.microsoft.com/en-us/dynamics365/customer-service/administer/assignment-methods?wt.mc_id=d365cs_inproduct_page)**.**
{% endhint %}
{% endtab %}

{% tab title="3.Create Flow: Auto routing" %}
For the Custom entity, we need to create a Flow to trigger the Unified Routing action to route the record to the Queue automatically.

In my approach, I must create a Flow to **unified-routing** the **Quality Order** automatically.

My flow configuration:

<figure><img src="../../../.gitbook/assets/5.CreateFlow.png" alt=""><figcaption><p>Flow configuration</p></figcaption></figure>

Details of Step 2:

* Action step: **Perform an unbound action**
* Action name: **msdyn\_ApplyRoutingRuleEntityRecord**
* Item/Target: _**entitynames (\<entityRecordId>)**_ \
  My example entity: ntd\_qualityorders , the recordId was obtained from **Step 1**
{% endtab %}
{% endtabs %}
{% endstep %}

{% step %}
**D365 Contact Center Configurations**

As an assumption, the QC team member will use the D365 Contact Center and use Contact Center Workspace apps (OOB apps). Therefore, we need to do at least the configurations for this app.

Therefore, after completing these necessary configurations above, we will move on to the configurations for the D365 Contact Center.

{% tabs %}
{% tab title="1.Create Workstream" %}
Create **Record** Workstream for the **Quality Order** entity.

<figure><img src="../../../.gitbook/assets/6.CreateQC-Workstream.png" alt=""><figcaption><p>Create QC Workstream - type Record - entity Quality Order</p></figcaption></figure>

After that, we need to **create** the **unified routing rule** for this workstream. By this configuration, the Quality Order record will be auto-routed to the QC Team queue.

<figure><img src="../../../.gitbook/assets/7.CreateIntakeRule-for-Workstream.png" alt=""><figcaption><p>Create intake rule for Workstreams</p></figcaption></figure>

... And then, we configure (optional) the **Session** and **Customer service representative notifications.** For more details, you can find them in the link: [Session template](https://learn.microsoft.com/en-us/dynamics365/customer-service/administer/session-templates) and [Notification](https://learn.microsoft.com/en-us/dynamics365/customer-service/administer/notification-templates).

{% hint style="success" %}
By default, the system will set **"Entity records session - default"** and **"Entity record - assign - default"** for the Workstream that has type **Record.**
{% endhint %}

<figure><img src="../../../.gitbook/assets/7.1WorkstramConfigured.png" alt=""><figcaption><p>Configure Session and Notification for Workstream.</p></figcaption></figure>
{% endtab %}

{% tab title="2.Create Experience Profile for QC Team" %}
Experience profiles enable you to create targeted app experiences for customer service representatives (service representatives or representatives) and supervisors, and are an alternative to building and maintaining custom apps. With the experience profiles, administrators can create custom profiles with specific session templates, conversation channels, and productivity tools. These profiles can then be assigned to users... [more details.](https://learn.microsoft.com/en-us/dynamics365/customer-service/administer/overview?wt.mc_id=d365cs_inproduct_page)

And in my solution, I would like to create a new **QC Team profile** and just apply it to the QC Team members.

To configure, you navigate to **Workspaces,** then open the **Experience profiles,** click **<+New>** to create a profile

<figure><img src="../../../.gitbook/assets/8.CreateExperienceProfile-QC Team.png" alt=""><figcaption><p>Create QC  Team Profile</p></figcaption></figure>

After that, we need to do some configurations on this profile:&#x20;

1. Add user to profile
2. Select Entity session template: I created the Quality order session entity.
3. Configure Inbox view: My Work Items, Open Work Items, Closed Work Items view.

<figure><img src="../../../.gitbook/assets/9.Configure-QC Team Profile.png" alt=""><figcaption><p>Profile configuration</p></figcaption></figure>
{% endtab %}
{% endtabs %}

Tada... :tada: I completed my necessary configurations for my approach. Now I will try to **create a new Quality Order record,** and my expectation is that the Quality Order record will be auto-routed to workstreams **QC Workstream.**
{% endstep %}

{% step %}
### Checking...!

My demo instance, I have 2 QC Members: **NguyễnTrung Dũng** (it's me :innocent:) and **HS DEV.** For the quick checking, I login to the **Customer Service Hub** then create **a Quality Order** record directly, and Owner of these records I will change to another user.&#x20;

Now, let's check the result video.  And thank you for your patient reading. :heart\_eyes\_cat:

{% embed url="https://youtu.be/kQrpk8xh9qU" %}
Checking Result
{% endembed %}

***

<figure><img src="../../../.gitbook/assets/CheckingNow.gif" alt=""><figcaption><p>GIF of the checking result</p></figcaption></figure>
{% endstep %}
{% endstepper %}

Hoping well! :herb:\
**\[NTD]yns.asia**<br>
