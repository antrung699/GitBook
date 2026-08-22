---
description: '#PowerAutomate, #OData, #LookupFiled'
---

# 💡 Tips: Get "DisplayName" of the Lookup field on Power Automate

Recently, I have leveraged Power Automate to retrieve a list of new deals and then sent this list to the Sales Owner.

In practice, I encountered difficulties when attempting to retrieve the **Account name** and **Primary** **Contact name**, both of which are lookup fields, from the Deals entity.

<figure><img src="../../.gitbook/assets/CleanShot 2024-03-30 at 10.42.03@2x.png" alt=""><figcaption><p>Deal form: Account &#x26; Primary Contact is lookup field</p></figcaption></figure>

## 1st attempt - Using Dynamics Content

I used the value in  **Dynamic content** (OOB dynamics field content of Power Automate)

<table><thead><tr><th width="357">Dynamics content</th><th width="281">Result</th></tr></thead><tbody><tr><td><img src="../../.gitbook/assets/image (215).png" alt="" data-size="original"></td><td><img src="../../.gitbook/assets/CleanShot 2024-03-30 at 22.12.40@2x.png" alt="" data-size="original"></td></tr><tr><td><ul><li>Account (Value): Get record GUID</li><li>Account (Type): Get the entity name</li></ul></td><td><ul><li>Account (Value): <em><strong>fdf6a531-.....</strong></em></li><li>Account (Type): <em><strong>account</strong></em></li></ul></td></tr></tbody></table>

... first try, I failed to get the display name with the OOB dynamic content field of the Power Automate.

## 2nd attempt - Using Expression

Then, I used **Expression** to create the formula and get the Display Name of Account lookup field.

\---

Initially, when displaying all attributes of the **Deal entity** and then applying a filter on the lookup field "**Account**" (_ntd\_account\_id_), I discovered exciting aspects.

<figure><img src="../../.gitbook/assets/CleanShot 2024-03-30 at 22.31.25@2x.png" alt=""><figcaption><p>All attributes of the field "Account" (ntd_account_id)</p></figcaption></figure>

I observed the first value is the "Display Name" of the Account field, I promptly accessed Power Automate and employed the mentioned attribute in my expression.

<pre class="language-javascript" data-overflow="wrap"><code class="lang-javascript"><strong>//The expression:
</strong><strong>item()?['_ntd_account_id_value@OData.Community.Display.V1.FormattedValue']
</strong></code></pre>

<figure><img src="../../.gitbook/assets/CleanShot 2024-03-30 at 22.38.59@2x.png" alt="" width="375"><figcaption><p>Power Automate used Expression</p></figcaption></figure>

... And checking now:

<figure><img src="../../.gitbook/assets/CleanShot 2024-03-30 at 22.44.01@2x.png" alt="" width="375"><figcaption><p>The final result - Get the "Display Name" of Account lookup field</p></figcaption></figure>

Thank you for reading & Hoping well... :tada:\
**\[NTD]yns.asia**\
...[invite me a cup.](https://ko-fi.com/ntdyns/?ref=qr\&amp;v=2) :coffee: <mark style="color:blue;">Thank you.</mark> :heart:
