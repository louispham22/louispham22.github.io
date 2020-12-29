---
layout: post
title:  "ANATOMY OF SMART CONTRACTS"
date:   2020-11-26 13:50
categories: erc20
---

# ANATOMY OF SMART CONTRACTS

Một smart contract là 1 chương trình chạy tại một địa chỉ trên Ethereum. Chúng tạo thành từ dữ liệu và function mà có thể thực hiện khi nhận được 1 giao dịch.

# DATA

Bất kỳ dữ liệu contract phải được gắn vào 1 vị trí. Hoặc `storage` hoặc là `memory`. Việc sửa đổi storage trong smart contract là rất tốn kém, vì vậy bạn cần phải xem xét dữ liệu của mình sẽ ở đâu.

# STORAGE

Persistent data là được gọi là strage và được biểu diễn bởi state variables. Các giá trị này được lưu trữ vĩnh viễn trên blockchain. Bận cần khai báo kiểu để smart contract có thể theo dõi dung lượng lưu trữ trên blockchain nó cần khi nó compiles.

Một addresstype có thể chứa một địa chỉ Ethereum tương đương với 20 byte hoặc 160 bit. Nó trả về ở dạng ký hiệu thập lục phân với số 0x ở đầu.

# Memory

Các giá trị chỉ được lưu trữ trong suốt thời gian thực thi của một hàm contract được gọi là các biến bộ nhớ, Vì chúng không được lưu trữ vĩnh viễn trên blockchain nên chúng rẻ hơn nhiều khi sử dụng.

# Environment variables

Ngoài các biến bạn xác định trên contract của bạn. Có 1 số biến xác định toàn cục. Chúng chủ yếu được sử dụng để cung cấp thông tin về blockchain hoặc giao dịch hiện tại.

    - block.timestamp   uint256
    - msg.sender        address

# Function

Nói một cách đơn giản nhất, các hàm có thể lấy thông tin hoặc thiết lập thông tin để đáp ứng với các giao dịch đến.

Có 2 kiểu function:
- internal: những kiểu này không tạo 1 EVM call
    - Các hàm tổng hợp và các biến trạng thái chỉ có thể được truy cập nội bộ (tức là từ bên trong hợp đồng hiện tại hoặc các hợp đồng bắt nguồn từ nó)

- external: Những kiểu này tạo ra 1 EVM call
    - Các chức năng bên ngoài là một phần của giao diện hợp đồng, có nghĩa là chúng có thể được gọi từ các hợp đồng khác và thông qua các giao dịch. Một hàm bên ngoài f không thể được gọi trong nội bộ (tức là f() không hoạt động, nhưng hàm this.f () hoạt động).

Chúng cũng có thể là `public` hoặc `private`

    - public: function có thể gọi nội bộ từ bên trong hoặc bên ngoài contract thông qua tin nhắn.
    - private: function chỉ hiển thị với contract xác định