---
layout: post
title:  "NODES AND CLIENTS"
date:   2020-11-20 16:00
categories: erc20
---

# NODES AND CLIENTS

Để Ethereum hoạt động theo cách phi tập trung, nó cần một mạng lưới các nodes phân tán có thể xác minh các block và dữ liệu transaction. Bạn cần một ứng dụng, được gọi là khách hàng, trên thiết bị của bạn chạy 1 node.

# What are nodes and cliens?

`Node` dùng để chỉ 1 phần của phần mềm được gọi là client. 1 client là 1 triển khai của Ethereum mà xác minh tất cả các transaction trong mỗi block, giữ cho mạng an toàn và dữ liệu chính xác.

Nhiều triển khai của client Ethereum tồn tại bằng nhiều ngôn ngữ khác nhau. Điểm chung của các triển khai ứng dụng client này là chúng đều tuân theo một đặc điểm kỹ thuật chính thức. Đặc điểm kỹ thuật này quy định cách thức hoạt động của mạng Ethereum và Blockchain.

![diagram-ethereum](./images/client-diagram.png)

Sơ đồ đơn giản về những tính năng của máy khách Ethereum.

# Node Types

Nếu bạn muốn chạy node của bạn, bạn nên hiểu rằng có nhiều node khách nhau sử dụng dữ liệu khác nhau. Trong thực tế, khách hàng có thể chạy 3 kiểu node khác nhau - nhẹ, đầy đủ, và lưu trữ. Ngoài ra còn có nhiều lựa chọn đồng bộ khác nhau cho phép thời gian đồng bộ nhanh hơn. 

# Full node

    - Lưu trữ dữ liệu blockchain đầy đủ.
    - Tham gia xác thực Block, Xác minh tất cả Block và trạng thái.
    - Tất cả trạng thái có thể bắt nguồn từ 1 node đầy đủ.
    - Phục vụ network và cung cấp dữ liệu khi có yêu cầu.

# Light node

    - Lưu trữ tiêu đề chain và yêu cầu mọi thứ khác.
    - Có thể xác minh tính hợp lệ của dữ liệu trạng thái gốc tronng tiêu đề Block.
    - Có ích cho các thiết bị công suất thấp, cũng như thiết bị nhúng hoặc điện thoại di động, không có khả năng lưu trữ hàng gigabyte dữ liệu Blockchain.

# Archive node

    - Lưu trữ mọi thứ được giữ trên fullnode, và xây dựng một lưu trữ của lịch sử trạng thái. Cần thiết nếu bạn muốn truy vấn điều gì đó như số dư tài khoản tại Blockchain.
    - Những dữ liệu này đại diện cho các đơn vị terabyte khiên các node lưu trữ kém hấp dẫn hơn đối với người dùng bình thường những có thể hữu ích cho các dịch vụ như blockchain explorers, nhà cung cấp wallet, và phân tích chain.

# Why should i run an Ethereum node?

Chạy 1 node cho phép bạn sử dụng Ethereum 1 cách tin cậy và riêng tư trong khi hỗ trợ hệ sinh thái.

# Benefits to you

Chạy node của riêng bạn cho phép bạn sử dụng Ethereum thực sự riêng tư, cách tự cung tự cấp và đáng tin cậy. Bạn không cần phải tin tưởng vào network bởi vì bạn có thể xác minh dữ liệu của bạn với khách hàng của bạn. "Don't trút, verify" (Đừng tin tuởng, hãy xác minh) 1 câu thần chú quan trọng của Blockchain.

    - Node của bạn tự xác minh tất cả các giao dịch và các khối chống lại các quy tắc đồng thuận. Điều này có nghĩa là bạn không phải dựa vào bất kỳ Node nào khác trong mạng hoặc hoàn toàn tin tưởng vào chúng.
    - Bạn sẽ không phải rò rỉ địa chỉ và số dư của mình cho các node ngẫu nhiên. Mọi thứ có thể được kiểm tra với khách hàng của riêng bạn.
    - Dapp của bạn có thể an toàn và riêng tư hơn nếu bạn sử dụng node của riêng mình. Metamask, MyEtherWallet và một số ví khác có thể dễ dàng trỏ đến node cục bộ của riêng bạn.

![nodes](./images/nodes.png)

# Network benefits

Một tập hợp các nút đa dạng rất quan trọng đối với sức khỏe, bảo mật và khả năng phục hồi hoạt động của Ethereum.

    - Họ cung cấp quyền truy cập vào dữ liệu blockchain cho các khách hàng nhẹ phụ thuộc vào nó. Trong mức sử dụng cao nhất, cần có đủ các nút đầy đủ để giúp các nút sáng đồng bộ. Các nút nhẹ không lưu trữ toàn bộ chuỗi khối, thay vào đó chúng xác minh dữ liệu thông qua gốc trạng thái trong tiêu đề khối. Họ có thể yêu cầu thêm thông tin từ các khối nếu họ cần.
    - Các nút đầy đủ thực thi các quy tắc đồng thuận bằng chứng công việc để họ không thể bị lừa khi chấp nhận các khối không tuân theo chúng. Điều này cung cấp thêm tính bảo mật trong mạng bởi vì nếu tất cả các nút đều là nút sáng, không thực hiện xác minh đầy đủ, các thợ đào có thể tấn công mạng và ví dụ: tạo ra các khối với phần thưởng cao hơn.

Nếu bạn chạy một nút đầy đủ, toàn bộ mạng Ethereum được hưởng lợi từ nó.
