# gas-management-system


## Mục lục
1. [Mục Tiêu Dự Án](#mục-tiêu-dự-án)
2. [Công Nghệ Sử Dụng](#công-nghệ-sử-dụng)
   - [Backend (API Server)](#backend-api-server)
   - [Frontend (Website Dashboard)](#frontend-website-dashboard)
   - [Công Cụ Hỗ Trợ](#công-cụ-hỗ-trợ)
3. [Cấu Trúc Database](#cấu-trúc-database)
   - [Bảng SanPham](#bảng-sanpham-sản-phẩm)
   - [Bảng TaiKhoan](#bảng-taikhoan-tài-khoản)
   - [Bảng DonHang](#bảng-donhang-đơn-hàng)
   - [Bảng UuDai](#bảng-uudai-ưu-đãi)
   - [Bảng GioHang](#bảng-giohang-giỏ-hàng)
   - [Bảng DanhGia](#bảng-danhgia-đánh-giá)
4. [Hướng Đi Cụ Thể](#hướng-đi-cụ-thể)
5. [Tài Nguyên Cần Thiết](#tài-nguyên-cần-thiết)
6. [Mô Tả Cây Thư Mục](#mô-tả-cây-thư-mục)
7. [Tài Liệu](#tài-liệu)



1. Mục Tiêu Dự Án
 -  Mục tiêu chính: Xây dựng một hệ thống Website quản lý bán gas dân dụng, bao gồm:
   +  Quản lý sản phẩm (gas).
   +  Quản lý tài khoản người dùng (khách hàng, nhân viên, quản trị viên).
   +  Quản lý đơn hàng và thanh toán.
   +  Quản lý ưu đãi và khuyến mãi.
   +  Quản lý giỏ hàng và đánh giá sản phẩm.
 -  Đối tượng sử dụng:
   +  Khách hàng: Đặt hàng, theo dõi đơn hàng, đánh giá sản phẩm.
   +  Nhân viên: Quản lý đơn hàng, cập nhật trạng thái giao hàng.
   +  Quản trị viên: Quản lý sản phẩm, tài khoản, ưu đãi, và thống kê doanh thu.
________________________________________
2. Công Nghệ Sử Dụng
Backend (API Server)
 -  Ngôn ngữ: Node.js (JavaScript/TypeScript).
 -  Framework: Express.js.
 -  Cơ sở dữ liệu: MySQL.
 -  ORM: Sequelize (để tương tác với MySQL).
 -  Xác thực: JWT (JSON Web Token) cho đăng nhập và phân quyền.
 -  API Documentation: Swagger.
Frontend (Website Dashboard)
 -  Ngôn ngữ: JavaScript.
 -  Framework: React.js (hoặc Vue.js nếu bạn thích).
 -  UI Library: Material-UI hoặc Ant Design.
 -  State Management: Redux hoặc Context API.
 -  API Client: Axios.
Công Cụ Hỗ Trợ
 -  Version Control: Git (GitHub/GitLab).
 -  CI/CD: GitHub Actions hoặc Jenkins.
 -  Hosting: AWS, Google Cloud, hoặc Vercel (cho frontend), Heroku hoặc DigitalOcean (cho backend).
 -  Monitoring: Sentry (theo dõi lỗi).
________________________________________
3. Cấu Trúc Database
Dựa trên các bảng bạn đã cung cấp, tôi sẽ mô tả chi tiết từng bảng và mối quan hệ giữa chúng:
Bảng SanPham (Sản phẩm)
 -  Mục đích: Lưu trữ thông tin sản phẩm gas.
 -  Các trường:
   +  MaSP (Primary Key): Mã sản phẩm.
   +  TenSP: Tên sản phẩm.
   +  MoTa: Mô tả sản phẩm.
   +  Gia: Giá sản phẩm.
   +  SoLuong: Số lượng tồn kho.
   +  TrangThai: Trạng thái sản phẩm (ví dụ: "Còn hàng", "Hết hàng").
   +  HinhAnh: Đường dẫn hình ảnh sản phẩm.
Bảng TaiKhoan (Tài khoản)
 -  Mục đích: Lưu trữ thông tin người dùng (khách hàng, nhân viên, quản trị viên).
 -  Các trường:
   +  MaTK (Primary Key): Mã tài khoản.
   +  HoTen: Họ và tên.
   +  Email: Email (duy nhất).
   +  MatKhau: Mật khẩu (đã được mã hóa).
   +  SDT: Số điện thoại.
   +  DiaChi: Địa chỉ.
   +  VaiTro: Vai trò (ví dụ: "Khách hàng", "Nhân viên", "Quản trị viên").
   +  TrangThai: Trạng thái tài khoản (ví dụ: "Hoạt động", "Khóa").
Bảng DonHang (Đơn hàng)
 -  Mục đích: Lưu trữ thông tin đơn hàng.
 -  Các trường:
   +  MaDH (Primary Key): Mã đơn hàng.
   +  MaTK: Mã tài khoản (khách hàng đặt hàng).
   +  NgayDat: Ngày đặt hàng.
   +  TongTien: Tổng tiền đơn hàng.
   +  TrangThai: Trạng thái đơn hàng (ví dụ: "Chờ xử lý", "Đang giao", "Hoàn thành").
   +  DiaChiGiao: Địa chỉ giao hàng.
   +  MaUD: Mã ưu đãi (nếu có).
Bảng UuDai (Ưu đãi)
 -  Mục đích: Lưu trữ thông tin ưu đãi/khuyến mãi.
 -  Các trường:
   +  MaUD (Primary Key): Mã ưu đãi.
   +  TenUD: Tên ưu đãi.
   +  MucGiam: Mức giảm giá (ví dụ: 10%).
   +  NgayBatDau: Ngày bắt đầu ưu đãi.
   +  NgayKetThuc: Ngày kết thúc ưu đãi.
   +  TrangThai: Trạng thái ưu đãi (ví dụ: "Đang áp dụng", "Hết hạn").
Bảng GioHang (Giỏ hàng)
 -  Mục đích: Lưu trữ thông tin giỏ hàng của khách hàng.
 -  Các trường:
   +  MaGH (Primary Key): Mã giỏ hàng.
   +  MaTK: Mã tài khoản (khách hàng).
   +  MaSP: Mã sản phẩm.
   +  SoLuong: Số lượng sản phẩm trong giỏ.
   +  NgayThem: Ngày thêm sản phẩm vào giỏ.
Bảng DanhGia (Đánh giá)
 -  Mục đích: Lưu trữ thông tin đánh giá sản phẩm của khách hàng.
 -  Các trường:
   +  MaDG (Primary Key): Mã đánh giá.
   +  MaTK: Mã tài khoản (khách hàng).
   +  MaSP: Mã sản phẩm.
   +  Diem: Điểm đánh giá (từ 0 đến 5).
   +  NhanXet: Nhận xét của khách hàng.
   +  NgayDanhGia: Ngày đánh giá.
________________________________________
4. Hướng Đi Cụ Thể
Giai Đoạn 1: Thiết Lập Cơ Bản
 -  Thiết lập dự án Node.js với Express.js.
 -  Kết nối MySQL và cấu hình Sequelize.
 -  Tạo các model tương ứng với các bảng đã thiết kế.
 -  Triển khai API cơ bản (CRUD) cho các bảng:
   +  Sản phẩm.
   +  Tài khoản.
   +  Đơn hàng.
   +  Ưu đãi.
   +  Giỏ hàng.
   +  Đánh giá.
Giai Đoạn 2: Phát Triển Frontend
 -  Thiết lập dự án React.js.
 -  Tích hợp API từ backend.
 -  Xây dựng các trang:
   +  Trang chủ (hiển thị sản phẩm).
   +  Trang quản lý đơn hàng.
   +  Trang quản lý sản phẩm.
   +  Trang quản lý tài khoản.
   +  Trang quản lý ưu đãi.
Giai Đoạn 3: Hoàn Thiện và Kiểm Thử
 -  Triển khai xác thực và phân quyền (JWT).
 -  Viết unit test và integration test.
 -  Triển khai CI/CD.
 -  Tối ưu hóa hiệu suất và bảo mật.
________________________________________
5. Tài Nguyên Cần Thiết
 -  Nhân lực:
   +  Backend Developer (Node.js, MySQL).
   +  Frontend Developer (React.js).
   +  QA Tester.
 -  Công cụ:
   +  MySQL Workbench (quản lý database).
   +  Postman (kiểm thử API).
   +  Visual Studio Code (IDE).


________________________________________
6. Mô Tả Cây Thư Mục
gas-management-system/
│
├── backend/                  # Thư mục chứa mã nguồn backend (API server)
│   ├── config/               # Cấu hình kết nối cơ sở dữ liệu, biến môi trường
│   │   ├── db.js             # Cấu hình kết nối cơ sở dữ liệu
│   │   └── auth.js           # Cấu hình xác thực
│   ├── controllers/          # Các controller xử lý logic nghiệp vụ
│   │   ├── authController.js # Controller xử lý đăng nhập, đăng ký
│   │   ├── userController.js # Controller quản lý người dùng
│   │   ├── orderController.js# Controller quản lý đơn hàng
│   │   ├── gasController.js  # Controller quản lý sản phẩm gas
│   │   ├── paymentController.js # Controller quản lý thanh toán
│   │   └── deliveryController.js # Controller quản lý giao hàng
│   ├── models/               # Các model (schema) của cơ sở dữ liệu
│   │   ├── User.js           # Model người dùng
│   │   ├── Order.js          # Model đơn hàng
│   │   ├── Gas.js            # Model sản phẩm gas
│   │   ├── Payment.js        # Model thanh toán
│   │   └── Delivery.js       # Model giao hàng
│   ├── routes/               # Các route (định tuyến) API
│   │   ├── authRoutes.js     # Route cho xác thực
│   │   ├── userRoutes.js     # Route cho quản lý người dùng
│   │   ├── orderRoutes.js    # Route cho quản lý đơn hàng
│   │   ├── gasRoutes.js      # Route cho quản lý sản phẩm gas
│   │   ├── paymentRoutes.js  # Route cho thanh toán
│   │   └── deliveryRoutes.js # Route cho giao hàng
│   ├── middleware/           # Các middleware xử lý logic trung gian
│   │   ├── authMiddleware.js # Middleware xác thực
│   │   └── errorHandler.js   # Middleware xử lý lỗi
│   ├── services/             # Các service xử lý logic nghiệp vụ phức tạp
│   │   ├── authService.js    # Service xử lý đăng nhập, đăng ký
│   │   ├── userService.js    # Service quản lý người dùng
│   │   ├── orderService.js   # Service quản lý đơn hàng
│   │   ├── gasService.js     # Service quản lý sản phẩm gas
│   │   ├── paymentService.js # Service quản lý thanh toán
│   │   └── deliveryService.js # Service quản lý giao hàng
│   ├── utils/                # Các tiện ích hỗ trợ
│   │   ├── logger.js         # Tiện ích ghi log
│   │   └── emailSender.js    # Tiện ích gửi email
│   ├── app.js                # File chính của ứng dụng backend
│   └── server.js             # File khởi chạy server
│
├── frontend/                 # Thư mục chứa mã nguồn frontend (website dashboard)
│   ├── public/               # Các file tĩnh (CSS, JS, hình ảnh)
│   │   ├── css/              # File CSS
│   │   ├── js/               # File JavaScript
│   │   └── images/           # Hình ảnh
│   ├── src/                  # Mã nguồn frontend
│   │   ├── components/       # Các component UI
│   │   │   ├── Header.js     # Component header
│   │   │   ├── Footer.js     # Component footer
│   │   │   ├── Sidebar.js    # Component sidebar
│   │   │   └── ...           # Các component khác
│   │   ├── pages/            # Các trang của ứng dụng
│   │   │   ├── Home.js       # Trang chủ
│   │   │   ├── Orders.js     # Trang quản lý đơn hàng
│   │   │   ├── Products.js   # Trang quản lý sản phẩm
│   │   │   ├── Users.js      # Trang quản lý người dùng
│   │   │   ├── Payments.js   # Trang quản lý thanh toán
│   │   │   └── Deliveries.js # Trang quản lý giao hàng
│   │   ├── services/         # Các service gọi API từ backend
│   │   │   ├── api.js        # Service gọi API chung
│   │   │   ├── authService.js # Service xử lý đăng nhập, đăng ký
│   │   │   ├── orderService.js # Service quản lý đơn hàng
│   │   │   └── ...           # Các service khác
│   │   ├── App.js            # Component chính của ứng dụng
│   │   └── index.js          # File khởi chạy ứng dụng frontend
│   ├── package.json          # File quản lý dependencies và scripts
│   └── README.md             # Hướng dẫn sử dụng và cài đặt
│
├── database/                 # Thư mục chứa các script và cấu trúc cơ sở dữ liệu
│   ├── migrations/           # Các file migration để tạo và cập nhật cơ sở dữ liệu
│   ├── seeds/                # Các file seed để thêm dữ liệu mẫu vào cơ sở dữ liệu
│   └── schema.sql            # File chứa cấu trúc cơ sở dữ liệu
│
├── docs/                     # Thư mục chứa tài liệu dự án
│   ├── requirements/         # Tài liệu yêu cầu hệ thống
│   ├── design/               # Tài liệu thiết kế hệ thống
│   └── api-docs/             # Tài liệu API
│
├── tests/                    # Thư mục chứa các test case
│   ├── unit/                 # Test case đơn vị
│   ├── integration/          # Test case tích hợp
│   └── e2e/                  # Test case end-to-end
│
├── .env                      # File chứa các biến môi trường
├── .gitignore                # File bỏ qua các file không cần đẩy lên git
├── package.json              # File quản lý dependencies và scripts