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

*Tạo subnet group gồm 2 subnet đã chọn

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

## Task 4: Provisioning Secrets Manager

![image](https://github.com/user-attachments/assets/b97ba6d9-12b7-4ddd-abbe-55926e0c0230)

## Task 5: Tạo thêm 1 EC2 instance cho web server mới

![image](https://github.com/user-attachments/assets/8a9deb20-c0c9-4a06-9320-3cd7107021c3)

## Task 6: Migrating the database

![image](https://github.com/user-attachments/assets/870ece46-65ae-4998-b3e4-e572e525038f)

Sau khi đăng nhập thành công thì vào test

## Task 7: Testing

Kết quả chạy web được triển khai trên EC2 instance mới và tách rời RDS

![Screenshot 2024-10-03 200336](https://github.com/user-attachments/assets/54d3d2b2-3203-4d39-95e7-4f20e077a0ea)
