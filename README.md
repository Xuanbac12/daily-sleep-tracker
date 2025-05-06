
# 💤 Daily Sleep Tracker

> Ứng dụng giúp người dùng **ghi lại** và **phân tích thói quen giấc ngủ** một cách trực quan, bao gồm hệ thống backend bằng Spring Boot và frontend bằng ReactJS.

---

## 📦 Tổng quan hệ thống

| Thành phần   | Mô tả |
|--------------|------|
| `backend/`   | Xây dựng bằng **Java Spring Boot**, cung cấp các API REST, xác thực người dùng bằng JWT, lưu trữ dữ liệu vào MySQL |
| `frontend/`  | Xây dựng bằng **ReactJS**, cho phép người dùng nhập bản ghi giấc ngủ, xem biểu đồ phân tích và quản lý tài khoản |

---

## 🚀 Tính năng nổi bật

### ✅ Backend (Spring Boot)
- 🧑 Đăng ký và đăng nhập người dùng với xác thực JWT
- 🛌 API thêm bản ghi ngủ mỗi ngày (giờ ngủ, giờ dậy)
- 📈 Phân tích thời gian ngủ theo tuần
- 🔐 Phân quyền bảo mật API với Spring Security
- 📄 RESTful API chuẩn hóa

### 🎨 Frontend (ReactJS)
- Giao diện hiện đại, dễ sử dụng
- Form nhập dữ liệu giấc ngủ với date/time picker
- Biểu đồ hiển thị giờ ngủ mỗi ngày
- Phân tích thời gian ngủ trung bình theo tuần
- Responsive UI hỗ trợ điện thoại và máy tính

---

## 🛠 Công nghệ sử dụng

| Công nghệ         | Backend                        | Frontend                    |
|------------------|--------------------------------|-----------------------------|
| Ngôn ngữ         | Java 21                       | JavaScript (React)          |
| Framework        | Spring Boot 3.4.4              | ReactJS + Vite              |
| Bảo mật          | Spring Security + JWT          | JWT (decode + localStorage) |
| Cơ sở dữ liệu     | MySQL                          | -                           |
| ORM              | Spring Data JPA                | -                           |
| UI               | -                              | Material UI + Recharts      |
| Công cụ build     | Maven                          | npm                         |

---

## 📁 Cấu trúc thư mục chính

```text
daily-sleep-tracker/
├── backend/                  # Dự án Spring Boot (API & DB)
│   └── src/...
├── frontend/                 # Dự án ReactJS (UI người dùng)
│   └── src/...
└── README.md                 # Tài liệu mô tả dự án
```

---

## ⚙️ Cấu hình và chạy dự án

### 1. Cài đặt MySQL

Tạo CSDL tên `sleep_tracker`:

```sql
CREATE DATABASE sleep_tracker;
```

### 2. Cấu hình backend (`application.properties`)

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/sleep_tracker
spring.datasource.username=root
spring.datasource.password=
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQLDialect
```

---

## ▶️ Hướng dẫn chạy dự án

### 📦 Backend (Spring Boot)

```bash
cd backend
./mvnw spring-boot:run
```

Hoặc chạy bằng IntelliJ → mở `BackendApplication.java` → Run

### 🌐 Frontend (ReactJS)

```bash
cd frontend
npm install
npm run dev
```

Truy cập tại: `http://localhost:5173/`

> 💡 Đảm bảo chỉnh `VITE_API_BASE_URL` trong `.env` nếu cần:
```env
VITE_API_BASE_URL=http://localhost:8080/api
=======

# 💤 Daily Sleep Tracker - Frontend

Đây là giao diện người dùng của ứng dụng **Daily Sleep Tracker**, cho phép người dùng ghi lại thời gian ngủ và phân tích thói quen ngủ hằng tuần. Dự án được phát triển bằng **React.js**.

---

## 📷 Giao diện chính

- Trang chào mừng (Splash Screen)
- Đăng ký / Đăng nhập người dùng
- Giao diện thêm bản ghi giấc ngủ (ngày, giờ ngủ, giờ thức)
- Biểu đồ trực quan hóa thời gian ngủ
- Bảng phân tích thói quen ngủ hằng tuần

---

## 🧩 Cấu trúc thư mục

```bash
src/
├── Home/              # Giao diện trang chính (biểu đồ, bảng, dialog nhập)
│   ├── Home.jsx
│   ├── SleepChart.jsx
│   ├── SleepTable.jsx
│   └── NewEntryDialog.jsx
│
├── Navbar/            # Thanh điều hướng
│   └── Navbar.jsx
│
├── Signin/            # Giao diện đăng nhập
│   └── Signin.jsx
│
├── Signup/            # Giao diện đăng ký
│   └── Signup.jsx
│
├── SleepAnalysis/     # Phân tích thói quen ngủ theo tuần
│   └── SleepAnalysis.jsx
│
├── SplashScreen/      # Màn hình chào ban đầu
│   └── SplashScreen.jsx
│
├── utils/             # Tiện ích như cấu hình axios
│   └── axiosInstance.js
│
├── App.js             # Cấu hình router chính
└── index.js           # Điểm bắt đầu ứng dụng
```

---

## 🚀 Cài đặt & Chạy dự án

```bash
# 1. Clone dự án
git clone https://github.com/Xuanbac12/daily-sleep-tracker-fontend.git
cd daily-sleep-tracker-fontend

# 2. Cài đặt thư viện
npm install

# 3. Chạy ứng dụng
npm start
>>>>>>> e00b64d (Squashed 'frontend/' content from commit c583269)
```

---


## 🔐 Bảo mật & JWT

- Người dùng đăng nhập nhận JWT token
- Token lưu trong `localStorage` và gửi qua header `Authorization`
- Backend kiểm tra token bằng `JwtFilter.java`

| Class                      | Mô tả                             |
|----------------------------|-----------------------------------|
| `SecurityConfig.java`      | Cấu hình phân quyền truy cập      |
| `JwtUtil.java`             | Tạo và kiểm tra token             |
| `JwtFilter.java`           | Lọc & xác thực JWT                |
| `UserDetailsServiceImpl.java` | Tải người dùng từ DB          |
| `SecurityBeans.java`       | Cấu hình mã hoá `PasswordEncoder` |

---

## 📊 Giao diện chính (Demo)

| Tính năng       | Giao diện                  |
|------------------|-----------------------------|
| Nhập giờ ngủ     | ✅ Date/Time Picker          |
| Biểu đồ ngủ       | ✅ Recharts BarChart         |
| Phân tích tuần   | ✅ Trung bình, <6h, >8h      |

---

## 🧪 Testing

- `spring-boot-starter-test`
- `spring-security-test`
- `BackendApplicationTests.java`
=======
## 🔧 Các thư viện sử dụng

- `react` – Thư viện UI chính
- `@mui/material` – Giao diện đẹp, dễ dùng (Material UI)
- `@mui/icons-material` – Thư viện icon MUI
- `chart.js`, `react-chartjs-2` – Biểu đồ trực quan
- `axios` – Gửi request đến backend

---

## 📡 Kết nối backend

Ứng dụng frontend này cần kết nối với backend (Spring Boot). Cập nhật địa chỉ trong file:

```js
// src/utils/axiosInstance.js
axios.defaults.baseURL = "http://localhost:8080/api"; // hoặc domain thật khi deploy
```

---

## 🤝 Đóng góp

Chúng tôi hoan nghênh mọi đóng góp!  
Vui lòng tạo branch mới trước khi commit:

```bash
git checkout -b feature/your-feature-name
```

---

## 📄 Giấy phép

Dự án được phát hành theo giấy phép **MIT License**.
>>>>>>> e00b64d (Squashed 'frontend/' content from commit c583269)

---

## 👤 Tác giả


- GitHub: [@Xuanbac12](https://github.com/Xuanbac12)
- Dự án phát triển phục vụ học tập và nâng cao kỹ năng lập trình Fullstack.

---

## 📄 License

Dự án mã nguồn mở, sử dụng cho mục đích học tập và phi thương mại.
=======
- **Xuanbac12** - [GitHub](https://github.com/Xuanbac12)

>>>>>>> e00b64d (Squashed 'frontend/' content from commit c583269)
