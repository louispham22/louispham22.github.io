---
layout: post
title:  "TRANSACTIONS"
date:   2020-11-20 15:00
categories: erc20
---
# TRANSACTIONS

Transaction là cryptographically được ký từ các tài khoản. Một tài khoản sẽ khởi tạo 1 giao dịch để update trạng thái của mạng Ethereum. Giao dịch đơn giản nhất là chuyển ETH từ tài khoản này sang tài khoản khác.

# What is a transaction?

Một giao dịch Ethereum đề cập đến một hành động được thực hiện bở một tài khoản bên ngoài, nói cách khác một tài khoản do con người quản lý, không phải contract. 

Các giao dịch thay đổi trạng thái EVM, cần broadcast tới toàn bộ mạng. Bất kỳ node nào có thể broadcast 1 yêu cầu cho 1 transaction để thực hiện trên EVM. Sau khi điều này xảy ra, 1 miner sẽ thực hiện transaction và tuyên truyền sự thay đổi trạng thái kết quả cho phần còn lại của mạng.

Các transaction yêu cầu 1 khoản phí và phải được miner để trở thành hợp lệ. để làm cho điều này đơn giản hơn, chúng tôi sẽ bao gồm phí gas và khai thác ở những nơi khác.

Một transaction đã gửi bao gồm các thông tin sau:

- recipient - địa chỉ nhận (Nếu một tài khoản sở hữu bên ngoài, giao dịch sẽ chuyển giá trị. Nếu 1 tài khoản contract, giao dịch sẽ thực hiện code contract)

- signature - danh tính của người gửi. Điều này tạo ra sau khi private key của người gửi ký transaction và xác nhận người gửi đã cho phép giao dịch này.

- value - số tiền của ETH chuyển từ người gửi tới người nhận (trong Wei, 1 mệnh giá của ETH).

- data - Trường tùy chọn để bao gồm dữ liệu bất kỳ

- gasLimit - số tiền tối đa của đơn vị gas mà có thể được tiêu thụ bởi transaction. đơn vị của gas đại diện cho bước tính toán.

- gasPrice - phí người gửi trả cho mỗi đơn vị của gas

Gas là một tham chiếu đến tính toán cần thiết để thực hiện transaction bởi 1 miner. Người dùng phải trả phí cho việc tính toán này. gasLimit và gasPrice xác định tối đa phí transaction trả cho miner.

# On Gas

Như đề cập, transaction tốn gas để thực hiện. Các transaction đơn giản yêu cầu 21000 đơn vị của gas.

# Transaction Lifecycle

Một transaction được gửi đi các điều sau sẽ xảy ra:

1. Sau khi bạn gửi 1 transaction, cryptography tạo ra 1 transaction hash:
    0x97d99bc7729211111a21b12c933c949d4f31684f1d6954ff477d0477538ff017
2. Transaction sau đó được broadcast tới mạng và bao gồm trong 1 pool với nhiều giao dịch khác.
3. Một miner phải chọn transaction của bạn và bao gồm nó trong 1 block để xác minh giao dịch và xem nó là thành công.
    - Bạn có thể phải chờ đợi ở gian đoạn này nếu mạng bận or miner không thể theo kịp. Miner sẽ luôn luôn ưu tiên transaction với GASPRICE cao bởi vì họ có thể giữ các khoản phí.
4. Transaction của bạn cũng sẽ nhận được 1 số xác nhận block. Đây là số khối được tạo kể từ khi khối mà transaction của bạn được đưa vào. Con số này càng cao, càng chắc chắn rằng transaction đã được xử lý và công nhận bởi mạng.


