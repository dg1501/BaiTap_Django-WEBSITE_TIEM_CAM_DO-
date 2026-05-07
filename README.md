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

- Bước 2: Kiểm tra file




