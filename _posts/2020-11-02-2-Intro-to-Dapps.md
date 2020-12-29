---
layout: post
title:  "INTRODUCTION TO DAPPS"
date:   2020-11-20 12:00
categories: erc20
---

Một ứng dụng phi tập trung (dapp) là một ứng dụng được xây dựng trên một mạng phi tập trung kết hợp 1 smart contract và 1 giao diện người dùng. Lưu ý, Trong Ethereum smart contracts là có thể truy cập và minh bạch - giống như APIs mở - vậy dapp của bạn có thể  ba gồm 1 smart contract mà người khác đã viết.

# Definition of a Dapp

Một dapp có backend code chạy trên 1 mạng peer-to-peer phi tập trung. 
Một dapp có thể có frontend và giao diện người dùng được viết với bất kỳ ngôn ngữ nào (giống như 1 app) có thể call đến backend. 

- Decentralized: khiến chúng trở nên độc lập và không ai kiểm soát chúng.
- Deterministic: Chúng thực hiện cùng function không phụ thuộc vào môi trường chúng thực thi.
- Turing compatible: có nghĩa là được cung cấp tài nguyên cần thiết, dapp có thể thực hiện bất kỳ hành động nào.
- Isolated: Có nghĩa là chúng thực hiện trong môi trường ảo là EVM, vì vậy nếu smart contract xảy ra bug, ít không ảnh hưởng tới hoạt động của mạng blockchain.

# On smart contracts

1 smart contract là code chạy trên Ethereum blockchain và chạy chính xác như được lập trình. Sau khi chúng được triển khai trên mạng thì bạn không thể thay đổi chúng.
Dapp có thể được phân quyền bởi vì chúng được kiểm soát bởi logic viết trong smart constract, không phải cá nhân hay công ty. Điều này cũng có nghĩa là bạn phải thiết kế contract của bạn cẩn thận và test chúng kỹ lưỡng.