---
layout: post
title:  "INTRODUCTION TO THE ETHEREUM STACK"
date:   2020-11-23 14:00
categories: erc20
---

# INTRODUCTION TO THE ETHEREUM STACK

Giống như bất kỳ stack software, `stack Ethereum` hoàn chỉnh sẽ khác nhau giữa các dự án tùy vào mục tiêu kinh doanh của bạn.

Tuy nhiên có những công nghệ cốt lõi của Ethereum giúp cung cấp 1 mô hình tinh thần cho các ứng dụng phần mềm tương tác với chain block Ethereum. hiểu các lớp của stack sẽ giúp bạn hiểu các cách khác nhau mà Ethereum có thể được tích hợp vào các dự án phần mềm.

# Level 1: Ethereum vitual machine

EVM là môi trường runtime cho smart contract trong Ethereum. Tất cả smart contracts và trạng thái thay đổi trên Ethereum Blockchain là thực hiện bởi transactions. EVM xử lý tất cả quá trình transaction trên mạng Ethereum.

Như với bất kỳ máy ảo nào, EVM tạo 1 level trừu tượng giữa thực thi code và thực thi máy (Ethereum node). Hiện tại EVM chạy trên hàng ngàn của node phân phối trên toàn thế giới.

# Level 2: Smart contracts

Smart contract là thực thi chương trình mà chạy trên Ethereum Blockchain.

Smart contracts được viết bằng các ngôn ngữ xác định biên dịch sang EVM bytecode.

Các smart contract không chỉ đóng vai trò như các thư viện mã nguồn mở, chúng còn là các dịch vụ API mở chạy 24/7 và không thể bị gỡ xuống. Smart contract cung cấp các chức năng công khai mà các ứng dụng (dapp) có thể tương tác mà không cần sự cho phép. Bất kỳ ứng dụng nào cũng có thể tích hợp với các hợp đồng thông minh đã triển khai để soạn thảo các chức năng. Bất kỳ ai cũng có thể triển khai các smart contract mới cho Ethereum để thêm chức năng tùy chỉnh nhằm đáp ứng như cầu ứng dụng của họ.

Là một nhà phát triển dapp, bạn chỉ cần viết các smart contract nếu bạn muốn thêm chức năng tùy chỉnh trên blockchain Ethereum. Bạn có thể thấy mình có thể đạt được hầu hết hoặc tất cả các nhu cầu của dự án chỉ bằng cách tích hợp với các smart contract.

# Level 3: Ethereum nodes

Để một ứng dụng tương tác với blockchain Ethereum (tức là đọc dữ liệu blockchain / hoặc gửi giao dịch đến network), nó phải kết nối đến một Ethereum node.

Các node Ethereum là máy tính chạy phần mềm - 1 máy khách Ethereum. Máy khách là một triển khai của Ethereum xác minh tất cả các giao dịch trọng mỗi block. giữ cho mạng an toàn và dữ liệu chính xác, Các node Ethereum là blockchain Ethereum. Họ lưu trữ chung trạng thái của blockchain Ethereum và đạt được sự đồng thuận về các giao dịch để thay đổi trạng thái blockchain.

Bằng cách kết nối application của bạn với node Ethereum (thông qua JSON RPC) Ứng dụng của bạn có khả năng đọc dữ liệu từ blockchain (cũng như số dư tài khoản người dùng) cung như broadcast transaction mới tới network (cũng như chuyển ETH giữa các tài khoản người dùng thực hiện function của smart contracts).

# Level 4: Ethereum client APIS

Nhiều thư viện tiện lơij (Xây dựng và duy trì bởi Ethereum cộng đồng mã nguồn mở) cho phép các ứng dụng người dùng cuối của bạn kết nối và giao tiếp với Ethereum blockchain.

# Level 5: End user application

Ở cấp cao nhất của stack là các ứng dụng giao diện người dùng. Đây là những ứng dụng tiêu chuẩn mà bạn thường xuyên sử dụng và xây dựng ngày nay: chủ yếu là ứng dụng web và ứng dụng di động.