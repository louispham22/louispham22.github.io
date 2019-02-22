---
layout: post
title:  "Giải thích Microservice Phần 1"
date:   2019-02-22 10:30
categories: microservice
permalink: /archivers/giai-thich-microservice-phan-1
---

**Giải thích Microservice Phần 1**

![](https://user-images.githubusercontent.com/10813839/53218250-fe861700-368d-11e9-8ee4-96330a399131.png)

Cảnh báo, bài viết chứa nhiều nội dung 18+, nghiêm cấm phụ nữ có thai và cho con bú. Những hình ảnh và nội dung trong bài có thể làm vẩn đục tâm hồn ngây thơ, trong trắng của các bạn

Trong bất kì lĩnh vực nào, các bạn sẽ đều bắt gặp những thuật ngữ “chuyên môn”. Ví dụ ở thế giới của thiên địa, các bạn sẽ được nghe những hot keyword như “check hàng”, “rau sạch”, “some swing”. Trong thế giới của kiếm hiệp, đó là “võ lâm giang hồ”, “khẩu quyết võ công”, “bí kíp”. Còn thế giới drama Hàn Quốc, đó là Uppa, Sunbae, Aegyo. Tóm lại là tả pì lù, không bút nào kể xiết.

Thế giới của Microservice cũng vậy, các bạn sẽ phải tìm hiểu những khái niệm, những thuật ngữ “trên trời” kiểu như Domain Driven Design, Distributed Transaction, Boundary Context, Anti-Pattern, Stranger Pattern, Anemic Domain… Những khái niệm này nếu tra cứu Google sẽ ra hàng nghìn kết quả hàn lâm mà cỡ phải IQ như Ngô Bảo Châu đọc mới hiểu nổi. Bài viết này sẽ giải thích các thuật ngữ trên bằng một hình thức khác, thấm đẫm chất 18+ và có phần siêu bựa.

# Boundary Context

Đây là một thuật ngữ được dùng nhiều trong Domain Driven Design (DDD), một chiến lược thiết kế phần mềm do Eric Evans đề xuất. Phương pháp này được áp dụng rất hiệu quả trong Microservice.
Đây là cách giải thích theo kiểu hàn lâm của Eric Evans, có lẽ chỉ dành người có IQ cao

Bounded Context

![](https://user-images.githubusercontent.com/10813839/53218306-34c39680-368e-11e9-87c4-e3059a851124.png)

Thật khó hiểu phải không? Mình đọc cũng muốn nổ tung óc :(

Mình sẽ giải thích theo kiểu dễ hiểu hơn: Ví dụ Ngọc Trinh

Ngọc Trinh là một Domain Entity (hiểu theo khái niệm Microservice), thực chất là một object với các thuộc tính như Tên, Giới tính, địa chỉ… 
Theo mô tả của Eric Evan

`An entity’s identity can cross multiple microservices or Bounded Contexts.`

![](https://user-images.githubusercontent.com/10813839/53218388-7c4a2280-368e-11e9-983d-d6dffa1ffbde.png)

Nghĩa là dư thế này:

Ở ngữ cảnh Việt Nam, Domain Entity Ngọc Trinh trở thành người Vietnamese woman có tính cách trung hậu đảm đang, có vẻ đẹp thùy mị đoan trang. Tóm lại công, dung ngôn, hạnh đủ cả.

Nhưng ở ngữ cảnh Showbiz, Ngọc Trinh lại trở thành 1 idol. Ở ngữ cảnh này, người ta chỉ quan tâm đến Nickname, số đo 3 vòng, công ty quản lý (Venus) và ko care mấy cái trên.

Còn ở ngữ cảnh thiên địa, Ngọc Trinh là trở thành “hàng”, anh em đồng râm lại chỉ quan tâm đến thuộc tính như xôi, bưởi, sò của em ý.

Như vây, cùng 1 domain entity nhưng ở những ngữ cảnh khác nhau, nó lại được thể hiện với tên và thuộc tính khác nhau, mặc dù đó vẫn chỉ là 1 mình em Ngọc Trinh. Các Context trên trở thành Boundary Context, các boundary context này sẽ giới hạn thuộc tính, và behavior của Entity tùy thuộc vào nghiệp vụ. Ví dụ Context Thiên Địa thì chỉ quan tâm em Ngọc Trinh ở thuộc tính như bưởi to, giò dài chứ ko care thuộc tính tính cách trung hậu đảm đang làm gì.

Khi thiết kế Microservice, các bạn cần xác định được các Boundary Context, data model như trên, từ đó sẽ xác định được các Microservice, data model cần thiết cho chúng, từ đó xây dựng database theo nhu cầu của Micorservice.

# Rich domain model vs anemic domain model

![](https://user-images.githubusercontent.com/10813839/53220359-a56eb100-3696-11e9-99c6-9fcd37177096.png)

Đây là một thuật ngữ trong Domain Driven. Với cách giải thích hàn lâm của Martin Flower như sau

```
The basic symptom of an Anemic Domain Model is that at first blush it looks like the real thing. There are objects, many named after the nouns in the domain space, and these objects are connected with the rich relationships and structure that true domain models have. The catch comes when you look at the behavior, and you realize that there is hardly any behavior on these objects, making them little more than bags of getters and setters
```
Tất nhiên, với cách giải thích trên thì ngay cả Toeic 990 đọc xong cũng thổ huyết mà chết.

Nếu bạn định nghĩa Domain Entity Ngọc Trinh có thuộc tính như sau:

- Name
- Address
- Sex
- Birthday

OK, rồi sao. Ngọc Trinh là người nhưng không có hoạt động gì cả, chỉ có thuộc tính mà không có behavior. Thực tế Ngọc Trinh có behavior như showHang (có thể hiểu là show hàng hay show háng đều OK), dancing… Một domain mà không có behavior là anemic domain, còn có đẩy đủ thuộc tính lẫn behavior thì là Rich domain model
Trong trường hợp Microservice và Bounded Context của bạn đơn giản (a CRUD service) thì dùng anemic domain model là đủ. Tuy nhiên nếu Microservice của bạn phức tạp, business thay đổi liên tục, thì nên thiết kế Rich domain model sẽ tốt hơn.

# Eventual Consistency

Đây là khái niệm được sử dụng nhiều trong các hệ phân tán distributed system. Thuật ngữ này được giải thích theo cách khá hàn lâm trên Wikipedia như sau:
```
Eventual consistency is a consistency model used in distributed computing to achieve high availability that informally guarantees that, if no new updates are made to a given data item, eventually all accesses to that item will return the last updated value.[1] Eventual consistency, also called optimistic replication,[2] is widely deployed in distributed systems, and has origins in early mobile computing projects.[3] A system that has achieved eventual consistency is often said to have converged, or achieved replica convergence.[4]Eventual consistency is a weak guarantee – most stronger models, like linearizability are trivially eventually consistent, but a system that is merely eventually consistent does not usually fulfill these stronger constraints.
```

Thật sự thì cách giải thích hàn lâm như trên là rất khó hiểu. Cho nên mình sẽ giải thích theo cách “nông dân” như sau
Hãy xem một scenario đơn giản của Kiến trúc Microservice như sau:
- Hoàng Kiều gọi API đến endpoint để order em Ngọc Trinh.
- Service Order thực hiện process Order của Hoàng Kiều (1 record order bao gồm order Id, customer…) được update vào database Order.
- Service Order process xong send request sang Service Payment để thực hiện trả tiền.

![](https://user-images.githubusercontent.com/10813839/53220428-0eeebf80-3697-11e9-9bee-90724da24e01.png)

Mọi thứ sẽ hoạt động bình thường nếu như các service không có trục trặc gì. Tuy nhiên đối với hệ thống phân tán như Microservice, việc các service gặp vấn đề là điều ko tránh khỏi. Điều gì xảy ra nếu như service Payment bị lỗi? Điều này dẫn tới hệ thống sẽ có 1 Order nhưng không có Payment tương ứng. Anh Kiều được chén e Ngọc Trinh miễn phí, ăn bánh không phải trả tiền. Như vậy data trong hệ thống sẽ không nhất quán (Inconsistency).

Để xử lý vấn đề này, Microservice đã sử dụng những mô hình như Retry, Circuit Breaker and Compensation Transaction, mục tiêu là sẽ rollback lại những thay đổi data trong hệ thống về trạng thái trước đó.
Ví dụ trong trường hợp trên, tại thời điểm bản ghi Order được tạo, nhưng Payment không được tạo → Dữ liệu là inconsistency. Tuy nhiên sau khi hệ thống detect được lỗi, sẽ rollback lại data (Bản ghi Order sẽ bị xóa đi) dữ liệu sẽ trở lại đồng nhất. Kiến trúc Microservice chấp nhận dữ liệu inconsistency tại một thời điểm nào đó, nhưng sau đó sẽ consistency trở lại. Cái này gọi là Eventual Consistency.

To bi con ti niu ...