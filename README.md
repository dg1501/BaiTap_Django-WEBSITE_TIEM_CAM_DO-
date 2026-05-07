## PHÁT TRIỂN ỨNG DỤNG VỚI MÃ NGUỒN MỞ (DJANGO + XÂY DỰNG WEBSITE QUẢN LÝ TIỆM CẦM ĐỒ)
### HỌ TÊN: NGUYỄN ĐỨC DƯƠNG
### LỚP: K58KTP
### MSSV: K225480106093

---

## 1: CHUẨN BỊ UBUNTU

- Kiểm tra phiên bản Docker `docker --version`

- Kiểm tra phiên bản Docker Compose `docker compose version`

<img width="1033" height="654" alt="{49B6E3E1-AE32-4839-A9B1-0F12281C082E}" src="https://github.com/user-attachments/assets/2ef83daa-4de6-4cb2-bc41-4c2c0a68a02a" /></P>

---

## 2: TẠO PROJECT

- Bước 1: Tạo thư mục `mkdir camdo_project`

- Bước 2: Vào thư mục `cd camdo_project`

<img width="994" height="660" alt="{BDF02D7F-48B8-4AF1-8608-A59F3F8BFE58}" src="https://github.com/user-attachments/assets/7ce9863b-ad3b-4b18-8f99-3232829944f3" /></P>

- Bước 3: Tạo thư mục **django** trong **camdo_project**

<img width="994" height="662" alt="{092374A5-9B7A-4D5A-A350-EC313D69E754}" src="https://github.com/user-attachments/assets/fa7cc1dd-a2fb-46d4-8e47-c9cf5c073448" /></p>

---

## 3: TẠO DOCKERFILE

- Bước 1: Vào thư mục Django: `cd django`

- Bước 2: Tạo file DockerFile `nano Dockerfile`

- Bước 3: Thêm nội dung cho File **dockerfile**

<img width="1258" height="830" alt="{4CFBB9EE-B51F-4841-9CEF-627F09D91C6F}" src="https://github.com/user-attachments/assets/5430b5a3-ee1f-4a13-8935-8592139c4d40" /></P>

---

## 4: TẠO FILE requirements.txt

- Bước 1: Tạo file requirements.txt `nano requirements.txt`

- Bước 2: Dán nội dung sau

<img width="991" height="671" alt="{E79F6C5D-B041-49D1-AD38-F1E7A486CD2A}" src="https://github.com/user-attachments/assets/2d90bc7e-3f9f-4884-ae54-c1ce9a8a15a8" /></p>

---

## 5: TẠO FILE DOCKER - COMPOSE.YML

- Bước 1: Quay lại thư mục gốc `cd ..`

<img width="1233" height="820" alt="{C2F9A4E1-EAB4-4CFF-BD18-7F24D650DE3A}" src="https://github.com/user-attachments/assets/2793313a-166d-46d1-8c7e-191a5002f972" /></p>

- Bước 2: Tạo file docker - compose.yml `nano docker-compose.yml`

- Bước 3: Dán nội dung sau

<img width="1234" height="815" alt="{645ACD9A-970D-404E-B11A-724F33FB92D2}" src="https://github.com/user-attachments/assets/7a0f8eea-8606-4ff8-a8e5-1e62c1cbef0d" /></p>

---

## 6: TIẾN HÀNH BUILD CONTAINER

- Bước 1: Build bằng lệnh `docker compose up -d --build`

<img width="999" height="661" alt="{D24E4F6D-0BBE-4CB3-B635-C3A451C0B083}" src="https://github.com/user-attachments/assets/d2069169-2b3a-4f18-802b-ab00aef82832" /></p>

- Bước 2: Kiểm tra container bằng lệnh `docker ps`

<img width="1175" height="667" alt="{61DE3E6B-2A19-4B82-8A6B-8EE350CDA0A9}" src="https://github.com/user-attachments/assets/1c1db0b6-19cd-4936-89fb-9325df2f54d7" /></p>

👉 Kết quả phải thấy 3 service: **mariadb + phpmyadmin + django_app** 

---

## 7: TẠO DJANGO PROJECT

- Bước1: chạy lệnh `docker compose exec django django-admin startproject pawnshop .`

<img width="1171" height="663" alt="{D74BE14D-7AC8-470E-8073-DFDCC0EBD8E4}" src="https://github.com/user-attachments/assets/26523474-0cc4-4d1a-8e5c-e600898c7470" /></p>

- Bước 2: Kiểm tra file `ls django`

<img width="1148" height="681" alt="{83F00666-65FC-4042-82ED-AD4BCE456A5A}" src="https://github.com/user-attachments/assets/abb07f6b-6741-48ad-a383-b56ce9cac795" /></p>

👉 Kết quả phải thấy

manage.py

pawnshop

Dockerfile

requirements.txt

---

# 8: TẠO APP

- Bước 1: Chạy lệnh `docker compose exec django_app python manage.py startapp management`

- Bước 2: Kiểm tra `ls django`

<img width="1146" height="682" alt="{EB37F68E-D33E-4199-9455-7F7C841C9A4F}" src="https://github.com/user-attachments/assets/1267db7d-358f-4715-bbd7-a33b9b81a133" /></p>

---

## 9: CẤU HÌNH DATABASE

- Bước 1: Mở settings.py `nano django/pawnshop/settings.py`

- Bước 2: Tìm DATABASES -> Trong nano bấm **Ctrl + M** -> Gõ **DATABASES**

- Bước 3: Tìm đến và sửa thành như sau

<img width="1184" height="740" alt="{B21D9A1C-0BC8-44BE-86AF-65BF12D2C42C}" src="https://github.com/user-attachments/assets/e9024252-3fce-4bd9-8602-fe3d7827fae0" /></P>

- Bước 4: Thêm app -> tìm INSTALLED_APPS -> Thêm **'management',**

<img width="958" height="593" alt="image" src="https://github.com/user-attachments/assets/33ff51d8-6894-4303-a3f5-6627f63faedf" /></p>

---

## 10: TẠO DATABASE MODEl

- Bước 1: Mở model.py bằng lệnh `nano django/management/models.py`

- Bước 2: Thêm nội dung

<img width="1302" height="797" alt="{287D4B98-57C0-4DF4-A8F2-D54804CF87B1}" src="https://github.com/user-attachments/assets/339d97fa-3551-41ef-9478-c365130d4b03" /></p>

- Bước 3: Đăng ký model vào admin bằng lệnh `nano django/management/admin.py`

<img width="1211" height="785" alt="{A1CB2AFE-F08D-4D98-9A96-86D2D8A6BA80}" src="https://github.com/user-attachments/assets/7e2997cb-2d43-41a7-a1b7-363a0acf591f" /></p>

---

## 11: TẠO MIGRATION

- Chạy lệnh: `docker compose exec django python manage.py makemigrations`

<img width="1213" height="803" alt="{9292682E-22C6-42A4-A472-35458D64D872}" src="https://github.com/user-attachments/assets/b57b04a7-b7de-4667-b63c-0a371832df6a" /></p>

- APPLY DATABASE bằng lệnh `docker compose exec django python manage.py migrate`

<img width="1214" height="798" alt="{8C172D22-B954-40C6-8B2E-650262AFBDCD}" src="https://github.com/user-attachments/assets/a2a6f8c6-1d7d-443f-959f-1c652d7bb480" /></p>

---

## 12: TẠO SUPERUSER

- Chạy lệnh `docker compose exec django python manage.py createsuperuser`

<img width="890" height="590" alt="{EE0A32BE-3308-4299-9374-C5032C3CB8B8}" src="https://github.com/user-attachments/assets/8bb3a2ca-ec97-4ace-ad84-f9a41f668746" /></p>

👉 Thực hiện điền các thông tin username & password 

---

# 13: CHẠY WEB

- Truy cập django admin bằng địa chỉ: `http://IP_UBUNTU:8000/admin`

<img width="1920" height="1028" alt="{AB088CF6-ECDE-4A8B-B52C-284D7ACA8DB0}" src="https://github.com/user-attachments/assets/f50964cc-6a31-4eb6-b148-2116057a7ddf" /></p>

Lưu ý: Nếu không truy cập được có thể là do cơ chế bảo mật của django, ip sử dụng chưa được khai báo trong danh sách người quen (allowed Hosts). Để khắc phục tình trạng này cần phải khai báo ip trong file settings.py hoặc để dễ dàng cho việc học tập có thể cho phép tất cả.

<img width="788" height="640" alt="{F1460C89-28BA-4A33-BC59-E296D1635735}" src="https://github.com/user-attachments/assets/aee75b6c-400f-4bab-94ed-32b3bb2539d7" /></p>





