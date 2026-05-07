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

<img width="1920" height="1022" alt="{7B7FDD7B-836F-48CD-8399-9856CED27B18}" src="https://github.com/user-attachments/assets/764d34f8-6a92-4950-8ee9-278461ee959c" /></p>

👉 Lưu ý: Nếu không truy cập được có thể là do cơ chế bảo mật của django, ip sử dụng chưa được khai báo trong danh sách người quen (allowed Hosts). Để khắc phục tình trạng này cần phải khai báo ip trong file settings.py hoặc để dễ dàng cho việc học tập có thể cho phép tất cả.

<img width="788" height="640" alt="{F1460C89-28BA-4A33-BC59-E296D1635735}" src="https://github.com/user-attachments/assets/aee75b6c-400f-4bab-94ed-32b3bb2539d7" /></p>

---

# 14: TEST CRUD

- Bước 1: Thêm dữ liệu

1) Thêm khách hàng

<img width="1920" height="985" alt="{03D762EA-6591-4FD2-8302-351869F91237}" src="https://github.com/user-attachments/assets/37ceb3fb-0579-4726-903d-c723d52acdb3" /></p>

2) Thêm Giao dịch

<img width="1920" height="1020" alt="{96D78736-36C0-4E62-BD1B-0D7261BBD0EE}" src="https://github.com/user-attachments/assets/f9461308-a2d4-43ed-8ce2-8ea6b83aeb30" /></p>

---

## 15: TEST PHPMYADMIN

- Truy cập địa chỉ `http://IP_UBUNTU:8888`

<img width="1920" height="1028" alt="image" src="https://github.com/user-attachments/assets/a08369e6-2d40-41f5-94d1-680e772b0b40" /></P>

- Kiểm tra các bảng

<img width="1920" height="1017" alt="{EE9EBC7F-45DB-48E4-90E5-5D4D7F02EEB0}" src="https://github.com/user-attachments/assets/86987a98-4899-4780-8f31-5b02f606c4d8" /></p>

<img width="1920" height="1027" alt="{F57847B3-F13B-4651-B077-E455C71635BC}" src="https://github.com/user-attachments/assets/98000560-6577-4172-bb5b-9e4a2652efc5" /></p>

<img width="1920" height="1022" alt="{A18F0037-4DA6-4C50-BFC3-7C384E6DB141}" src="https://github.com/user-attachments/assets/76b2e438-2f40-4cad-ae69-df7ddb28485e" /></p>

---

## 16: TẠO TEMPLATE HTML

- Bước 1: Tạo thư mục template `mkdir -p django/management/templates`

- Bước 2: Tạo file home.html `nano django/management/templates/home.html`

- Bước 3: Thêm nội dung

<img width="1137" height="826" alt="{5976C949-B8AA-4640-BEBA-DAFB1E7E6559}" src="https://github.com/user-attachments/assets/4c55dbc8-a953-4fc2-8045-3a16ac111ab2" /></p>

- Bước 4: Tạo file views.py `nano django/management/views.py`

<img width="1141" height="826" alt="{3444BC36-CA06-419F-8820-D7B977DEABAA}" src="https://github.com/user-attachments/assets/155ee429-8891-432f-a08b-b195609341dc" /></p>

- Bước 5: Tạo file urls.py `nano django/pawnshop/urls.py`

<img width="1144" height="828" alt="{842DF8CC-CC9D-4896-9D3C-3AB791B4BF53}" src="https://github.com/user-attachments/assets/4a9d32d2-8564-40a9-beab-a134caeb3d23" /></p>

--- 

## 17: TEST WEB

- Truy cập địa chỉ 'http://172.31.174.131:8000/`
  
<img width="1920" height="1029" alt="{50C5AA8C-E753-4E64-A331-C358D3D4D7E3}" src="https://github.com/user-attachments/assets/a2d1fd3d-5cd1-42e6-9861-86aabb4418bc" /></p>

---

## 18: PUBLIC DJANGO LÊN SUBDOMAIN BẰNG CLOUDFLARE TUNNEL

- Bước 1: Dowload claudfare tunnel bằng lệnh `wget https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb`

<img width="1149" height="832" alt="image" src="https://github.com/user-attachments/assets/2dba8b73-c28a-4b7f-8ee7-8dea4813ac02" /></p>

- Bước 2: Cài đặt `sudo dpkg -i cloudflared-linux-amd64.deb`

- Bước 3: Kiểm tra `cloudflared --version`

<img width="836" height="613" alt="{810FF189-36A5-4CC8-8F51-A17ABC56EBE5}" src="https://github.com/user-attachments/assets/c5ea610d-f430-4dbd-9bd3-a527a2b02b9d" /></p>

---

## 19: LOGIN CLOUDFLARE

- Chạy lệnh 'cloudflared tunnel login` sẽ sinh ra 1 địa chỉ để login vào claudfare tunnel

- Truy cập địa chỉ đó trên trình duyệt

<img width="835" height="606" alt="{CA1C8789-0390-475A-A8D8-DBF4E66E441D}" src="https://github.com/user-attachments/assets/c1d21de0-fa73-494a-9b2d-7fc2e5196bf3" /></p>

- Chọn đúng domain -> Chọn Authorize

<img width="1410" height="745" alt="{4A182B01-1A62-4CB8-BEFD-27E95C016FF4}" src="https://github.com/user-attachments/assets/6721c93a-37c3-4e8f-90b9-8cb3125a1064" /></p>

👉 Sau khi click sẽ hiện thông báo đồng thời trên ubuntu cũng thông báo **You have successfully logged in** và sinh ra file .pem

<img width="1920" height="1022" alt="image" src="https://github.com/user-attachments/assets/75956c0e-12e7-4157-8af1-d35d8790224f" /></p>

<img width="1045" height="744" alt="{581C8B6F-168F-43BA-B53E-A033F9BB80EE}" src="https://github.com/user-attachments/assets/b1ac52d5-d13f-484e-819b-08f1df45d9b1" /></p>

---

## 20: TẠO TUNNEL

- Chạy lệnh: `cloudflared tunnel create camdo-tunnel` sẽ ra 1 dãy id

<img width="832" height="602" alt="{C8CE2927-5BEA-4EB0-A962-4894914EA46A}" src="https://github.com/user-attachments/assets/f947d4e3-0234-4070-b6f1-59bd598607d0" /></p>

- Tạo file config.yml bằng lệnh `nano ~/.cloudflared/config.yml`

<img width="1091" height="822" alt="{366841DA-4FB7-4FFB-AFF4-EAA9EF845C75}" src="https://github.com/user-attachments/assets/8d8e3f4d-c870-4567-b1e3-1d3fc68db2bc" /></p>

- Thêm nội dung sau ( Vì dùng chung đường hầm với web cũ nên không cần thêm id, có thể dùng chung ip với web cũ)

<img width="829" height="600" alt="{C3765F71-80C9-41AE-9A3B-260C458973CB}" src="https://github.com/user-attachments/assets/4b7da615-43bc-42ea-ab5f-add2b4d5623a" /></p>

---

## 21: CHẠY TUNNEL

- Chạy lệnh `cloudflared tunnel run camdo-tunnel`

<img width="1139" height="827" alt="{78CE7D21-BF3A-4AE4-B399-CFFC0FCC4E9A}" src="https://github.com/user-attachments/assets/15ffb973-77e0-48d5-bfc5-ae5f684a4f65" /></p>

- Truy cập http://camdo.ducduong.id.vn

<img width="1918" height="1020" alt="{B80F327C-3F48-454C-97D0-074B51A09A8C}" src="https://github.com/user-attachments/assets/5c2ea192-6b21-4a1f-96ec-8b9104665dbb" /></p>




- 



















