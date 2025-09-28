# Simple Authentication & Cookie Authentication

## 🧪 Cách Test Bằng Postman

1. **Chạy server**
   - Với Basic Auth: `node server.js` (port 3000)
   - Với Cookie Auth: `node app.js` (port 3001)

2. **Test Basic Authentication**
   - **Public route**: Gửi GET `http://localhost:3000/public` → Không cần auth.
   - **Secure route**: Gửi GET `http://localhost:3000/secure`
     - Thêm Header `Authorization: Basic YWRtaW46MTIzNDU=`  
       (đây là `admin:12345` encode base64).  
     - Nếu sai user/pass → báo lỗi 403.

3. **Test Cookie Authentication**
   - **Login**: POST `http://localhost:3001/login`
     - Body (JSON):
       ```json
       { "username": "admin", "password": "12345" }
       ```
     - Trả về cookie `auth_cookie_token` + lưu vào MongoDB.
   - **Profile**: GET `http://localhost:3001/profile`
     - Dùng cookie từ bước login.
   - **Logout**: POST `http://localhost:3001/logout`
     - Xóa cookie ở trình duyệt và trong MongoDB.

---

## 📸 Kết Quả Test (Screenshots)

### 🔹 Basic Auth
- Public route:  
  ![Public](./public/results/public.png)

- Secure route (có auth):  
  ![Secure](./public/results/secure.png)

- Login:  
  ![Login](./public/results/login.png)

- Profile:  
  ![Profile](./public/results/profile.png)

- Logout:  
  ![Logout](./public/results/logout.png)

### 🔹 Cookie Auth + MongoDB
- Login (Postman):  
  ![Cookie Login](./public/results/cookie_postman_login.png)

- Logout (Postman):  
  ![Cookie Logout](./public/results/cookie_postman_logout.png)

- MongoDB sau login:  
  ![Mongo Login](./public/results/coookie_mongo_login.png)

- MongoDB sau logout:  
  ![Mongo Logout](./public/results/coookie_mongo_logout.png)
