---
description: >-
  The sample of using command bar with functional consultant. Using the command
  bar to prepare the POC/Demo solution for customer.
---

# New modern Command Bar

## My challenge

In my role as a Business Analyst/Functional Consultant, I'm tasked with presenting a DEMO to a new client. Drawing from my experience, which includes some developer skills, I'm exploring alternative approaches to executing the DEMO without relying on the development team's assistance - because of the available resources.

**My case**\
My current task involves **creating a new button on the Command bar to initiate an approval request.** Traditionally, I've sought support from the development team for such tasks. However, with the introduction of the new app designer, I've discovered the ability to handle this independently, especially in simpler cases.

**Scenario:** I'm in the process of preparing a DEMO for a customer, and I have a specific requirement: Upon creating an Account master data record, the user needs to submit this record to the IT Admin for verification and subsequent creation of a new record in another system.\
&#x20;  To demonstrate this functionality, I've crafted a custom button called "Customer Master Maintenance request" (CMM request) on the Account form's command bar. When this button is clicked, it triggers an action that updates the Account record's status to "CMM requested". Subsequently, the system initiates a Status change to send an Approval request to the IT Admin for review and approval."

## Proving steps

<figure><img src="../../.gitbook/assets/image (178).png" alt=""><figcaption><p>Sample steps</p></figcaption></figure>

## Doing...

### Create a custom button "CMM Request"

Open the new **App Designer** from make.powerapps.com >> then select the **Account view** >> click **Edit Command bar** >> click **Edit** or **Edit in new tab.**<br>

<figure><img src="../../.gitbook/assets/image (179).png" alt=""><figcaption><p>Edit command bar</p></figcaption></figure>

After that, the new windows will pop up. You must select the area where you create the custom button.

* Main grid: select if you want to create the button on the Account Main view
* **Main form:** select if you want to create the button on the Account Main form
* Subgird view and Associate view: select if you want to create the button on subgrid/ associate view into the Account main form.

And in my scenario, I will select the **Main form.**

<figure><img src="../../.gitbook/assets/image (180).png" alt=""><figcaption><p>New studio for creating custom button </p></figcaption></figure>

Now, here, click **New** >> choose **Command** >> then input the _**Label, Icon**_ to define the button as below.

<figure><img src="../../.gitbook/assets/image (181).png" alt=""><figcaption><p>New "CMM Request" custom button</p></figcaption></figure>

In the next step, we will define the **Action** of this button by [Power Fx language.](https://learn.microsoft.com/en-us/power-apps/maker/model-driven-apps/commanding-use-powerfx) So, in my situation, I will show the notification and update the Account status to "CMM Requested".

**Action >> Run Formula**

```javascript
--powerfx--
If(Confirm( "Do you want to submit CMM request?"),
    Patch(Accounts,Self.Selected.Item, {'Status Reason' : 'Status Reason (Accounts)'.'CMM Requested'}))
    
```

In some cases, you can configure the Visibility button to improve the UX/UI. :heart\_eyes: (configure in the option **Visibility >> Run Formula).**

Okay... the final step is **"Save and Publish" >>** then open the app and check...

<figure><img src="../../.gitbook/assets/image (184).png" alt=""><figcaption><p>New button is working</p></figcaption></figure>

Yeah.. the button is run as well.  The **Status Reason has been changed to "CMM Requested".**

At this time, the Approval Flow will be run because I created the Approval Power Automate trigger on the field "Status Reason" changed.

### Create an Approval - Power Automate

<figure><img src="../../.gitbook/assets/image (185).png" alt=""><figcaption><p>Sample approval flow</p></figcaption></figure>

For more details - you can find the link: [Customize the command bar using command designer](https://learn.microsoft.com/en-us/power-apps/maker/model-driven-apps/use-command-designer).

Thank you and hopping well.\
**\[NTD]yns.asia**\
<mark style="color:red;">...</mark>[<mark style="color:red;">invite me a cup.</mark>](https://ko-fi.com/ntdyns/?ref=qr\&amp;v=2) :coffee: Thank you. :heart:
