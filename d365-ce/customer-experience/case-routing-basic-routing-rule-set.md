---
description: Feature in D365 Customer Service
cover: ../../.gitbook/assets/DataServiceProcess.png
coverY: 0
---

# Case Routing: Basic Routing rule set

Chào mọi người!\
Hôm nay mình xin phép chia sẻ tính năng **Routing Case** - điều hướng Case trong D365 Customer Service. Và đây là một yêu cầu thực tế từ dự án cũng thực tế mình đang triển khai.

&#x20; Bài toán đặt ra: Công ty đang triển khai Customer Service. Bộ phận CX của công ty được chia ra rất nhiều Team và mỗi Team sẽ chịu trách nhiệm để xử lý những request, feedback, complain... của khách hàng với những mảng nghiệp vụ khác nhau. Và cũng cần điều hướng xử lý đúng Team ở từng vùng miền.

&#x20;Vậy với tính năng **Routing Case** thì hỗ trợ nhu cầu này đến đâu?

## Case

&#x20;Đầu tiên, **Case** trong D365 Customer Service được dùng để ghi nhận và theo dõi các sự cố, nhu cầu, feedback, complain từ phía Khách hàng hoặc đến từ nội bộ.

**Case** sẽ được ghi nhận vào hệ thống D365 Customer Service manual hoặc auto.

* Manual: Các bạn CX Agent đóng vài trò là người tiếp nhận Case và cũng sẽ là người trực tiếp tạo Case để ghi nhận vào hệ thống.&#x20;
* Auto: Case có thể được tạo tự động từ email/ task/ appointment bằng chức năng [Automatically create or update records](https://learn.microsoft.com/en-us/dynamics365/customer-service/automatically-create-update-records?tabs=customerserviceadmincenter) sẵn có. Ngoài ra, với Power Automate chúng ta cũng có thể lắng nghe Khách hàng từ các trang mạng xã hôi và từ đó có thể tạo Case để hõ trờ Khách hàng một cách kịp thời.

&#x20; Và tất cả mọi hoạt động, mọi thông tin giao tiếp cũng sẽ được tracking lại trên **Timeline** của Cas&#x65;**.**

<figure><img src="../../.gitbook/assets/Customer Service - Overall Porcess.png" alt=""><figcaption><p>Customer Service - Overall Process</p></figcaption></figure>

&#x20; Chúng ta quay lại một chút về việc ghi nhận Case. Nếu các bạn đã từng tạo các yêu cầu support đến các công ty dịch vụ, bạn sẽ tự hỏi: Vấn đề này của mình nên raise lên cho bộ phận nào để họ hỗ trợ, giải quyết nhanh nhất cho mình ??? :) \
&#x20;  Do đó, các công ty hay có các câu hỏi nhanh trên màn hình ghi nhận yêu cầu hoặc các bạn CX Agent cũng sẽ hỏi các câu hỏi phân loại khi ghi nhận. Và chính các câu hỏi phân loại đó sẽ giúp yêu cầu của mình được điều hướng nhanh tới bộ phận hỗ trợ nhanh nhất - đỡ phải đi vòng vòng qua nhiều nơi mới tới được bộ phận mình cần yêu cầu.

Và **Routing Case - tính năng sẽ hỗ trợ việc điều hướng Case một cách tự động khi Case được ghi nhận vào hệ thống.**     &#x20;

## Routing Rule Set

Routing Rule - được sử dụng để tự động điều hướng Case đến User / Team hoặc Queue (Hàng đợi) dựa trên một bộ điều kiện được bạn thiết lập sẵn.

## Configure Routing rule

_Path: Customer Service Admin Center > Routing > Basic Routing Rule Sets_\
Sau đó click **<+New>** để tạo record routing rule và thiết lập.

<figure><img src="../../.gitbook/assets/image (95).png" alt=""><figcaption><p>Basi routing rule sets</p></figcaption></figure>

Sau khi đã tạo được record, bạn clic vào **<+New Rule Items>** để thiết lập rule cụ thể

<figure><img src="../../.gitbook/assets/image (96).png" alt=""><figcaption><p>Routing Rule Set record</p></figcaption></figure>

Tại subgrid **Rule Items**, thêm mới các rule, màn hình thiết lập rule:

* **Rule Criteria:** màn hình thiết lập điều kiện của Case và khi Case thoả điều kiện thì sẽ thực hiện action "Route to" bên dưới.
* **Action:** thiết lập Case sẽ được điều hướng tới đâu. Ở đây có 2 option:
  * **User/ Team:** Case được assign tới một User cụ thể hoặc Team user cụ thể.
  * **Queue**: Case sẽ được Assign tới một hàng đợi "[Queue](https://learn.microsoft.com/en-us/dynamics365/customer-service/set-up-queues-manage-activities-cases?tabs=customerserviceadmincenter)". Trong một Queue có thể được Public hoặc Private. Đối với Queue dạng Private thì thường sẽ được chỉ định các Member thuộc Queue và khi Case được điều hướng tới Queue thì các member thuộc Queue sẽ được thấy Case này trong Queue của mình.\
    Và phần Queue này thì hẹn mọi người ở topic khác nhé.

<figure><img src="../../.gitbook/assets/image (98).png" alt=""><figcaption><p>New Rule Item</p></figcaption></figure>

Trong ví dụ của mình, mình thiết lập: Nếu như Case có type là "Inquiry" thì Case sẽ được chỉ đích danh cho một user chụ thể - **Dev Admin.**

Okay!!!! Tới đây thì Save & Close để tạo rule item nhé.

Và cuối cùng là click **\<Activate>** để kích hoạt và sử dụng Routing Rule Set.

<figure><img src="../../.gitbook/assets/image (99).png" alt=""><figcaption><p>Active Routing Rule Set</p></figcaption></figure>

## How to use Routing

Để sử dụng thì quay lại màn hình **Case.** Tại main view của **Case** > Click chọn 1 record sau đó click button **\<Apply routing rule>**

<figure><img src="../../.gitbook/assets/image (101).png" alt=""><figcaption><p>Apply routing rule</p></figcaption></figure>

Hoặc sau khi ghi nhận Case xong thì click button **\<Save & Route>** để lưu thông tin và điều hướng Case và sau đó click **OK** để xác nhận điều hướng Case.

<figure><img src="../../.gitbook/assets/image (102).png" alt=""><figcaption><p>Case form: Save &#x26; Route</p></figcaption></figure>

Giờ thì check xem nhé: Owner của Case đã được assign đến user **Dev Admin.**

<figure><img src="../../.gitbook/assets/image (103).png" alt=""><figcaption></figcaption></figure>

Đến đây thì anh em cũng sẽ hỏi, cách trên thì User sẽ là người chọn Case và apply routing rule. Vậy một khi Case đã vào hệ thống thì liệu mình có trigger tự đông và điều hướng case luôn không? Sẽ được nhé anh em. Và cách mình dùng là sử dụng **Workflow.**

## Workflow: Apply Routing Rule

Mình share thêm tip này để anh em sử dụng thử hén. Nên nhớ, mình cần license D365 Customer Service nha.

Mình tạo một Workflow, trigger trên entity **Case** khi Case được tạo. \
Sau kh check condition xong thì mình thực hiện add step **Perform Action** >> Các bạn kéo xuống mục **Command Action:** chọn action **ApplyRoutingRule**.

<figure><img src="../../.gitbook/assets/apply routing rule wf.png" alt=""><figcaption><p>Workflow > check condition > add: Perform Action</p></figcaption></figure>

Mọi người thử dùng tip này để trigger xem sao nha. Nếu run ok thì cho mình 1 like hén. :doughnut:

&#x20;                                                                                                                                                                        **\[NTD]yns.asia**
