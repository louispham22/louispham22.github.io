---
layout: post
title:  "Sự tích DevOps"
date:   2019-02-21 18:30
categories: story devops
permalink: /archivers/su-tich-devops
---

**Sự tích DevOps tập 2**

![](https://user-images.githubusercontent.com/10813839/53164391-ac4be400-3602-11e9-8b82-319c22210fc9.png)

Từ ngày gặp Bụt bên bờ suối, người em IT Operation về nhà ngày đêm nghiền ngẫm về DevOps, học thêm về Linux Ubuntu, SysAdmin, tập code ShellScript, Python, không quản ngại khó khan gian khổ, thức thâu đêm suốt sáng để luyện rèn. Chả mấy chốc, trình độ tăng tiến rõ rệt, việc deploy application nhanh hơn trc rất nhiều, lại ít gặp issue, khiến nàng User vô cùng sung sướng, nhiều lần cho chàng được “thị tẩm”, phê như con tê tê.

![](https://user-images.githubusercontent.com/10813839/53164508-e9b07180-3602-11e9-9a2d-ff5786d66e79.png)

Trái lại, người anh Developer thì lại tỏ ra chểnh mảng, không quan tâm đến DevOps, chỉ tối ngành lêu lổng chơi bời, không chịu rèn luyện, khiến application code xong mà bug hàng tấn, cho nên mặc dù deploy lên server bình thường nhưng chất lượng app vẫn rất kém, nàng User rất bực tức, nhiều lần “cấm vận” khiến chàng bị bỏ đói.
Lâu ngày, người anh sinh ra đố kị, căm ghét người em. Rồi một hôm đang ngồi xem phim Diên Hy Công Lược, thấy Nhàn Phi dùng kế hãm hại Phú Sát Hoàng Hậu, người anh đã nghĩ ra một kết hay….
Từ hôm đó, người anh trở nên rất chịu khó viết code, rồi nỉ non với người em
An ơi, anh code xong rồi deploy cho anh đi, để tối nay nàng user còn dùng
OK, man. Chờ chút.
Người anh lọ mọ mở terminal ssh vào server, run command build, chạy test check kết quả rồi deploy app. Ngày ngày cứ theo process như vậy
Điều lạ là người anh make Pull Request yêu cầu merge code và deploy app liên tục. Trước đây, tuần độ 2 3 lần, giờ đây 1 ngày đến 3, 4 lần. Khiến chàng IT operation làm việc không xuể, nhiều lần ko keep dc deadline, làm cho nàng User rất đau lòng, ko còn sướng như trước. 
Chàng buồn lắm, lại ôm laptop ra bờ suối ngồi khóc, đợi bụt xuất hiện giải cứu, nhưng khóc hết cả chậu nước mắt mà chẳng thấy ai, mệt mỏi chàng thiếp đi…
Trời bỗng nổi 1 cơn gió, trong làn khói sương mờ ảo, một bóng người con gái hiện ra

![](https://user-images.githubusercontent.com/10813839/53164582-1ebcc400-3603-11e9-9180-188ca7acb88c.png)

Ta là Ngụy Anh Lạc bà nội 10 đời của ngươi, thật ra thằng Dev nó cố ý tạo request nhiều lần để cho ngươi không kham nổi công việc deploy thôi, chứ nó ko có code thêm features gì đâu, chỉ toàn sửa comment với change tên biến. Vì nó biết ngươi deploy app manual tốn effort, nên mới làm thế để bẫy ngươi. Muốn thoát khỏi cảnh tay chân, phải xây dựng hệ thống CICD tự động build, test deploy app mỗi khi có source code commit mới là chuẩn men. Cái này gọi là Continuous Integration (CI) tích hợp liên tục mục đích để

Giảm thiểu effort manual lặp đi lặp lại (Build, Test, Deploy)
Hạn chế sai sót của con người
Tạo phần mềm có giá trị sử dụng sớm nhất có thể và sẵn sàng triểnkhai mọi lúc mọi nơi.
Phát hiện issue nhanh chóng

Tóm lại mô hình tích hợp liên tục nó như thế này này

![](https://user-images.githubusercontent.com/10813839/53164617-309e6700-3603-11e9-9091-3bbfd541c5ac.png)

Giờ nếu như thằng Dev nó commit code lên repository như GitHub hoặc make Pull Request, hệ thống CI sẽ tự động detect new source và pull source về để thực hiện build, chạy test (Unit Test, Smoke Test), ngoài ra còn có thể tích hợp 1 số công cụ review code như Coverity hoặc Sonar nữa để generate kết quả review code trước khi chạy test. Nếu như kết quả Test Pass, quá trình deploy sẽ đc trigger và app sẽ được deploy lên server trên các môi trường khác nhau (QA, DEV, Staging và Production environment). Server có thể là on premise hoặc cloud (AWS, GCE). Ngược lại có lỗi thì không deploy, notify lại cho developer qua mail hoặc kênh chat như Slack…
Quá trình CI này được thực hiện bởi các pipeline job. Thực chất là 1 cấu hình build cho 1 ứng dụng. Vòng đời quản lý của 1 ứng dụng có thể có 1 hoặc nhiều job/item, được viết dưới dạng script (Groovy Script hoặc Shell). Các script này sẽ thực hiện các tác vụ tự động như run command build, execute tests script, output kết quả ra console.
Tóm lại thay vì anh DevOps deploy app manual thì sẽ automated nó bằng scripting, vừa đơn giản gọn nhẹ lại ít sai sót.
Tool để làm CI rất nhiều, chẳng hạn như

Source Code version control có Git, SVN, Visual Source Safe, tốt nhất là dùng Git
CI system có Jenkins, Bamboo...Ta khuyến khích ngươi dùng Jenkins nhé, hàng tốt đấy
Testing framework có Junit, CPP, ưu tiên automation framework như Selenium…
Chàng trai thấy lạ liền hỏi 
Thế Jenkins nó hoạt động thế nào ạ, làm sao code được job trên Jenkins??
Ngụy Anh Lạc bực mình nói:
Cái đấy bữa sau bà hiện hồn về rồi chỉ cho cách setup và viết pipeline script trên Jenkins, bây giờ đến lúc ta phải thị tẩm với hoàng thượng rồi
Nói xong, bà tát vô mặt chàng IT bốp 1 cái rồi biến mất, chàng giật mình tỉnh dậy hóa ra là giấc mơ.Chàng IT nhớ lại câu chuyện thầm nhủ
“Thằng Dev nó lừa ta, hãy đợi đấy…”
(Còn tiếp)