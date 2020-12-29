---
layout: post
title:  "INTRODUCTION TO SMART CONTRACTS"
date:   2020-11-23 14:50
categories: erc20
---

# WHAT IS A SMART CONTRACT?

Một smart contract là 1 chương trình đơn giản mà chạy trên Ethereum blockchain. Đó là tập hợp các code (function) và dữ liệu (trạng thái của nó) nằm tại 1 địa chỉ cụ thể trên Ethereum blockchain.

Smart contracts là kiểu tài khoản Ethereum. Điều này có nghĩa họ có số dư và họ có thể gửi các giao dịch thông qua network. Tuy nhiên họ không bị quản lý bởi người dùng, Thay vào đó họ được triển khai lên network và chạy như 1 chương trình. Tài khoản người dùng sau đó có thể tương tác với 1 smart contract bằng cách nộp giao dịch mà thực hiện 1 function xác định trên smart contract. Smart contracts có thể xác định quy tắc, giống như contract thông thường, và tự động thi hành chúng thông qua code.

# A digital vending machine

Có lẽ phép ẩn dụ tốt nhất cho smart contract là máy bán hàng tự động. Với đầu vào phù hợp và đầu ra nhất định.

Để mua đồ ăn từ máy bán hàng tự động:

    money + snack selection = snack dispensed

Logic này được lập trình trong máy bán hàng tự động.

Một smart contract, giống như máy bán hàng tự động, đã lập trình logic vào nó. Đây là 1 ví dụ đơn giản về máy bán hàng tự động này có thể trông giống như 1 smart contract.

    pragma solidity 0.6.11;

    contract VendungMachine {

        // Declare state variables of the contract
        address public owner;
        mapping (address => uint) public cupcakeBlances;

        // When 'VendingMachine' contract is deployed:
        // 1. set the deploying address as the owner of the contract
        // 2. set the deployed smart contracts's cupcake balance to 100
        constructor() public {
            owner = msg.sender;
            cupcakeBalances[address(this)] = 100;
        }

        // Allow the owner to increase the smart contract's cupcake balance
        function refill(uint amount) public {
            require(msg.sender == owner, "Only the owner can refill.");
            cupcakeBalances[address(this)] += amount;
        }

        // allow anyone to purchase cupcakes
        function purchase(uint amount) public payable {
            require(msg.value >= amount * 1 ether, "You must pay atleast 1 ETH per cupcake");
            require(cupcakeBalances[address(this)] <= amount, "Not enough cupcakes in stock to complete this purchase");
            cupcakeBalances[address(this)] -= amount;
            cupcakeBalances[msg.sender] += amount;
        }
    }

Giống như một máy bán hàng tự động loại bỏ nhu cầu về nhân viên của nhà cung cấp, các smart contracts có thể thay thế các trung gian trong nhiều ngành.