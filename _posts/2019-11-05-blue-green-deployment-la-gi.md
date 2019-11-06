---
layout: post
title:  "Blue/Green Deployment là gì?"
date:   2019-11-05 10:30
categories: tips-trick
permalink: /archivers/blue-green-deployment-la-gi
---

![blue-green](../../images/bluegreen1.webp)

Trong thời gian công tác tại Nhật, mình có tham gia deploy dự án cho khách hàng. Yêu cầu của người nhật khá là khắt khe về việc deploy mà bị downtime. 

Vì vậy mình đã tham khảo giải pháp Blue/Green deployment để đáp ứng nhu cầu của khách hàng. 

**Blue/Green deployment là gì?**

Đầu tiên các bạn hình dung về infra của hệ thống truyền thống. chúng ta thường sẽ sử dụng một nguồn tài nguyên phần cứng đúng không các bạn. Khi deploy một phiên bản mới, chúng ta deploy lên chính phần cứng đó - nơi service đang chạy. Cài cắm, thêm cấu hình, update function...

Điều này dẫn đến một vấn đề là Downtime trong quá trình deploy, nói cách khác là users không thể sử dụng được service trong thời gian deploy. Nó lý giải tại sao người ta hay chọn deploy lúc nửa đêm, và tạo ra mấy màn hình thông báo Maintenance.

![maintenance](../../images/img_system_base.png)

Để giải quyết vấn đề trên, Blue/Green deploy được ra đời. Ý tưởng của nó là sử dụng hai tài nguyên phần cứng song song giống hệt nhau để tạo ra hai môi trường production (gọi là blue và green). Quá trình deploy bằng phương pháp Blue/Green sẽ diễn ra như sau:

- User đang sử dụng dịch vụ qua môi trường Blue
- Khi release sẽ được deploy lên môi trường còn lại là Green (Môi trường này user đang không sử dụng)
- Sau khi Deploy và test mọi thứ trên môi trường Green OK. Thì ta chỉ cần switch route users qua môi trường Green vừa deploy. (Ở đây mình dùng DNS switch trên Route53)
- Môi trường Blue bây giờ trở thành môi trường dự bị cho lần release tiếp theo. 

Các bạn xem hình bên dưới: 

![blue](../../images/blue.png)

**Ưu điểm**

- Giảm thời gian downtime

Như các bạn đã thấy ở phần giới thiệu phía trên, thời gian downtime do deployment đã được giải quyết. Users vẫn sử dụng service bình thường trong quá trình deploy, khi phiên bản mới sẵn sàng trên môi trường dự bị (green hay blue) thì request của users được route qua môi trường mới mà thôi. Quá trình deploy diễn ra mượt mà và không hề tạo ra bất kì phiền hà nào trong trải nghiệm với users.

- Dễ dàng rollback khi gặp trouble

 vì chúng ta có sẵn hai môi trường production nên sau khi deploy, dù sự cố bất ngờ có phát sinh thì dễ dàng rollback lại.

 **Nhược Điểm**

- Đắt đỏ
	- Việc sử dụng đến hai môi trường production sẽ kéo theo vấn đề chi phí. Do đó quy mô service và ngân sách không hợp lý thì việc triển khai B/G deploy đôi khi biến thành "lợi bất cập hại".

- Deployment sẽ rất khó khăn khi có sự thay đổi lớn với database

	- Phần database rất khó để cũng tách ra riêng biệt cho hai môi trường blue/green, do đó nó thường là phần giữ nguyên, không được switch khi deploy. Dẫn đến một việc là nếu trong lần release, schema của bảng dữ liệu có nhiều thay đổi thì deploy sẽ càng phức tạp. Có thể hình dung là đầu tiên ta phải thiết kế logic phía ứng dụng phiên bản mới sao cho tương thích với cả schema cũ, rồi deploy, rồi sau đó mới chỉnh sửa bỏ schema cũ để chỉ support với schema mới v...v...

