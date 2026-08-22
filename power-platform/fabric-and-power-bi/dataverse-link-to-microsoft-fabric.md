---
icon: link
cover: ../../.gitbook/assets/dv2fb.png
coverY: 0
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

# Dataverse link to Microsoft Fabric

Hi, my friends,&#x20;

Today I would like to share an exciting feature that I have shared with my colleagues recently.&#x20;

* **Dataverse link to Microsoft Fabric**
* **Create Virtual Table from Microsoft Fabric**&#x20;

Do you remember the previous data integration patterns for Dataverse?  In the past, we relied on exporting data to a DataLake and then utilizing Synapse Link to connect to Azure Synapse via Azure Storage.

And now, Microsoft has introduced a new **"Link to Microsoft Fabric"** feature, which streamlines this process even further. This feature is similar to the [_**Shortcut**_](https://learn.microsoft.com/en-us/fabric/onelake/onelake-shortcuts) functionality when ingesting data into Fabric, offering a more integrated and efficient way to connect Dataverse with Fabric.



## Try the feature "Link to Microsoft Fabric"

{% hint style="success" %}
For the prerequisites of enabling this feature, you can find detailed information [here](https://learn.microsoft.com/en-us/power-apps/maker/data-platform/azure-synapse-link-view-in-fabric#prerequisites).
{% endhint %}

Go to the Power Apps Maker portal, select the **Tables** > click the button **Analyze** > then click the "**Link to Microsoft Fabric"** button to link Dataverse tables to Fabric.

<figure><img src="../../.gitbook/assets/CleanShot 2024-09-02 at 22.25.18@2x.png" alt=""><figcaption><p>Using the Link to MS Fabric feature</p></figcaption></figure>

After signing and passing verifications, you will move to the next step "**Chose Workspace"** of Microsoft Fabric (Ex: my workspace called _**"D365 Link"**_), then click **Next** and move to the last step "**Review & Create".**

<figure><img src="../../.gitbook/assets/CleanShot 2024-09-02 at 22.27.37@2x.png" alt=""><figcaption><p>Configurations to link Dataverse to MS Fabric</p></figcaption></figure>

To complete it, just click the button **Create** and wait... Then, the new Lakehouse will be created automatically in the MS Fabric workspace.

<figure><img src="../../.gitbook/assets/CleanShot 2024-09-02 at 22.37.03@2x.png" alt=""><figcaption><p>The new Lakehouse in the MS Fabric</p></figcaption></figure>

Within the Fabric workspace, it's possible to access the Lakehouse to engage with data sourced from Dataverse efficiently.

## **Try to create a Virtual Table from Microsoft Fabric**&#x20;

Now I will share a use case for using Virtual Table which was created from Microsoft Fabric as below.

<figure><img src="../../.gitbook/assets/CleanShot 2024-09-03 at 08.54.54@2x.png" alt=""><figcaption><p>Use Case &#x26; Simple steps</p></figcaption></figure>

Ya.. with the **Dataflow Gen 2,** you can do the ETL data and then store the output to Lakehouse or Warehouse into Microsoft Fabric. For example, as below picture, I used the **Dataflow Gen 2** to create an aggregated table **"FactExpensebyBuDept"** and store this table to Data Warehouse into the Fabric.

<figure><img src="../../.gitbook/assets/CleanShot 2024-09-03 at 09.02.37@2x.png" alt=""><figcaption><p>Dataflow Gen 2: Transform - Aggregation - Store the Output</p></figcaption></figure>

After creating the **FactExpensebyBuDept** table, I will establish a Virtual Table in the Dataverse to retrieve insightful data from Fabric for the D365 App.

Go to the Power App Maker portal, in the solution, click **New > Table > Table from external Data.** The new dialog will be pop-up and you need to select the connection **"Microsoft Fabric"**

<figure><img src="../../.gitbook/assets/CleanShot 2024-09-03 at 09.30.49@2x.png" alt=""><figcaption><p>Create Virtual table</p></figcaption></figure>

... then, we just following the step-by-step to create the Virtual Table (as below is these sample steps).

<figure><img src="../../.gitbook/assets/CleanShot 2024-09-03 at 09.35.33@2x.png" alt=""><figcaption><p>Completion: Virtual table "FactExpensebyBuDept"</p></figcaption></figure>

Now.. checking on the Dynamics 365 Application.

<figure><img src="../../.gitbook/assets/CleanShot 2024-09-03 at 09.38.04@2x.png" alt=""><figcaption><p>Add the Virtual table into Dynamics 365 Application.</p></figcaption></figure>

This is an exciting feature that allows for the extension of your data and insights within Dynamics 365 and Power Apps in Fabric; brings your data into Fabric and combines, reshapes, and aggregates data with data from Dataverse.&#x20;

***

## Additional...

I would like to share some info. of this feature that I have explored. Hopefully, it can be helped. :clock:

### 1. Benefits

<figure><img src="../../.gitbook/assets/CleanShot 2024-09-02 at 22.17.54@2x.png" alt=""><figcaption><p>Benefit of Link to Fabric feature</p></figcaption></figure>

### 2. Transition diagram

<figure><img src="../../.gitbook/assets/CleanShot 2024-09-03 at 09.23.15@2x.png" alt=""><figcaption><p>Transition diagram</p></figcaption></figure>

As indicated in the before and after diagrams above, customer retired the Export to Data Lake service (1) as well as staging data stores (2) with Fabric link. For operational insights, (4), they consumed data in OneLake directly in Power BI. Some of the insights require data merge, transformation, and aggregation (3). Instead of using disparate Azure services, they standardized on the same tools built into Fabric.

{% hint style="info" %}
For more details and another cases, please find the link: [Transition from legacy data integration services to Fabric link and Azure Synapse Link for Dataverse - Power Apps | Microsoft Learn](https://learn.microsoft.com/en-us/power-apps/maker/data-platform/azure-synapse-link-transition-from-fno)
{% endhint %}

Yeahhhh... That's my sharing.&#x20;

Thank you and Hoping well.\
**\[NTD]yns.Asia**
