---
layout: post
title:  "ETHEREUM ACCOUNTS"
date:   2020-11-20 13:00
categories: erc20
---

# ETHEREUM ACCOUNTS

Một tài khoản Ethereum là 1 thực thể với số dư ether(ETH) mà có thể gửi transactions trên Ethereum. Tài khoản có thể được kiểm soát bởi người dùng hoặc triển khai dưới dạng smart contracts.

# Type of account

Ethereum có 2 kiểu của account:
- Externally-owned – controlled by anyone with the private keys (Thuộc sở hữu bên ngoài - được kiểm soát bởi bất kỳ ai có private keys)
- Contract - 1 smart contract triển khai vào mạng, được kiểm soát bởi code

Cả 2 kiểu account có khả năng:
- Nhận, giữ, gửi ETH và tokens
- Tương tác với smart contract đã được triển khai

# Key differences

**Externally-owner (Thuộc sở hữu bên ngoài)**

- Tạo tài khoản không tốn phí
- Có thể khởi tạo giao dịch
- Giao dịch giữa Externally-owner account chỉ có thể chuyển ETH

**Contract**

- Việc tạo tài khoản có phí bởi vì bạn sử dụng network storage
- Chỉ có thể gửi được giao dịch khi nhận được 1 giao dịch
- Các giao dịch từ bên ngoài và trong tài khoản contract có thể kích hoạt code, có thể thực hiện nhiều hành động khác nhau, chẳng hạn như chuyển tokens or tạo contract mới.

# An Account Examined

**Ethereum account có 4 trường**

- nonce - một bộ đếm cho biết số lượng giao dịch được gửi từ tài khoản. Điều này đảm bảo các giao dịch chỉ được xử lý 1 lần. Nếu 1 tài khoản contract, con số này đai diện cho contract được tạo bởi tài khoản.

- balnace - Số lượng Wei thuộc sở hữu của địa chỉ này. Wei là mệnh giá của ETH và có 1e+18 = 1ETH

- CodeHash - Tất cả các đoạn code như vậy được chứa trong cơ sở dữ liệu dưới các hàm băm tương ứng của chúng để truy xuất sau này. Đối với tài khoản contract, đây là code được băm và được lưu trữ dưới dạng codeHash. Đối với tài khoản thuộc sở hữu bên ngoài, trường codeHash là hash của chuỗi trống.

- storageRoot - một hash 256 bit của node gốc của Merkle Patricia mã hóa lưu trữ nội dung của account.

# Externally-owner accounts and key pairs

Một tài khoản được tạo thành từ cặp khóa `public và private`. Chúng giúp chứng minh rằng một giao dịch đã thực sự được ký bởi người gửi và ngăn chặn việc giả mạo. Private keys của bạn dùng để ký các giao dịch, vì vậy nó cấp cho bạn quyền giám sát đối với các khoản tiền được liên kết với tài khoản của bạn. Thực sự bạn không bao giờ giữ tiền điện tử, bạn giữ private keys - Tiền luôn nằm trên sổ cái (ledger) Ethereum.

Điều này ngăn chặn các kẻ xấu phát đi các giao dịch giả mạo vì bạn luôn có thể xác minh người gửi giao dịch.

# Account Creation

Sau khi bạn muốn tạo 1 tài khoản hầu hết các thư viện sẽ tạo ra ngẫu nhiên 1 private key.

Một private key được tạo thành từ 64 ký tự hex và có thể mã hóa với 1 password.

Example:

fffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd036415f

# Contract Accounts

Tài khoản Contract cũng có 42 địa chỉ ký tự hexadecimal:

Example:

0x06012c8cf97bead5deae237070f9587f8e7a266d

Địa chỉ contract thường được cung cấp khi một contract được triển khai vào Ethereum Blockchain.

# A Note on wallets

Tài khoản không phải là ví (wallet). Một ví là keypair liên kết với một tài khoản do người dùng sở hữu, cho phép người dùng thực hiện các giao dịch hoặc quản lý tài khoản.