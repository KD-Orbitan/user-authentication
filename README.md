# User Authentication API with MySQL

![GitHub](https://img.shields.io/github/license/KD-Orbitan/user-authentication)
![GitHub last commit](https://img.shields.io/github/last-commit/KD-Orbitan/user-authentication)

Một hệ thống xác thực người dùng sử dụng Node.js, Express và MySQL, hỗ trợ đăng ký, đăng nhập và quản lý thông tin tài khoản.

## Tính năng chính

- **Đăng ký tài khoản** (không yêu cầu xác thực email, chỉ kiểm tra định dạng)
- **Đăng nhập/JWT authentication**
- **Lấy thông tin người dùng** (có xác thực)
- **Cập nhật thông tin cá nhân**
- **Đổi mật khẩu**
- **Quản lý voucher** (kèm xác thực)

## Công nghệ sử dụng

- **Backend**: Node.js + Express
- **Database**: MySQL
- **Authentication**: JWT (JSON Web Tokens)
- **Password hashing**: bcryptjs
- **Input validation**: express-validator

## Cài đặt

1. Clone repository
```bash
git clone https://github.com/KD-Orbitan/user-authentication.git
cd user-authentication
```
2. Cài đặt dependencies

```bash
npm install
```
3. Thiết lập biến môi trường (.env)
```env
PORT=3000
DB_HOST=your_mysql_host
DB_USER=your_mysql_username
DB_PASSWORD=your_mysql_password
DB_NAME=your_database_name
JWT_SECRET=your_jwt_secret_key
JWT_EXPIRE=24h
```
4. Khởi chạy server
```
npm start
```
## API Endpoints
Authentication
|Method	|Endpoint	|Mô tả	Yêu cầu|
|-----------|-----------|-----------|
|'POST'	|/login|	Đăng nhập	Email + Password|
|'POST'	|/register|	Đăng ký tài khoản mới	Email (đúng định dạng) + Password + Thông tin cá nhân| 

Customer (yêu cầu JWT)
|Method	|Endpoint	|Mô tả|
|-----------|-----------|-----------|
|'GET'	|/me|	Lấy thông tin tài khoản|
|'PUT'	|/me|	Cập nhật thông tin|
|'PUT'	|/change-password	|Đổi mật khẩu|

Voucher (yêu cầu JWT)
|Method	|Endpoint	|Mô tả|
|-----------|-----------|-----------|
|'GET'	|/vouchers|	Lấy danh sách voucher|

## Ví dụ Request/Response
Đăng ký tài khoản:

POST /register
```
Content-Type: application/json

{
  "email": "user@example.com",
  "password": "securepassword123",
  "name": "Nguyễn Văn A",
  "phone": "0123456789"
}
```
Đăng nhập:
POST /login
```
Content-Type: application/json

{
  "email": "user@example.com",
  "password": "securepassword123"
}
```
Response thành công sẽ trả về JWT token:
```
json
{
  "success": true,
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
}
```
## Đóng góp
Pull requests được hoan nghênh! Hãy đảm bảo:

Fork repository

Tạo branch mới (git checkout -b feature/your-feature)

Commit changes (git commit -am 'Add some feature')

Push lên branch (git push origin feature/your-feature)

Tạo Pull Request

## License
MIT © [KD-Orbitan](https://github.com/KD-Orbitan)
