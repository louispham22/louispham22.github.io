---
layout: post
title:  "How to Create an ERC20 Token the Simple Way"
date:   2020-11-18 14:00
categories: erc20
---
# What is ERC20?
- Tiêu chuẩn ERC20 xác định một tập hợp các chức năng (function) được thực hiện bởi tất cả các token ERC20 để cho phép tích hợp với các contract khác, wallet hoặc marketplaces. Function này khá ngắn gọn và căn bản.

        function totalSupply() public view returns (uint256);
        function balanceOf(address tokenOwner) public view returns (uint);
        function allowance(address tokenOwner, address spender) public view returns (uint);
        function transfer(address to, uint tokens) public returns (bool);
        function approve(address spender, uint tokens) public returns (bool);
        function transferFrom(address from, address to, uint tokens) public returns (bool);

ERC20 function cho phép một người dùng bên ngoài, chẳng hạn như là crypto-wallet app, tìm số dư (balancer) của người dùng và chuyển tiền từ người dùng này sang người dùng khác với sự ủy quyền cho phép.

The smart contract (Hợp đồng thông minh) xác định 2 sự kiện được xác định cụ thể:

        event Approval(address indexed tokenOwner, address indexed spender, uint tokens);
        event Transfer(address indexed from, address indexed to, uint tokens);

Các event sẽ được invoked (gọi) hoặc emitted (phát ra) sau khi người dùng được cấp quyền rút (withdraw) tokens từ một tài khoản, và sau đó tokens thực sự được chuyển.

Ngoài các ERC20 function tiêu chuẩn, nhiều tokens thông báo ERC20 cũng có các trường bổ sung và một số đã trở thành một phần thực tế của tiêu chuẩn ERC20, nếu không phải bằng văn bản thì trên thực tế. Dưới đây là một vài ví dụ về các trường như vậy.

        string public constant name;
        string public constant symbol;
        uint8 public constant decimals;

Đây là 1 số điểm liên quan tới ERC20 và Solidity:
- Một `public` function có thể truy cập bên ngoài contract của nó
- `view` trạng thái bên trong của hợp đồng sẽ không bị thay đổi bởi function
- Một `event` là cách của Solidity cho phép khách hàng. 

# Writing an ERC20 token in Solidity
![ERC20 token](https://uploads.toptal.io/blog/image/127335/toptal-blog-image-1539181714183-62a47883ea777f12969345038389fb22.png)

Bây giờ chúng ta đã phác thảo những điều cơ bản và giải thích những gì cần thiết để tạo token ERC20
Đầu tiên, chúng ta cần xác định 2 đối tượng mapping. Đây là khái niệm Solidity cho một liên kết hoặc mảng key/value:

        mapping(address => uint256) balances;
        mapping(address => mapping (address => uint256)) allowed;

Cách diễn đạt mapping(address => uint256) xác định 1 mảng kết hợp với key là kiểu `address` 1 só sử dụng để biểu diễn tài khoản. và giá trị của ai thuộc kiểu `uint256` số nguyên 256 bit thường được sử dụng để lưu trữ số dư token.

Đối tượng mapping đầu tiên, `balances` sẽ giữ số dư token của mỗi tài khoản.

Đối tượng mapping thứ hai, sẽ bao gồm tất cả tài khoản được approve rút tiền từ một tài khoản nhất định cùng với số tiền rút được phép cho mỗi tài khoản.

Như bạn có thể thấy, trường giá trị (value) của mapping được phép tự nó là một địa chỉ tài khoản lập bản đồ với số tiền rút được chấp thuận của nó.

Các mapping cùng nhau với tất cả trường contract khác sẽ lưu trữ trong blockchain và sẽ được khai thác (mined) dẫn đến các thay đổi được truyền tới tất cả các nodes.

Lưu trữ Blockchain là tốn kém và người dùng contract sẽ cần phải trả tiền, bằng cách này hay cách khác. Do đó bạn luôn cố gắng giảm thiểu kích thước lưu trữ và viết vào trong blockchain.

Bây giờ chúng ta đã có cấu trúc (data structures) dữ liệu cần thiết, Chúng ta có thể bắt đầu viết ERC20 logic vào các function thích hợp.

# Setting the number of ICO tokens

Làm cách nào để chúng tôi set số lượng của ICO tokens? 
Có một số cách để cài đặt tối đa số lượng ICO tokens

Đối với nhu cầu của hướng dẫn ERC20, chúng tôi sẽ sử dụng cách tiếp cận đơn giản nhất. Set tổng số tiền của tokens tại thời điểm tạo contract và ban đầu chỉ định tất cả chúng cho "contract owner". Tài khoản đã triển khai smart contract:

        uint256 totalSupply_;
        constructor(uint256 total) public {
                totalSupply_ = total;
                balances[msg.sender] = _totalSupply;
        }

Một constructor là một function đặc biệt được Ethereum tự động gọi ngay sau khi contract được triển khai. Nó thường được sử dụng để khởi tạo tokens trạng thái sử dụng các tham số được truyền vào bởi tài khoản triển khai của contract.

`msg` là biến toàn cục được khai báo và được phổ biến bởi chính Ethereum. Nó chứa data quan trọng để thực hiện contract. Trường chúng tôi đang sử dụng ở đây là `msg.sender` chứa tài khoản đang thực hiện function contract hiện tại.

Chỉ tài khoản triển khai mới có thể nhập hàm tạo của contract. Sau khi contract được khởi động, function này sẽ phân bổ các tokens vào tài khoản chủ sở hữu contract (cotract owner).

# Get total token supply

        function totalSupply() public view returns (uint256) {
                return totalSupply_;
        }

Function này sẽ trả về số lượng của tất cả tokens phân bổ bởi contract này bất kể chủ sở hữu (regardless of owner).

# Get token balance of owner

        function balanceOf(address tokenOwner) public view returns (uint) {
                return balances[tokenOwner];
        }

`balanceOf` sẽ trả về số lượng tokens hiện tại của tài khoản, được xác định bởi địa chỉ của chủ sở hữu. (identified by its owner's address)

# Transfer tokens to Another Account

        function transfer(address receiver, uint numTokens) public returns (bool) {
                require(numTokens <= balances[msg.sender]);
                balances[msg.sender] = balances[msg.sender] - numTokens;
                balances[receiver] = baances[receiver] + numTokens;
                emit Transfer(msg.sender, receiver, numTokens);
                return true;
        }

Đúng như tên gọi, `transfer` function được sử dụng để di chuyển `numTokens` số tiền của tokens từ số dư của chủ sở hữu tới người dùng khác or `receiver`. Chủ sở hữu chuyển nhượng là `msg.sender`

Cách của Solidity khẳng định một thuộc tính là `require`. Trong trường hợp này là tài khoản chuyển có đủ số dư để thực hiện chuyển khoản. Nếu 1 câu lệnh `require` không thành công, thì (transaction) giao dịch ngay lập tức rolled back với không có thay đổi nào được ghi vào blockchain.

Ngay trước khi thoát, function kích hoạt ERC20 event `Transfer` cho phép người nghe đã đăng ký phản ứng với sự hoàn thành của nó.

# Approve Delegate to withdraw tokens

Function này thường được sử dụng nhất trong một kịch bản thị trường tokens.

        function approve(address delegate, uint numTokens) public returns (bool) {
                allowed[msg.sender][delegate] = numTokens;
                emit Approval(msg.sender, delegate, numTokens);
                return true;
        }

Việc `approve` cho phép một chủ sở hữu. `msg.sender` để phê duyệt tài khoản ủy quyền - có thể là chính thị trường. Để rút tokens từ tài khoản của mình và chuyển chúng sang các tài khoản khác.

Như các bạn thấy, Function này sử dụng cho kịch bản mà chủ sở hữu đang cung cấp tokens trên thị trường. Nó cho phép thị trường hoàn tất giao dịch mà không cần chờ phê duyệt trước.

Khi kết thúc quá trình thực thi, chức năng này kích hoạt `Approval` event.

# Get Number of tokens Approved for withdrawal

        function allowance(address owner, address delegate) public view returns (uint) {
                return allowed[owner][delegate];
        }

Function này trả về số lượng tokens được approve hiện tại bởi một chủ sở hữu cho một đại biểu cụ thể, như thiết lập trong `approve` function.

# Transfer Tokens by Delegate

`transferFrom` function là peer (ngang hàng) của `approve` function, mà chúng ta đã thảo luận trước đây. Nó cho phép 1 người được ủy quyền cho phép rút tiền để chuyển tiền của chủ sở hữu sang tài khoản của bên thứ ba.

        function transferFrom(address owner, address buyer, uint numTokens) public returns (bool) {
                require(numTokens <= balances[owner]);
                require(numTokens <= allowed[owner][msg.sender]);
                balances[owner] = balances[owner] - numTokens;
                allowed[owner][msg.sender] = allowed[from][msg.sender] - numTokens;
                balances[buyer] = balances[buyer] + numTokens;
                Transfer(owner, buyer, numTokens);
                return true;
        }

Hai `require` câu lệnh lúc bắt đầu function là để xác minh rằng giao dịch là hợp pháp. Rằng chủ sở hưu có đủ token để chuyển và người được ủy quyền đã chấp thuận `numTokens` để rút.

Ngoài việc chuyển `numTokens` số tiền từ chủ sở hữu tới người mua. Function này cũng trừ đi (subtracts) `numTokens` từ phụ cấp của người được ủy quyền. Về cơ bản điều này cho phép ủy quyền với 1 khoản phụ cấp nhất định để chia thành nhiều lần rút riêng biệt. đó là hành vi thị trường điển hình.

# safeMath Solidity Library

SafeMath là thư viện Solidity nhằm đối phó với hacker đã biết phá contract. Tấn công tràn số nguyên. Trong cuộc tấn công như vậy, hacker bắt contract sử dụng số không chính xác bằng cách truyền các tham số sẽ đưa các số nguyên có liên quan vượt qua giá trị lớn nhất của chúng.

![safemath](https://uploads.toptal.io/blog/image/127336/toptal-blog-image-1539181732450-e81e93f6028bd7db90c30d5a1814195d.png)

SafeMath bảo vệ chống lại điều này bằng cách kiểm tra tràn trước khi thực hiện hành động số học, do đó loại bỏ nguy cơ tấn công tràn. Thư viện quá nhỏ nên tác động đến quy mô hợp đồng là tối thiểu, không phát sinh hiệu suất và ít bị phạt chi phí lưu trữ.

Bắt đầu thêm `SafeMath` vào code:

        library SafeMath {
                function sub(uint256 a, uint256 b) internal pure returns (uint256) {
                        assert (b <= a);
                        return a - b;
                }

                function add(uint256 a, uint256 b) internal pure returns (uint256) {
                        uint256 c = a + b;
                        assert(c >= a);
                        return c;
                }
        }

SafeMath sử dụng câu lệnh `assert` để xác thực tính đúng đắn của các tham số được truyền vào. Nên `assert` thất bại, function sẽ ngay lập tức dừng lại và các thay đổi blockchain sẽ được quay trở lại.

Tiếp theo chúng ta hãy thêm câu lệnh sau và trình biên dịch Solidity:

        using SafeMath for uint256;


Sau đó, chúng tôi thay thế số học đúng mà chúng tôi sử dụng lúc đầu:

        balances[msg.sender] = balances[msg.sender].sub(numTokens);
        balances[receiver] = balances[receiver].add(numTokens);
        balances[buyer] = balances[buyer].add(numTokens);
        balances[owner] = balances[owner].sub(numTokens);

Trong Solidity, một smart contract function và events là được bao bọc bởi 1 thực thể gọi là `contract` mà bạn có thể dịch nhầm là `blockchain class`. Dưới đây là ERC20 tương thích với contract chúng tôi đã tạo. Trường tên và ký hiệu có thể thay đổi. Hầu hết các tokens đều giữ giá trị thập phân là 18.

Full Source Code:

                pragma solidity ^0.4.19;

                contract ERC20Basic {

                        string public constant name = "ERC20Basic";
                        string public constant symbol = "BSC";
                        uint8 public constant decimals = 18;  


                        event Approval(address indexed tokenOwner, address indexed spender, uint tokens);
                        event Transfer(address indexed from, address indexed to, uint tokens);


                        mapping(address => uint256) balances;

                        mapping(address => mapping (address => uint256)) allowed;
                        
                        uint256 totalSupply_;

                        using SafeMath for uint256;


                        constructor(uint256 total) public {  
                                totalSupply_ = total;
                                balances[msg.sender] = totalSupply_;
                        }  

                        function totalSupply() public view returns (uint256) {
                                return totalSupply_;
                        }
                        
                        function balanceOf(address tokenOwner) public view returns (uint) {
                                return balances[tokenOwner];
                        }

                        function transfer(address receiver, uint numTokens) public returns (bool) {
                                require(numTokens <= balances[msg.sender]);
                                balances[msg.sender] = balances[msg.sender].sub(numTokens);
                                balances[receiver] = balances[receiver].add(numTokens);
                                emit Transfer(msg.sender, receiver, numTokens);
                                return true;
                        }

                        function approve(address delegate, uint numTokens) public returns (bool) {
                                allowed[msg.sender][delegate] = numTokens;
                                Approval(msg.sender, delegate, numTokens);
                                return true;
                        }

                        function allowance(address owner, address delegate) public view returns (uint) {
                                return allowed[owner][delegate];
                        }

                        function transferFrom(address owner, address buyer, uint numTokens) public returns (bool) {
                                require(numTokens <= balances[owner]);    
                                require(numTokens <= allowed[owner][msg.sender]);
                        
                                balances[owner] = balances[owner].sub(numTokens);
                                allowed[owner][msg.sender] = allowed[owner][msg.sender].sub(numTokens);
                                balances[buyer] = balances[buyer].add(numTokens);
                                Transfer(owner, buyer, numTokens);
                                return true;
                        }
                        }

                library SafeMath { 
                function sub(uint256 a, uint256 b) internal pure returns (uint256) {
                assert(b <= a);
                return a - b;
                }
                
                function add(uint256 a, uint256 b) internal pure returns (uint256) {
                uint256 c = a + b;
                assert(c >= a);
                return c;
                }
                }

[Link tham khảo](https://www.toptal.com/ethereum/create-erc20-token-tutorial)