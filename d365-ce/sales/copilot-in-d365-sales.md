---
description: 'Preview feature: Sales Copilot'
cover: ../../.gitbook/assets/Copilot Medium.jpeg
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

# Copilot in D365 Sales

Hello mọi người!\
Sau khi Chat GPT làm mưa làm gió trên đất liền, thì Microsft sau đó cũng đã công bố là gã khổng lồ đứng sau cùng đầu tư và hợp tác gới Open AI. Chính vì thế mà không lâu sau cái tên **Copilot** cũng đã được Microsoft giới thiệu trong hầu hết các sản phẩm của mình như Office 365, Dynamics 365, Power Platform, ... Và sắp tới với bản build mới cho Windows 11 thì **Copilot** cũng sẽ chính thức thay thế **Cortana.**&#x20;

Release Wave - cũng là một trong những mộc thời gian Microsft release và giới thiệu các tính năng mới cho các sản phẩm thuộc nhóm Business Application của mình. \
Tháng 10/2023 tới, sẽ là đợt Release Wave 2 trong năm 2023 của Microsoft. Tuy nhiên, trong quá trình làm dự án, mình cũng đã phát hiện bản preview sớm trên D365 Sales ....\
... Chính là [**Sales Copilot (preview).**](https://learn.microsoft.com/en-us/dynamics365/sales/copilot-overview)

Và hôm nay mình sẽ thử enable rồi configure và sử dụng thử xem sao. :)

## Enable Sales Copilot

Vì tên gọi là Sales Copilot nên mình vào app Sales Hub để enable tính tăng nhé. Path: Sales Hub > App Settings > Sales Copilot (Preview) Click vào Set up Sales Copilot để enable và configure nhé.

<figure><img src="../../.gitbook/assets/image (83).png" alt=""><figcaption><p>Enable Sales Copilot</p></figcaption></figure>

Trên app Sales, thì copilot đang hỗ trợ một số tính năng trên 2 entity chính là: **Lead** và **Opportunity.**\
Sau khi click setup thì chúng hệ thống sẽ hỏi mình áp dụng tín năng Sales Copilot trên app nào nhé. Chọn xong nhớ Confirm để xác nhận. (_Mình áp dụng 2 tính năng Compose và Chat cho app Sales Hub luôn nhé)._\
_Lưu ý: Sales Copilot cho áp dụng luôn trên các custom app luôn anh em ạ. Thử xem sao nha!_<br>

<figure><img src="../../.gitbook/assets/image (85).png" alt=""><figcaption><p>Apply features for apps</p></figcaption></figure>

## **Configure Sales Copilot**

<figure><img src="../../.gitbook/assets/image (87).png" alt=""><figcaption><p>Configure Record Summary</p></figcaption></figure>

Như đã nói, hiện tính năng Sales Copilot chỉ đang áp dụng trên 2 entity là **Lead** và **Opportunity.** Các bạn chọn view mặc định để Copilot truy xuất dữ liệu cho 2 entity trên và click **Save** để hoàn thất configure cho tính năng **Record Summary** nhé.\
\
Và các tính năng mà Sales Copilot mang lại được Microsoft giới thiệu, gồm có

* Record summarization: tổng hợp thông tin record
* Record catch up: nắm bắt các thay tay đổi của record
* Meeting preparation: thông báo và tổng hợp các cuôc họp sắp đến
* Email assistance: hỗ trợ soạn thảo email
* News updates: cập nhật nhanh thông tin về Customer\
  \--\
  Tuy nhiên, tính tới thời điểm hiện tại như trên hình, chúng ta có thể thấy Sales Copilot đợt này chỉ mới có 3 tính năng chính là **Record Summary,** **Record catch up** và **Compose (**&#x73;oạn email).

## **Sales Copilot Features**

* **Record Summary.**
*   **Record catch up:**\
    Trước hết cần turn on audit nhé. Sau đó là chọn Default view cho 2 entity và **Save.**

    <figure><img src="../../.gitbook/assets/image (88).png" alt=""><figcaption><p>Configure Record Catch up</p></figcaption></figure>

    Tới đây xem như là mình configure xong rồi, giờ thử xem sao nhé.\
    Àh, mà mọi người muốn bổ sung thêm các app sử dụng Sales Copilot thì click lại vào mục **Manage apps** để thêm vào nhé.

## **Using Sales Copilot**

Anh em configure xong nhớ refresh lại nha. Sau đó thì compact em nó thôi.

<figure><img src="../../.gitbook/assets/image (89).png" alt=""><figcaption><p>Using Copilot</p></figcaption></figure>

Trên sidepane, mọi người sẽ thấy icon Copilot nhỏ nhỏ xynh xynh <3. Click vào rồi hỏi chuyện em nó thôi.\
User: "Hi Copilot"\
Copilot: " Try a different request Copilot can help with specific tasks. Type / for suggestions or choose from prompts below" ==> Em ấy vẫn chưa smart lắm anh em nhĩ. :D \
Nói vậy thôi, chứ mới preview mà, phải theo format con nhà người ta một tí.<br>

<figure><img src="../../.gitbook/assets/image (90).png" alt=""><figcaption><p>Wrong format question</p></figcaption></figure>

Okay, mình thử chọn theo suggestion của Copilot: **Summarize opportunity**\
**-->** Woah, @ cái là truy vấn được record Opportunity luôn nhé.<br>

<figure><img src="../../.gitbook/assets/image (91).png" alt=""><figcaption><p>Ask Summarize Opps</p></figcaption></figure>

Kết quả:\
Copilot: " Here is the opportunity summary for "\[NTD]Opps Bán máy":

The potential customer for this opportunity is Công ty CP Luu Minh and the current status of the opportunity is Open. The estimated revenue amount for this opportunity is 500,000,000đ."\
\--> Cũng ổn anh em nhĩ. \
Nhưng anh em nào xài qua **Power BI** rồi, thì so sánh cái [**Smart narrative summaries**](https://learn.microsoft.com/en-us/power-bi/visuals/power-bi-visualization-smart-narrative) vs em nó thử thế nào nhé. Hoặc cái visual [Q\&A](https://learn.microsoft.com/en-us/power-bi/natural-language/q-and-a-intro) nữa.&#x20;

<figure><img src="../../.gitbook/assets/image (92).png" alt=""><figcaption><p>Summary Result</p></figcaption></figure>

\-----\
Thêm một câu về Record Catch up nhé. Tình hình là data mình ko có nên Copilot chưa catchup đc. Anh em thử trên môi trường của mình xem sao nha.<br>

<figure><img src="../../.gitbook/assets/image (93).png" alt=""><figcaption><p>Record Catch up</p></figcaption></figure>

\----\
Anh em nào mà hay viết mail cho sếp, thì thử chức năng **Compose** của Sales Copilot nha.\
Em ấy nhiều chữ Tiếng anh lắm, còn tiếng việt thì đợi thêm nha. Hehe.<br>

<figure><img src="../../.gitbook/assets/image (94).png" alt=""><figcaption><p>Compose</p></figcaption></figure>



Thôi tới đây tạm kết bài nha. Chúc anh em ngủ ngon!\
&#x20;                                                                                                                                          **\[NTD]yns.asia**
