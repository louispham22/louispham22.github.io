---
layout: post
title:  "How to delete Docker Images, Containers and Volumes"
date:   2019-07-24 8:30
categories: docker
permalink: /archivers/how-to-delete-docker-images-containers-and-volumes
---

**Cách để xóa Docker Images, Containers, và Volumes**

# Xóa tất cả hình ảnh chưa sử dụng hoặc thừa, Containers, Volumes và Networks
Docker cung cấp một lệnh duy nhất sẽ dọn sạch mọi tài nguyên - hình ảnh, containers , volumes và networks - đang treo lơ lửng (không được liên kết với container):

		docker system prune

Để loại bỏ thêm bất kỳ container đã dừng nào và tất cả các hình ảnh không sử dụng (không chỉ là hình ảnh lơ lửng),hãy thêm chỉ báo -avào lệnh:  

		docker system prune -a

# Xóa Docker Images

Xóa một hoặc nhiều hình ảnh cụ thể

Sử dụng lệnh docker images với chỉ báo -a  để định vị ID của hình ảnh bạn muốn xóa. Điều này sẽ hiển thị cho bạn mọi hình ảnh, bao gồm các lớp hình ảnh trung gian. Khi bạn đã định vị những hình ảnh bạn muốn xóa, bạn có thể chuyển ID hoặc thẻ của họ tới docker rmi:

# List:

docker images -a

# Xóa:

		docker rmi ImageImage

Xóa hình ảnh lơ lửng

Hình ảnh Docker bao gồm nhiều lớp. Hình ảnh lơ lửnglà các lớp không có mối quan hệ với bất kỳ hình ảnh được gắn thẻ nào. Chúng không còn phục vụ một mục đích và tiêu thụ không gian đĩa. Chúng có thể được định vị bằng cách thêm cờ lọc, -fvới giá trị dangling=true vào lệnh docker images. Khi bạn chắc chắn muốn xóa chúng, bạn có thể sử dụng lệnh docker images purge :

Nếu bạn xây dựng một hình ảnh mà không gắn thẻ nó, hình ảnh sẽ xuất hiện trên danh sách các hình ảnh lơ lửng bởi vì nó không có liên kết với một hình ảnh được gắn thẻ. Bạn có thể tránh tình trạng này bằng cách cung cấp thẻ khi bạn xây dựng và bạn có thể gắn thẻ lại một hình ảnh với lệnh thẻ docker.

Chú ý: Nếu bạn xây dựng một hình ảnh mà không gắn thẻ nó , hình ảnh sẽ xuất hiện trên danh sách các hình ảnh lơ lửng bởi vì nó không có liên kết với một hình ảnh được gắn thẻ . Bạn có thể tránh tình trạng này bằng cách cung cấp thẻ khi xây dựng và bạn có thể gắn thẻ lại một hình ảnh với lệnh docker tag.

# List:

		docker images -f dangling=true

# Remove:

		docker images purge

# Xóa hình ảnh theo mẫu

Bạn có thể tìm thấy tất cả các hình ảnh phù hợp với một mẫu bằng cách  kết hợp docker images và grep. Khi hài lòng,hãy xóa chúng bằng cách sử dụng awk để chuyển các ID tới docker rmi. Lưu ý rằng những tiện ích này không được Docker cung cấp và không nhất thiết phải có trên tất cả các hệ thống:

# List:

		docker images -a | grep "pattern"

# Remove:

		docker images -a | grep "pattern" | awk '{print $3}' | xargs docker rmi

# Xóa tất cả hình ảnh

Tất cả các hình ảnh Docker trên một hệ thống có thể được liệt kê bằng cách thêm-a vào lệnh docker images. Khi bạn chắc chắn muốn xóa tất cả, bạn có thể thêm cờ-q  để chuyển ID hình ảnh tới docker rmi:

# List:

		docker images -a

# Remove:

		docker rmi $(docker images -a -q)

# Xóa Containers

Xóa một hoặc nhiều container cụ thể

Sử dụng lệnh docker ps với cờ -a-a để xác định tên hoặc ID của các container mà bạn muốn xóa:

# List:

		docker ps -a

# Remove:

		docker rm ID_or_NameID_or_Name

# Xóa container khi thoát

Nếu  biết khi nào bạn đang tạo container mà bạn sẽ không muốn giữ nó khi hoàn tất, bạn có thể chạy docker run --rm  để tự động xóa container khi nó thoát.

# Chạy và xóa:

		docker run --rm image_name

# Xóa tất cả các container đã thoát

Bạn có thể định vị cáccontainer bằng cách sử dụng docker ps -a và lọc chúng theo trạng thái : được tạo, khởi động lại, chạy, tạm dừng hoặc thoát. Để xem lại danh sách các container đã thoát, hãy sử dụng chỉ báo-f  để lọc dựa trên trạng thái. Khi bạn đã xác minh bạn muốn loại bỏ các container đó, hãy sử dụng -q để chuyển các ID tới lệnh docker rm.

# List:

		docker ps -a -f status=exited

# Remove:

		docker rm $(docker ps -a -f status=exited -q)

# Xóa containers bằng nhiều bộ lọc

Bộ lọc Docker có thể được kết hợp bằng cách lặp lại cờ lọc với một giá trị bổ sung. Điều này dẫn đến một danh sách các container đáp ứng một trong hai điều kiện. Ví dụ: nếu bạn muốn xóa tất cả container được đánh dấu là Created (trạng thái có thể dẫn đến khi bạn chạy container với lệnh không hợp lệ) hoặc  Exited, bạn có thể sử dụng hai bộ lọc:

# List:

		docker ps -a -f status=exited -f status=created

# Remove:

		docker rm $(docker ps -a -f status=exited -f status=created -q)

# Loại bỏ các containers theo mẫu

Bạn có thể tìm thấy tất cả các containers khớp với mẫu bằng cách kết hợp giữa docker ps và grep. Khi bạn hài lòng rằng bạn có danh sách bạn muốn xóa, hãy sử dụng awk và xargs để cung cấp ID cho  docker rmi. Lưu ý rằng các tiện ích này không được Docker cung cấp và không nhất thiết phải có trên tất cả các hệ thống:

# List:

		docker ps -a | grep "pattern”

# Remove:

		docker ps -a | grep "pattern" | awk '{print $3}' | xargs docker rmi

# Dừng và xóa tất cả containers

Bạn có thể xem lại các container trên hệ thống của bạn với docker ps. Thêm cờ-a  sẽ hiển thị tất cả các container. Khi bạn chắc chắn muốn xóa chúng, bạn có thể thêm cờ -qđể cung cấp các ID cho các lệnh docker stop và docker rm:

# List:

		docker ps -a

# Remove:

		docker stop $(docker ps -a -q)
		
		docker rm $(docker ps -a -q)

# Xóa Volumes

Xóa một hoặc nhiều Volumes cụ thể - Docker 1.9 trở lên

Sử dụng lệnh docker volume ls để xác định tên volumehoặc tên bạn muốn xóa. Sau đó, bạn có thể xóa một hoặc nhiều volumes bằng lệnh docker volume rm:U

# List:

		docker volume ls

# Remove:

		docker volume rm volume_namevolume_name

# Xóa Volumes lơ lửng - Docker 1.9 trở lên

Vì điểm của volumes là tồn tại độc lập với các container, khi một container được lấy ra, một volume không được tự động loại bỏ cùng một lúc. Khi một volume tồn tại và không còn kết nối với bất kỳ container nào, nó được gọi là volume lơ lửng. Để xác định vị trí chúng để xác nhận bạn muốn xóa , hãy sử dụng lệnh docker volume lsvới bộ lọc để giới hạn kết quả volumes lơ lửng. Khi bạn đã hài lòng với danh sách, hãy xóa tất cả chúng với  docker volume prune:

# List:

		docker volume ls -f dangling=true

# Remove:

	docker volume prune

# Xóa container và volume của nó

Nếu bạn đã tạo một volume chưa đặt tên, nó có thể bị xóa cùng lúc với container có chỉ báo -v. Lưu ý rằng điều này chỉ hoạt động với volume chưa đặt tên. Khi container được loại bỏ thành công, ID của nó sẽ được hiển thị. Lưu ý rằng không có tham chiếu nào được thực hiện để loại bỏ volume. Nếu chưa được đặt tên, nó sẽ bị xóa khỏi hệ thống. Nếu được đặt tên, nó  vẫn âm thầm tồn tại.

# Remove:

		docker rm -v container_name

# Kết Luận 

Hướng dẫn này bao gồm một số lệnh phổ biến được sử dụng để xóa hình ảnh, containers và volumes với Docker. Có nhiều kết hợp và chỉ báo khác có thể được sử dụng với nhau. Để có hướng dẫn toàn diện về những gì có sẵn, xem tài liệu Docker cho  docker system prune, docker rmi, docker rm và docker volume rm.