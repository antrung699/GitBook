---
description: Service Level Agreement - D365 Customer Service
cover: ../../.gitbook/assets/new_SLA.png
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

# Custom SLA for any Entity

Hello! What's up!\
&#x20;   Anh em nào đã từng vọc hay triển khai cho KH sản phẩm D365 Customer Service thì ắt hẳn đều biết về cái engine nổi bật của D365 CS - chính là [**SLA (Service Level Agreement)**](https://learn.microsoft.com/en-us/dynamics365/customer-service/overview-service-level-agreements)**.**

&#x20;   Tuy nhiên, mặc định của system, chỉ mỗi entity **Case** là được Microsoft bật sẵn tính năng SLA này. Vậy nếu như KH có nhu cầu áp dụng SLA cho các entity khác ngoài Case thì mình sẽ enable và thiết lập nó như thế nào?&#x20;

&#x20;  Hôm nay, mình sẽ nói về cách enable và configure custom SLA cho 1 entity bất kỳ.\
&#x20;   _**Và trước khi bắt đầu, mọi người lưu ý, mình chỉ có thể enable maximum 7 entity trong 1 môi trường thôi. Số lượng SLA tối đa áp dụng trên mỗi entity là 15 cái và tổng số lượng tối đa trên 1 môi trường là 100 cái.**_ \
&#x20;   Mọi người nhớ chỗ này để có gì tư vấn KH hén. :D'

Giờ thì mình tiến hành enable và configure thử nha.

&#x20;   Mình chọn entiy **Lead -** để enable tính năng SLA. Hôm trước đi làm, anh Sales Manager bên KH có hỏi, hệ thống có cái cơ chế nào để nhắc nhở hay thông báo hoặc thậm chí là warning khi Sale Man không follow Lead được giao đúng thời hạn hay không.  \
&#x20;   Ban đầu mình nghĩ, hay tạo 1 cái field Due Date rồi sau đó tạo ra nhiều cái workflow để trigger và thực hiện các action trên nếu như quá hạn. Tuy nhiên, có 1 cái yêu cầu nữa là warning/remind cho Sales Man/ Managerr trước bao nhiều ngày quá hạn. Vẫn làm được workflow nha, tuy nhiên lại tạo ra nhiều quá. \
&#x20;  Do đó, mình chọn **SLA** - vừa tracking được trên Lead, vừa cho phép user thiết lập điều kiện dynamically, vừa làm được nhiều action trên mỗi sự kiện của SLA.

Và nghĩ là làm.... Khách hàng không chịu tính sau... hehe.

## Involved Steps

Mình note trước cá bước cần thực hiện nha:

<figure><img src="../../.gitbook/assets/image (117).png" alt=""><figcaption><p>Custom SLA KPI Steps</p></figcaption></figure>

## Enable SLA for Entity

Mọi người mở Solution cần customize cho cái custom entity nha. Sau đó click chọn **Entity** cần enable SLA lên và tick chọn **SAL** >> **Save** là xong.\
_&#x4C;ưu ý: Môt khi đã enable rồi là không undo lại được nha mọi người. Bút sa gà xối mỡ nha._

<figure><img src="../../.gitbook/assets/image (105).png" alt="" width="563"><figcaption><p>Enable SAL for entity</p></figcaption></figure>

## Create SLA KPI field&#x20;

Sau khi đã enable rồi, thì bước tiếp theo là xác định cái SLA nào cần apply trên entity.\
Cụ thể là anh Sales Managerr có hỏi, anh muốn force các bạn Sales man phải liên lạc với Khách hàng trong vòng 2 giờ đồng hồ khi **Lead** được phân công cho bạn đó.&#x20;

Hehe, thấy cái vụ liên lạc là quen quen rồi. Do đó mình đặt tên là "**First Contact In" -** nghĩa là **Liên lạc đầu tiên trong xxx (giờ).**&#x20;

Ở trong entity Lead, mình tạo 1 field _**lookup**_ tới _**entity "SLA KPI Instance"  -** field "First Contact In"_

<figure><img src="../../.gitbook/assets/image (106).png" alt=""><figcaption><p>Create lookup field for custom SLA KPI Instance</p></figcaption></figure>

&#x20;  Và mọi người sẽ thấy mình có tạo thêm 1 field _"**First Contact Date"**_ để log lại ngày liên hệ KH đầu tiên của Sales Man. Mục đích, là lợi dụng field này có data để làm điều kiện **Successful** cho SLA KPI.

## Create Quick View Form for SLA KPI

Sau khi tạo SLA KPI xong rồi, mình vào entity _**SLA KPI Instance**_ để tạo 1 Quick view form cho cái custom SLA KPI cần áp dụng trên **Lead.**

Quick view form: _**First Contact In - Lead**_

<figure><img src="../../.gitbook/assets/image (107).png" alt=""><figcaption><p>Create Quick view form - for Lead</p></figcaption></figure>

Sau đó vào form: click Insert >> chọn **add Timer control** cho Quick View form:<br>

<figure><img src="../../.gitbook/assets/image (118).png" alt=""><figcaption><p>Add Timer Control</p></figcaption></figure>

Tới đây coi như là xong việc thiết lập cho custom SLA rồi. Bước tiếp theo là vào **Lead** form, insert cái Quick view form vừa tạo cho field SLA KPI **"First Contact In"**

## Add Quick view form on Entity

Mở main form **Lead** và insert Quick view form như hình. Nhớ chọn đúng field SLA KPI cần thiết lập nha.

<figure><img src="../../.gitbook/assets/image (108).png" alt=""><figcaption><p>Insert Quick View form of SLA KPI for Lead entity</p></figcaption></figure>

Tới đây là hoàn thiện xong phần configure cho Custom SLA cho entity Lead rồi. Giờ mình sẽ thiết lập SLA và SLA KPI conditioni để trigger và apply cho **"First Contact In"** trên entity **Lead** để test thử.

## Create SLA and configure condition.

_Path: Customer Service Admin Center > Operation > Service Terms_<br>

<figure><img src="../../.gitbook/assets/image (109).png" alt=""><figcaption><p>Service terms in CS Admin Center</p></figcaption></figure>

1.  Tạo mới record **SLA KPI**\
    Mọi người chọn **Manage** ở mục _**SLA KPIs**_ để tạo vào và tạo mới SLA KPI - **"First Contact In"**<br>

    <figure><img src="../../.gitbook/assets/image (110).png" alt=""><figcaption><p>Create SLA KPI record for custom SLA</p></figcaption></figure>
2.  Tạo mới **SLA** apply cho entity **Lead**\
    Mọi người chọn **Manage** ở mục _**Service-level agreements (SLAs)**_ để tạo vào và tạo mới SLA rule cho custom SLA - **"First Contact In".**<br>

    <figure><img src="../../.gitbook/assets/image (112).png" alt=""><figcaption><p>SLA applied for Lead entity</p></figcaption></figure>

    Ở đây, do nhu cầu của KH nên mình thiết lập khá là nhiều rule cho SLA "First Contact In" trên Lead nha mọi người. \
    **Note:**\
    Trong mục thiết lập SLA Items --> mọi người có thể thiết lập gửi mail, gửi notification, tạo task... để báo tới Sales Man/ Manager ở mục **Configure Actions** nhé.<br>

    <figure><img src="../../.gitbook/assets/image (113).png" alt="" width="563"><figcaption><p>Configure Actions</p></figcaption></figure>
3. **Active** and set **Default SLA** cho entity **Lead**\
   Sau khi đã tạo SLA và thiết lập xong thì bước cuối cùng là Active và Set Default SLA vừa tạo cho Lead nhé.

## Checking now....

Tạo 1 Lead record đúng với cái điều kiện đã thiết lập trong SLA - SLA Items thử nha.

Lead ban đầu được tạo ra nhưng chưa apply được SLA "First Contact In" - vì Lead này mình đang trigger thêm hành động Lead được Assign cho Sales Man nữa.

<figure><img src="../../.gitbook/assets/image (114).png" alt=""><figcaption><p>Lead created</p></figcaption></figure>

Lead được Assign cho Sales man **Tester --> SLA "First Contact In" ngay lập tức được tính toán.** \
Và user cần phải contact với KH trên của Lead này trong vòng **14h59m21s.**

<figure><img src="../../.gitbook/assets/image (115).png" alt=""><figcaption><p>SLA is applied</p></figcaption></figure>

Và khi đã liên hệ tìm hiểu nhu cầu KH xong thì Sales man tiến hành Mark Complete task này để hệ thống ghi nhận thời điểm hoàn thành và mark SLA Succeeded.

<figure><img src="../../.gitbook/assets/image (116).png" alt=""><figcaption><p>Succeeded SLA</p></figcaption></figure>

Bingo! Tới đây là hoàn thành xong việc tạo và thiết lập 1 custom SLA KPI cho entity Lead. \
Mọi người thử xem sao nhé.

&#x20;                                                                                                                               **\[NTD]yns.asia**
