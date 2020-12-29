---
layout: post
title:  "INTRO TO ETHEREUM"
date:   2020-11-20 10:00
categories: erc20
---
# What is Blockchain?

Một `Blockchain` được mô tả là một cơ sở dữ liệu công khai đươc update và share qua nhiều máy tính trên một network.

`Block` thực tế là dữ liệu và trạng thái được lưu trữ tuần tự or `block`. Nếu bạn gửi ETH cho ai đó, giao dịch dữ liệu cần thêm vào một block để nó successful.

`Chain` thực tế là mỗi block tham chiếu đến cha mẹ nó. Một dữ liệu của block không thể thay đổi nếu không thay đổi các khối tiếp theo, yêu cầu sự đồng thuận của toàn bộ mạng.

Ethereum hiện tại đang sử dụng cơ chế đồng thuận `proof-of-work`. Điều này có nghĩa là bất kỳ ai muốn thêm block mới vào `chain` phải giải câu đố khó mà bạn cần nhiều khả năng tính toán để giải quyết. Việc giải câu đố  chứng tỏ rằng bạn đã sử dụng tài nguyên tính toán. Điều này được gọi là `mining`. Mining có thể thử hoặc sai nhưng thêm 1 block mới thành công sẽ được thưởng (reward) Eth. 

Block mới sẽ được (broadcast) phát tới các nodes trong network, kiểm tra và xác minh, update trạng thái cho tất cả các nodes.

Tóm lại, khi bạn gửi ETH cho ai đó, giao dịch (transaction) phải được khai thác và đưa vào block mới. Update trạng thái sau đó chia sẻ với toàn bộ mạng.

# What is Ethereum?

Trong thế giới Ethereum, có một máy tính chuẩn gọi là (Ethereum Virtual Machine, or EVM). trạng thái mà mọi người trên mạng Ethereum đồng ý. Tất cả những người tham gia vào mạng Ethereum (every Ethereum node) giữ 1 bản sao (copy) trạng thái của máy tính này. Ngoài ra, bất kỳ người tham gia có thể (broadcast) gửi 1 yêu cầu cho máy tính này để thực hiện tính toán tùy ý. Bất cứ khi nào yêu cầu như vậy được phát đi, người tham gia khác trên mạng xác minh, xác thực và thực hiện tính toán. Điều này gây ra một thay đổi trạng thái trong EVM, được cam kết và tuyên truyền trên toàn mạng.

Các yêu cầu tính toán được gọi là các yêu cầu giao dịch (transaction). bản ghi của tất cả các giao dịch cũng như trạng thái hiện tại của EVM được lưu trữ trong blockchain, đến lượt nó được lưu trữ và đồng ý của tất cả các nodes.

Cơ chế mật mã đảm bảo rằng một transactions được xác minh là hợp lệ và thêm vào block, chúng không thể bị giả mạo sau này. Các cơ chế giống nhau cũng đảm bảo rằng tất cả các transactions là được ký và thực hiện với quyền thích hợp.

# What is Ether?

Mục đích của Ether, tiền điện tử, là cho phép sự tồn tại của thị trường tính toán. Cũng như thị trường cung cấp một khích lệ kinh tế cho những người tham gia xác minh/ thực hiện yêu cầu transactions và cung cấp tài nguyên tính toán vào mạng.

Bất cứ người tham gia phát đi 1 yêu cầu transaction cũng phải cung cấp một số lượng Ether cho mạng. Như một khoản tiền thưởng được trao cho ai cuối cùng thực hiện công việc xác minh giao dịch, thực hiện nó, cam kết nó với blockchain, và phát nó cho toàn network.

Số tiền Ether được trả là 1 function độ dài của phép tính. Điều này cũng ngăn chặn những người cố tình làm tắc nghẽn mạng bằng cách yêu cầu thực hiện các vòng lặp vô hạn hoặc các tập lệnh sử dụng nhiều tài nguyên, vì các tác nhân này sẽ liên tục bị tính phí.

# What is Dapps?

Trong thực tế, người tham gia không viết code mới mỗi khi họ muốn yêu cầu tính toán trên EVM. Đúng hơn, các nhà phát triển ứng dụng tải lên các chương trình (các đoạn mã có thể sử dụng) lưu trữ trong EVM, và sau đó người dùng đưa ra yêu cầu để thực hiện các đoạn mã này với các tham số khác nhau. Chúng tôi gọi các chương trình upload lên và thực hiện bởi mạng smart contracts.

Ở cấp độ cơ bản, bạn có thể nghĩ 1 smart contract giống như 1 máy bán hàng tự động. Một tập lệnh, sau khi gọi với các thông số nhất định, thực hiện 1 số hành động or tính toán nếu một số điều kiện được thỏa mãn. Ví dụ: một hợp đồng thông minh đơn giản của nhà cung cấp có thể tạo và chỉ định quyền sở hữu tài sản kỹ thuật số nếu người gọi gửi ether cho một người nhận cụ thể.

Bất kỳ developer nào cũng có thể tạo 1 smart contract và đưa nó lên mạng public, sử dụng Blockchain làm lớp dữ liệu của nó, với một khoản phí trả cho mạng. Bất kỳ người dùng nào cũng có thể  gọi smart contract để thực hiện đoạn mã đó, và phải trả 1 khoản phí cho mạng.

Do đó, với smart contracts, developers có thể build và deploy các ứng dụng và dịch vụ phức tạp tùy ý dành cho người dùng (thị trường, tài chính, games, vv..)

# Terminology (Thuật ngữ)

- Blockchain
- ETH
- EVM
- Nodes
- Accounts
- Transactions
- Block
- Smart contracts
