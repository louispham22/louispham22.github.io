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



