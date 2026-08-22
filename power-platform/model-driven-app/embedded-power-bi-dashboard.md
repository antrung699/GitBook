---
description: Power BI, Model Driven App
cover: ../../.gitbook/assets/power-bi-microsoft-diagram.png
coverY: 69.32968536251711
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

# Embedded Power BI - Dashboard

Hello mọi người.

&#x20;  Chắc hẳn mọi người đã làm nhiều về Dashboard trong D365 CE rồi nhĩ! Dashboard trong D365 ngày trước chia làm hai loại chính là Classic Dashboard và Intractive Dashboard, sau này khi phát triển mạnh mẽ Power Platform thì Microsoft đã cho phép chúng ta nhúng thẳng report/dashboard Power BI trên Dashboard area ở D365.\
&#x20;   Có thể nói, việc cho phép nhúng thẳng Power BI report/ dashboard vào D365 mở ra cho chúng ta khả năng sáng tạo rất rất nhiều. Và mới đây, Microsoft con enable thêm tính năng **Visualize this view** rất hiệu quả, giúp user có thể tạo nhanh report và phân tích nhanh số liệu.

<figure><img src="../../.gitbook/assets/image (119).png" alt=""><figcaption><p>Visualize this view</p></figcaption></figure>

Bài viết này mình sẽ nói vè cách nhúng Power BI report vào Dashboard và cách nhúng vào form trên Model Driven App nhé.

## Embedded Dashboard PwBI

&#x20;   Đầu tiên thì chúng ta cần có cái Dashboard hay cái Report PwBI đươc public lên Power BI Service trước đã - powerbi.com đó anh em.\
&#x20;   Việc public cái report này lên trên Power BI Service thì mọi người biết rồi hén - chỉ cần mở file .pbix bằng Power BI Desktop, sau đó đăng nhập tài khoản rồi click **Public** --> BÙM xong: Report đã được public lên Power BI Service.\
_&#x4E;ote: Mọi người lưu ý, chỗ này khi public thì mình cần chọn 1 cái Workspace khác vs "My Workspace" nha._

<figure><img src="../../.gitbook/assets/image (122).png" alt=""><figcaption><p>Public PwBI report to Power BI Service</p></figcaption></figure>

Sau khi đã có report rồi thì giờ vào **Solution** của mình và tạo Dashboard thôi.

<figure><img src="../../.gitbook/assets/image (120).png" alt=""><figcaption><p>Power BI embedded Dashboard</p></figcaption></figure>

Sau đó thì chọn như hình:<br>

<figure><img src="../../.gitbook/assets/image (123).png" alt=""><figcaption><p>Configure Power BI Embedded Dashboard</p></figcaption></figure>

1. Chọn **Power BI Report:** nếu mọi người muốn nhúng nguyên report (trên PwBI Service).\
   Chọn **Power BI Dashboard:** nếu mọi người muốn nhung Dashboard (trên PwBI Service).
2. **Workspace**: chính là Workspace mà mọi người public report lúc nãy.
3. **Power BI report:** chọn Report mọi người cần nhúng vào Dashboard D365.

Và click **OK** để hoàn thành.

Tuy nhiên, còn 1 lưu ý nhỏ, sau khi đã tạo Dashboard xong thì mọi người phải nhớ vào **App** chọn **Dashboard** và nhớ select cái DB Power BI Embedded vừa rồi nữa.&#x20;

Tới đây là xong phần Dashboard Power BI Embedded nha.

<figure><img src="../../.gitbook/assets/image (124).png" alt=""><figcaption><p>Sample Power BI Embedded Dashboard</p></figcaption></figure>

&#x20;   Thế nhưng anh em có tự hỏi, lúc mà deploy cái Dashboard Power BI Embedded từ môi trường DEV sang môi trường PRODUCTION thì sẽ như nào không? Bởi, nếu lúc dev, thì trên môi trường DEV mọi người đang chọn là cái Report PwBI dùng cho môi trường DEV, lên PRODUCTION thì mình phải chọn Report PwBI dùng cho PRODUCTION. \
&#x20;   Do đó, mình đã sử dụng **Environment Variables (Biến môi trường)** để khai báo Report Power BI nào dùng cho DEV, cái nào dùng cho PRODUCTION.

## Using Variables to change PwBI report

&#x20;    Do mình ko có 2 environment để làm, nên để Demo, thì mình sẽ thay đổi value của Variable để show report nhé.  Một khi đã thay đổi Value của Environment Variable trên PRODUCTION rồi, thì khi deploy từ solution từ DEV qua PRODUCTION nó cũng sẽ không bị override đâu.

&#x20;   Mình vào **Solution,** chọn Power BI Embedded dashboard (nếu đã có ) hoặc chưa có thì mọi người tạo mới nha. Mình sẽ sử dụng lại cái dashboard khi nãy.\
&#x20;   Click **Edit** dashbaord > chọn **Use environment variable** để khai báo report cho từng môi trường nhé.

<figure><img src="../../.gitbook/assets/image (128).png" alt=""><figcaption><p>Edit dashbaord and using environment variable</p></figcaption></figure>

Tạo biến môi trường mới, hệ thống sẽ bắt chọn Default Work Space và Default Report. Tuy nhiên, mình có thể tạo **<+New Value>** để override cái giá trị mặc định.

<figure><img src="../../.gitbook/assets/image (129).png" alt=""><figcaption><p>New variable with default value</p></figcaption></figure>

Sau khi tạo xong, mọi người quay lại chỗ component **Environment Variables** > Chọn biến cần sửa như hình. Rồi copy giá trị câu Json vào là ok.

<figure><img src="../../.gitbook/assets/image (131).png" alt=""><figcaption><p>New value for Variable</p></figcaption></figure>

**BÙM!!!** vậy là new value xong là ghi đè được report rồi. Trên môi trường PRODUCTION, bạn chỉ cần vào Biên môi trường chỉnh sửa lại là được. :)

Cấu trúc câu Json và cách tìm value mình note dưới này nha mọi người:

<pre><code><strong>{"group":{"id":"[GroupID]","name":"[Workspace Name]"},"component":{"id":"[Report ID]","name":"[Report Name]","type":"Report","embedUrl":"https://app.powerbi.com/reportEmbed"}}
</strong></code></pre>

Để xác định các tag trong đoạn json ở trên, bạn mở cái report Power BI cần nhúng ra để lấy htông tin:

<figure><img src="../../.gitbook/assets/image (127).png" alt=""><figcaption><p>Open a PwBI Report</p></figcaption></figure>

* **\[Group ID]:** chính là khung màu xanh (sau chữ _**groups/**)._
* **\[Workspace Name]**: chính là khung màu tím (tên của Workspace chứa report)
* **\[Report ID]:** chính là khung màu đỏ (sau chữ _**reports/**)._
* **\[Report Name]:** chính là khung màu cam (tên của report đấy).

<pre><code>// Sampe PwBI Report: FE_Poc
<strong>{"group":{"id":"d5682936-b896-4a08-8b3b-d1844fb6fb55","name":"Fabric"},"component":{"id":"1bd6d6f2-5627-4c08-bfbd-938159019a24","name":"FE_Poc","type":"Report","embedUrl":"https://app.powerbi.com/reportEmbed"}}
</strong></code></pre>

Giờ thì check thử thôi nào....

<figure><img src="../../.gitbook/assets/image (132).png" alt=""><figcaption><p>New PwBI Report with new value of Variable</p></figcaption></figure>

&#x20;   Hiện tại còn 1 phần nữa là nhúng cái Report vào Form trên Model Driven App và add thêm pre-filtering cho cá report đó theo record đang được mở.

Nhưng mà giờ hơi trễ chút, nên hẹn mọi người ở bài sau nha.

Thân chào mọi người!\
&#x20;                                                                                                                                **\[NTD]yns.asia**

