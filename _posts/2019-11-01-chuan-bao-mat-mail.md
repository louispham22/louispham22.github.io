---
layout: post
title:  "Chuẩn bảo mật Mail"
date:   2019-11-01 08:30
categories: tips-trick
permalink: /archivers/chuan-bao-mat-mail
---

**Chuẩn bảo mật Mail**

Tiếp bài [xây dựng hệ thống mail server](https://tunglouis.github.io/archivers/xay-dung-mail-server-marketing). Mình sẽ tổng hợp lại 1 số kiến thức apply vào hệ thống mail server để hạn chế mail gửi đi bị vào spam.

Để xây dựng được một hệ thống mail server thì rất đơn giản. Nhưng để xử lý mal gửi đi vào inbox thì là một việc không hề đơn giản chút nào. Nên mình sẽ tổng hợp một số chuẩn bảo mật cho hệ thống mail.

**Sender Policy Framework (SPF)**
SPF hoạt động theo sơ đồ như sau:
![spf](../../images/spf.png)

Sender Policy Framework (SPF) là một phương thức xác thực email được thiết kế để phát hiện giả mạo địa chỉ Sender trong quá trình gửi email. SPF giúp xác nhận domain email bằng cách liệt kê các địa chỉ IP hoặc tên miền hợp lệ trong bản ghi DNS. Điều này cho phép các dịch vụ email của Receiver kiểm tra xem một email đến từ một địa chỉ IP hoặc miền hợp lệ hay không và sẽ đánh dấu nó là spam nếu không hợp lệ.
Bản ghi SPF phải tồn tại trên bản ghi DNS của domain Sender mà dịch vụ email Receiver phải kiểm tra khi nhận được email. [Link gốc SPF](https://en.wikipedia.org/wiki/Sender_Policy_Framework).

**DomainKeys Identified Mail (DKIM)**
DKMI hoạt động theo sơ đồ như sau:
![dkim](../../images/dkim.png)

DomainKeys Identified Mail (DKIM) là một phương thức xác thực email được thiết kế để phát hiện address Sender giả mạo trong email (email spoofing), một kỹ thuật thường được sử dụng trong phishing (thư lừa đảo) và Email spam (thư rác). [Link gốc DKIM](https://en.wikipedia.org/wiki/DomainKeys_Identified_Mail).

**Domain-based Message Authentication, Reporting & Conformance (DMARC)**
DMARC hoạt động theo sơ đồ như sau:
![dmarc](../../images/dmarc.jpg)

Domain-based Message Authentication, Reporting & Conformance (DMARC) là một phương thức xác thực email, chính sách và giao thức báo cáo. Nó xây dựng trên các giao thức SPF và DKIM, thêm liên kết đến tên miền của tác giả (From), các chính sách được phát hành cho Recipient xử lý của các lỗi xác thực, và Reporting từ  receivers đến senders, để cải thiện và giám sát việc bảo vệ domain khỏi email lừa đảo. [Link gốc DMARC](https://dmarc.org/).

Các chính sách DMARC được xuất bản trong DNS dưới dạng bản ghi tài nguyên văn bản (TXT) (RR) và thông báo những gì người nhận email nên làm với thư không liên kết mà nó nhận được.
Hãy xem xét một ví dụ DMARC TXT RR cho miền domain sender.dmarcdomain.com.

```
NAME: _dmarc
TYPE: TXT
TTL: 60
VALUE: "v=DMARC1; p=quarantine; sp=quarantine; pct=100; adkim=s; aspf=r; rua=mailto:mailaddress@dmarcdomain.com"
```
Bản ghi trên tạo 1 policy (cách ly) sẽ hướng dẫn người nhận email xử lý những email mà check DMARC fails vào thư mục SPAM/JUNK (p=quarantine) 100% (pct=100) các email không pass DKIM hay SPF. Bên cạnh đó, bản ghi còn cho biết lý do từ chối sẽ được gửi vào mail (rua=mailto:mailaddress@dmarcdomain.com) để người quản trị phía được biết.

Note: Nếu muốn gửi report cho địa chỉ email không nằm trong domain dmarcdomain.com thì sẽ phải cấu hình thêm bản ghi DNS record để reference reports tớ domain chứa email đó. Thêm bản ghi như sau:

```
NAME: dmarcdomain.com._report._dmarc.{domain chứa email nhận report}
TYPE: TXT
TTL: 60
VALUE: "v=DMARC1"
```

```
Tag Name	Purpose	
v			Protocol version
pct			Percentage of messages subjected to filtering
ruf			Reporting URI for forensic reports
rua			Reporting URI of aggregate reports
p			Policy for organizational domain
sp			Policy for subdomains of the OD
adkim		Alignment mode for DKIM
aspf		Alignment mode for SPF
```
[Cách cài đặt SPF và DKIM tham khảo tại đây](https://tunglouis.github.io/archivers/xay-dung-mail-server-marketing)

**Transport Layer Security (TLS)**
TLS hoạt động theo sơ đồ như sau:
![ssl](../../images/ssl.png)

Transport Layer Security (TLS) là một giao thức mã hóa được sử dụng để bảo vệ dữ liệu trong quá trình chuyển tiếp giữa các máy tính. Khi hai máy tính gửi dữ liệu cho nhau, thông tin được mã hóa theo cách mà cả hai đều hiểu. Tùy thuộc vào các quy tắc, một trong hai máy có thể từ chối kết nối nếu không thể tìm thấy một phương pháp mã hóa phù hợp. Trong trao đổi email, máy chủ gửi liên lạc với máy chủ nhận qua kết nối SMTP tiêu chuẩn và sẽ yêu cầu liệu có chấp nhận kết nối TLS an toàn hơn (STARTTLS) hay không. Khi thực hiện điều này, máy chủ gửi chia sẻ một danh sách các giao thức và mật mã mà nó hiểu được. Máy chủ nhận sẽ nhìn vào danh sách và chọn một tùy chọn mà cả hai đều hiểu. Sau đó nó sẽ gửi lại chứng chỉ bảo mật và khóa mã hóa công khai. Máy chủ gửi sẽ kiểm tra chứng chỉ bảo mật hợp lệ, sau đó sử dụng khóa công khai để mã hóa và gửi email. Chỉ máy chủ nhận được có khóa cá nhân có thể giải mã email, vì vậy tin nhắn được gửi được đảm bảo an toàn. Nếu một trong hai máy chủ không thể hỗ trợ kết nối được mã hoá thì chúng sẽ được mặc định kết nối Secure Sockets Layer (SSL) ít an toàn hơn hoặc kết nối không mã hóa. Khi trao đổi email giữa các tổ chức chính phủ, cả hai bên nên nhấn mạnh vào kết nối TLS và từ chối các loại kết nối khác.

Bất kỳ dịch vụ email hiện đại nào đều có thể sử dụng TLS. Trong hầu hết các trường hợp, bạn sẽ có cơ hội lựa chọn sử dụng TLS trên tất cả các kết nối. Điều này có nghĩa là các máy chủ sẽ cố gắng tạo ra một kết nối được mật mã, nhưng nếu họ không thể gửi thì chúng sẽ không được mã hóa. Điều này về cơ bản thì vẫn được , nhưng không đủ để đảm bảo cho việc sử dụng thường xuyên. Để sử dụng thường xuyên, bạn nên tạo ra quy tắc đảm bảo rằng kết nối TLS được thực hiện khi kết nối với một số miền nhất định. Nếu các máy chủ gửi và nhận không thể thống nhất về phương pháp mã hóa, kết nối sẽ bị loại bỏ và không có dữ liệu nào được gửi đi.

Năm 2002, bằng cách sử dụng kĩ thuật TLS, STARTTLS đã được phát minh ra với vai trò là một bản nâng cấp dành cho kết nối kém bảo mật thành kết nối an toàn. Nhưng STARTTLS cũng rất dễ bị khai thác bằng kỹ thuật tấn công Man-in-the-Middle (MitM) nhằm làm suy yếu khả năng mã hóa.

**Tại sao StartTLS lại không thể đảm bảo an toàn cho Email ?**
STARTTLS rất dễ bị khai thác bởi kỹ thuật tấn công MitM nhằm làm khả năng mã hoá bị suy yếu do đó giao thức này không thể đảm bảo cơ chế bảo mật cho thông điệp hay xác thực cho máy chủ. Cơ chế hoạt động của giao thức này như sau:
![starttls](../../images/starttls.png)

Khi một client ping đến máy chủ Email, client sẽ hỏi máy chủ Email có hỗ trợ SSL hay không. Tại đây, tin tặc có thể can thiệp vào quá trình thỏa hiệp này và làm Client tin rằng máy chủ Email không hỗ trợ SSL. Điều này đồng nghĩa với việc tin tặc có thể làm suy yếu khả năng mã hoá TLS hoặc thậm chí có thể đọc, sửa được nội dung Email khi Client đã bị thuyết phục và gửi thư trong trạng thái không được mã hoá.