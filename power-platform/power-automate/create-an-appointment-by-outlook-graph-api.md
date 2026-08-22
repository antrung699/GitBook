---
description: '#outlook, #outlookevent, #dataverse, #powerplatform, #graph'
cover: >-
  https://images.unsplash.com/photo-1649433391719-2e784576d044?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHNlYXJjaHwxfHxvdXRsb29rJTIwY2FsZW5kYXJ8ZW58MHx8fHwxNzE0MjczNTkyfDA&ixlib=rb-4.0.3&q=85
coverY: 0
---

# 📤 Create an Appointment by Outlook Graph API

Last week, I configured the synchronization of email, appointments, contacts, and tasks between Dataverse and Outlook for my client. However, this functionality is available for the Dynamcis 365 CE application and not for the Power Platform (without any D365CE apps)

Then, I tried to create an Outlook appointment from the Appointment activity by Power Automate.

## Using the Power Automate action of Outlook

I worked with 2 actions on Power Automate.

* **Send HTTP request** to Outlook: using JSON of MS Graph API
* **Create Event (V4)** to Outlook: pre-built action from the Power Automate

<figure><img src="../../.gitbook/assets/CleanShot 2024-04-28 at 11.12.26@2x.png" alt="" width="375"><figcaption><p>2 Actions</p></figcaption></figure>

## Details of the configuration

My scenarios:&#x20;

* Trigger: An Appointment created or updated (Fields: Start Time, End Time)
* Action: Create an Event in my Outlook Calendar.\
  My testing with 2 actions:
  * Using "Send HTTP Request" action
  * Using "Create event (V4)" action.

For instance, I used my calendar and my email for that:

<figure><img src="../../.gitbook/assets/CleanShot 2024-04-28 at 10.22.12@2x.png" alt=""><figcaption><p>Details of configurations</p></figcaption></figure>

***

{% hint style="info" %}
For the sample JSON code, you can find it in [**Graph Explorer**](https://developer.microsoft.com/en-us/graph/graph-explorer)**.**
{% endhint %}

<figure><img src="../../.gitbook/assets/CleanShot 2024-04-28 at 10.52.45@2x.png" alt="" width="563"><figcaption><p>My sample from Graph Explorer</p></figcaption></figure>

```json
// My sample code:
{
    "subject": "[[Subject]]",
    "start": {
        "dateTime": "[[StartTime]]",
        "timeZone": "[[TimeZone]]"
    },
    "end": {
        "dateTime": "[[EndTime]]",
        "timeZone": "[[TimeZone]]"
    },
    "attendees": [
        {
            "emailAddress": {
                "address": "[[EmailAddress]]",
            },
            "type": "Required"
        }
    ]
}
```

***

## Testing now...

Okay, I have done form my sample configuration. And run testing now...

<figure><img src="../../.gitbook/assets/_Test_Create_outlook_event.gif" alt=""><figcaption><p>Testing</p></figcaption></figure>

Thank you & Hoping well .. :tada:\
**\[NTD]yns.asia**
