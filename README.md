# Building a Highly Available, Scalable Web Application.
# Phase 2: Tạo ứng dụng web cơ bản.
## Task 1 : Tạo VPC.
Thiết lập địa IPv4 CIDR cho VPC là 10.0.0.0/16 và tạo 2 zone chưa các public và private.

![image](https://github.com/user-attachments/assets/9c850306-3585-4e46-88b7-704ad20963a0)

![image](https://github.com/user-attachments/assets/7819918b-16c1-4298-8c5e-b2f91205fedd)

Thêm rule chấp nhận tất IP truy cập giao thức.

![image](https://github.com/user-attachments/assets/c6678235-8e56-40bd-bf2d-a38a47835c42)

## Task 2: Tạo máy ảo sử dụng EC2.

![image](https://github.com/user-attachments/assets/9b02bbdd-02b7-4d56-ba8d-e29350f62c0e)

* Chọn AMI

![image](https://github.com/user-attachments/assets/e7876fe0-4095-4312-a12a-a3d5ce3f05d0)


* Thiết lập mạng

![image](https://github.com/user-attachments/assets/7415ded4-83f3-4691-83b1-d6d140f1d086)


* Thiết lập security group cho instance

![image](https://github.com/user-attachments/assets/37478a4f-154d-4440-b45a-7a81574a156a)


* Thiết lập user data cho instance

![image](https://github.com/user-attachments/assets/e734da38-7ad9-4af9-825e-5b63c7aa328f)



## Task 3: Testing the deployment.
Truy cập vào địa chỉ public iPv4 của instance, thử nghiệm thêm một số học sinh để có dữ liệu minh họa việc chuyển sang database

![image](https://github.com/user-attachments/assets/fd5930e6-8d49-4922-b68e-39da05747e22)

# Phase 3: Decoupling the application componets.
Ở phase này sẽ tách cơ sở dữ liệu ra và được triển khai riêng trên RDS. Việc tách cơ sở dữ và triển khai như vậy dễ quản lý hơn, sử group để triển trên nhiều để đảm bảo tính sẵn sàng và bảo mật.

## Task 1:Cấu hình VPC.
* Tạo 2 subnet 
## Task 2: Tạo cấu hình Amazon RDS database.

![image](https://github.com/user-attachments/assets/8186532f-461e-4237-90c3-98ed4ff9819e)

*Tạo subnet group gồm 2 subnet đã chọn db 

![image](https://github.com/user-attachments/assets/0dfe5f58-8285-405b-ba25-e51cd9297159)


* Tạo Database

![image](https://github.com/user-attachments/assets/49d6b96c-b15b-4945-bac9-9d05b75e1953)

* Tạo DB instance
Đặt username và password cho 

![image](https://github.com/user-attachments/assets/105903c4-ba64-43ae-a630-32ce41ba61ef)

* Thiết lập instance và lưu trữ

![image](https://github.com/user-attachments/assets/45b42e50-e560-4520-a9a5-b61fd00918ea)

## Task 3: Cấu hình môi trường phát triển.

![image](https://github.com/user-attachments/assets/dff727f1-794e-4c1b-b751-0ba9a00b8fc1)

Sau khi tạo xong có thể truy cập CLI của Unbutu

![image](https://github.com/user-attachments/assets/875207ff-375f-401d-82f5-8643268ec43e)

## Task 4: Provisioning Secrets Manager.

![image](https://github.com/user-attachments/assets/b97ba6d9-12b7-4ddd-abbe-55926e0c0230)

## Task 5: Tạo thêm 1 EC2 instance cho web server mới.

![image](https://github.com/user-attachments/assets/8a9deb20-c0c9-4a06-9320-3cd7107021c3)

## Task 6: Migrating the database.

![image](https://github.com/user-attachments/assets/870ece46-65ae-4998-b3e4-e572e525038f)

Sau khi đăng nhập thành công thì vào test

## Task 7: Testing

Kết quả chạy web được triển khai trên EC2 instance mới và tách rời RDS

![Screenshot 2024-10-03 200336](https://github.com/user-attachments/assets/54d3d2b2-3203-4d39-95e7-4f20e077a0ea)

# Phase 4: Implementing high availability and scalability.
## Task 1: Application Load Balancer .
* Load Balancer dùng để phân phối đều lưu lượng truy cập đến các máy chủ hoặc thành phần của hệ thống.

![image](https://github.com/user-attachments/assets/b04076f0-5b04-4663-a263-f29086b90805)

* Network Mapping

![image](https://github.com/user-attachments/assets/c8ddb301-6d0d-42c6-8d38-cc5a031f946d)

* Chọn Security Group ALB-SG đã thiết lập từ trước để quản lý và kiểm soát traffic đến và đi từ Load Balancer.

![image](https://github.com/user-attachments/assets/37c9dfb6-d4ca-4c48-b59c-a7bf2723d4f7)

* Thiết lập listeners and routing để kiểm tra các yêu cầu kết nối sử dụng các cổng và phương kết nối mạng ở đây là phương thức http port 80 và sử dụng target group đã tạo.

![image](https://github.com/user-attachments/assets/18dded3e-77c2-478c-8679-6bff0092581d)

## Task 2: Triển khai amazon EC2 Auto Scalling
ASG giúp hệ thông vận hành tốt, giúp tự động quản lý và mở rộng instance EC2 được triển dựa vào EC2 ở phase 3.
* Tạo Template

![image](https://github.com/user-attachments/assets/58e21919-0ae9-4a3e-9fa8-7771e8ef514a)

* Thiết Template đã tạo để auto scalling group tạo instance

![image](https://github.com/user-attachments/assets/87ea64f1-8e92-43f6-badd-2fc34bd25945)

* Lựa chọn VPC và thiết lập những AZ và subnet mà auto sẽ triển khai

![image](https://github.com/user-attachments/assets/5dd19a0c-c000-4568-9a59-b0316c988888)

* Lựa chọn load balance

![image](https://github.com/user-attachments/assets/7fd6bb11-3107-4df2-b95d-78ca694ed5e6)

* Gán ALB cho auto scalling group

![image](https://github.com/user-attachments/assets/56955d5c-5e95-46d8-a82a-2393f0d439b2)

* Chọn group size và scalling với min là instance và max là 6 instance tùy thuộc vào số lượng yêu cầu, công việc cần xử lý.

![image](https://github.com/user-attachments/assets/f654b496-5046-42fb-87f5-5a08c87853c5)

* Sau khi tạo xong

![image](https://github.com/user-attachments/assets/5faae8ce-9c54-468f-916f-ca1b70e75c89)

* Kết quả

![image](https://github.com/user-attachments/assets/83c08114-cc4e-4bae-9489-c99138308db3)

## Task 3: Truy cập vào web

![image](https://github.com/user-attachments/assets/25fabd2e-df9c-4910-87d3-a88d8fb57480)

## Task 4: Load test ứng dụng

![image](https://github.com/user-attachments/assets/3b7da79b-9a05-4524-9d80-7447df7a4c9f)


