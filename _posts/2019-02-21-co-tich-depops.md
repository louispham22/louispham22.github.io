---
layout: post
title:  "Sự tích DevOps"
date:   2019-02-21 16:30
categories: story devops
permalink: /archivers/su-tich-devops-tap-1
---

**Sự tích DevOps tập 1**

Ngày xửa ngày xưa, ở thung lũng độn silicon valley, có 2 anh em cùng cha khác bố. Người anh tên là Developer, làm ngồi coding. Người em tên là IT Operation, làm nghề quản trị hệ thống CNTT. Cả 2 anh em đều phục vụ 1 cô bé tên là QA.
Nàng QA đẹp lắm, tóc nàng dài như dòng suối mơ, tóc đen như gỗ mun, da trắng như bạch tuyết. Hàng ngày, nàng sử dụng những application do anh Developer tạo ra, được deploy và vận hành bởi chàng IT operation.
Người code, người deploy, người sử dụng. Cuộc sống diễn ra thật êm đềm như nước hồ thu….

![](https://www.guru99.com/images/2-2017/092917_0812_DevOpsTrain1.png)

Thế rồi thời gian trôi nhanh như chó chạy ngoài đồng. nàng QA từ cô bé thơ ngây ngày nào đã trở thành 1 thiếu nữ căng đầy sức sống. Càng lớn, ham muốn của nàng QA càng cao, nàng muốn application phải có nhiều tính năng hơn nữa. Trước đây, một tuần nàng chỉ đòi hỏi change requirement một lần, giờ thì ngày nào nàng cũng muốn. Đôi khi một ngày muốn đến 2, 3 lần, thậm chí sáng đòi thêm feature này, chiều lại đòi bỏ đi. Làm hai anh Dev và IT Op làm việc chết bỏ, mệt bở hơi tai, OT triền miên nhưng release vẫn bị trễ. Khiến nàng QA không thể nào thỏa mãn, bực mình cáu gắt liên miên, hờn giận đòi chia tay.
Buồn lắm, hai chàng trai ra bờ suối ngồi khóc với nhau. Rồi 1 ông cụ râu tóc bạc phơ hiện ra trong làn khói trắng, hiền từ bảo
Ta là bụt đây, làm sao con khóc ?

![](http://giaoducso.vn/upload_file/EMCO_20170121070024truyen-cuoi-3-dieu-uoc.jpg)

2 chàng trai thuật lại sự tình, ông Bụt nghe xong thì cười ôn tồn bảo:
Trong phát triển phần mềm, anh developer thì chỉ tập trung ngồi code ứng dụng. Nhưng để ứng dụng chạy được thì cần phải có môi trường, server, infrastructure. Cho nên cần có IT Operation để deploy vận hành ứng dụng. Anh dev chỉ biết code, anh IT operation chỉ biết vận hành nên giữa 2 con luôn có 1 bức tường ngăn cách gọi là Wall of Confusion, làm delay quá trình release sản phẩm. Chưa kể mỗi lần dev thêm tính năng mới là phải deploy lại, dẫn tới các issue như down time, troubleshooting environment issues…

![](https://dzone.com/storage/temp/7180884-ingraphics-devops-to-agile.png)

Nếu con đọc truyện bảy viên ngọc rồng, sẽ có biết 1 chiêu thức gọi là “Lưỡng long nhất thể”, hai người có thể lực tương đương nhau hợp lại làm 1, thì dù cho sức có yếu nhưng khi kết hợp lại thì sẽ mạnh như rồng hổ. Đủ sức chiều nàng QA.

![](https://blog.testlodge.com/wp-content/uploads/2018/06/what-is-devops-1024x538.png)

Hai con mỗi người có 1 skill riêng, nếu làm việc đơn lẻ thì sẽ không phục vụ nổi nàng QA đang tuổi căng đầy sức sống, nhưng nếu 2 con cùng phối hợp với nhau thì ta đảm bảo nàng QA sẽ phải khóc thét vì sung sướng. Nói theo ngữ cảnh thiendia, người ta gọi là play some đó con. 
Khi kết hợp được với nhau, các con sẽ tạo nên một mô hình gọi là CI/CD (Continuous Integration, Continuous Delivery), khiến việc deploy ứng dụng nhanh chóng, liên tục, đảm bảo thõa mãn nàng QA

![](https://hostadvice.com/wp-content/uploads/2018/03/devopstools1.jpg)

CI/CD là gì vậy? Làm thế nào để 2 anh em con hợp lại làm một được ạ? 2 chàng trai hỏi ông bụt:
Ồ, để làm việc đó thì phải khổ luyện nhiều lắm, không chỉ có ngôn ngữ lập trình mà còn cả kĩ năng SysAdmin, hãy nhớ lấy mấy skill sau
![](https://endocode.com/img/blog/DevOps_Roadmap.png)

Hai chàng trai nghe xong mừng vui như bắt được vàng, quỳ lạy cảm ơn bụt rối rít. Từ đó hai chàng trai về nhà ngày đêm tu luyện, mong một ngày có thể build thành công hệ thống CI/CD để phục vụ nàng User
Muốn biết 2 chàng đã build như thế nào, đón đọc tập tiếp theo…

