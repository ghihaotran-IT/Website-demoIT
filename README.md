# THTech Web Application — Hệ Thống Quản Lý Bán Hàng, Kho Hàng & Dịch Vụ Kỹ Thuật

![ASP.NET](https://img.shields.io/badge/ASP.NET-WebForms-512BD4?style=for-the-badge&logo=.net&logoColor=white)
![C#](https://img.shields.io/badge/C%23-10.0-239120?style=for-the-badge&logo=c-sharp&logoColor=white)
![MSSQL](https://img.shields.io/badge/SQL_Server-2019+-CC292B?style=for-the-badge&logo=microsoftsqlserver&logoColor=white)
![Architecture](https://img.shields.io/badge/Architecture-DAO_Pattern-00599C?style=for-the-badge)

**THTech Web Application** là hệ thống phần mềm quản lý toàn diện dành cho doanh nghiệp kinh doanh thiết bị công nghệ (Camera quan sát, Đèn năng lượng mặt trời, Linh kiện máy tính, Thiết bị mạng, Điện gia dụng). Hệ thống tích hợp đa kênh bán hàng (**B2C E-Commerce, Thu ngân POS tại quầy, Bán buôn B2B**), quản lý kho theo **Số Serial vật lý**, bảo hành, dịch vụ sửa chữa, chấm công IP và quản trị nhân sự - bảng lương.

---

## 📑 Mục Lục
- [✨ Tính Năng Nổi Bật](#-tính-năng-nổi-bật)
- [👥 Phân Quyền & Vai Trò Người Dùng](#-phân-quyền--vai-trò-người-dùng)
- [📦 Kiến Trúc Hệ Thống & Cấu Trúc Mã Nguồn](#-kiến-trúc-hệ-thống--cấu-trúc-mã-nguồn)
- [🗄️ Cơ Sở Dữ Liệu & Stored Procedures](#-cơ-sở-dữ-liệu--stored-procedures)
- [🛠️ Hướng Dẫn Cài Đặt & Vận Hành](#%EF%B8%8F-hướng-dẫn-cài-đặt--vận-hành)

---

## ✨ Tính Năng Nổi Bật

### 1. 🛒 Cổng Thông Tin & Thương Mại Điện Tử B2C
* **Trang chủ & Slider Khuyến mãi:** Tự động hiển thị Banner Voucher ưu đãi đang kích hoạt, slider sản phẩm nổi bật (`Default.aspx.cs`).
* **Lọc & Tìm kiếm sản phẩm nâng cao:** Mega Menu theo ngành hàng (An ninh, Năng lượng, Máy tính, Gia dụng) kết hợp AJAX lọc theo Thương hiệu, Khoảng giá, Từ khóa (`Site.master.cs`, `Default.aspx.cs`).
* **Chi tiết Sản phẩm & Thuộc tính:** Hiển thị thông số kỹ thuật, album ảnh sản phẩm, tình trạng kho theo thuộc tính (Màu sắc, Dung lượng, Công suất) và tem nhãn HOT/NEW (`ChiTietSanPham.aspx.cs`).
* **Giỏ hàng & Khuyến mãi:** Tự động kiểm tra tồn kho real-time, áp dụng mã voucher giảm giá (theo % hoặc số tiền cố định), tính năng mua lại đơn hàng cũ (`GioHang.aspx.cs`, `LichSuDonHang.aspx.cs`).
* **Thanh toán trực tuyến:** Hỗ trợ nhiều phương thức (COD, Chuyển khoản QR), tự động phân vùng phí ship và chặn tài khoản đại lý B2B đặt nhầm qua luồng bán lẻ (`ThanhToan.aspx.cs`).
* **Sổ đơn hàng & Yêu cầu dịch vụ:** Khách hàng theo dõi tiến độ giao hàng, tải hóa đơn điện tử, gửi yêu cầu bảo hành đính kèm ảnh chụp thực tế hoặc gửi phiếu sửa chữa dịch vụ riêng (`LichSuDonHang.aspx.cs`, `DichVuRieng.aspx.cs`).

### 2. 💻 Bán Hàng Tại Quầy (POS - Point of Sale)
* **Quét mã vạch & Quản lý Serial:** Quét Số Serial duy nhất hoặc SKU để chọn sản phẩm chính xác từ kho (`POS.aspx.cs`).
* **Xử lý đa hóa đơn song song:** Cơ chế giữ chỗ Serial thông minh, ngăn chặn quét trùng 1 Serial trên nhiều tab thu ngân đang mở.
* **Thanh toán nhanh & Kích hoạt bảo hành:** Tự động tính giá niêm yết từ DB, chốt đơn tại quầy và kích hoạt ngay thời hạn bảo hành cho sản phẩm bán ra (`POS.aspx.cs`).

### 3. 🤝 Quản Lý Bán Buôn & Đại Lý B2B (Business-to-Business)
* **Hồ sơ Đại lý & Chiết khấu:** Quản lý danh mục Đại lý, Thợ lắp đặt, thiết lập tỷ lệ chiết khấu riêng (%) và Hạn mức công nợ (`QuanLyDoiTac.aspx.cs`).
* **Lên đơn B2B chuyên biệt:** Giao diện quét hàng tự động tính giá sau chiết khấu đại lý, kiểm tra hạn mức nợ còn lại và ghi nhận công nợ tự động.
* **Phiếu thu & Cấn trừ công nợ:** Lập phiếu thu tiền theo từng đơn hàng hoặc thu nợ tổng hợp, tự động giảm tổng nợ hiện tại (`sp_Admin_B2B_InsertPhieuThu`).
* **In hóa đơn B2B:** Mẫu hóa đơn B2B chuẩn hóa hiển thị Tên đại lý, Mã số thuế, tỷ lệ chiết khấu và mô tả hợp đồng (`InHoaDonB2B.aspx.cs`).

### 4. 🏬 Quản Lý Kho Hàng & Số Serial Vật Lý
* **Quản lý kho chi tiết theo Serial:** Theo dõi chính xác từng đơn vị sản phẩm trong kho bằng Serial/Barcode, trạng thái (`Trong kho`, `Đã bán`) (`TonKho.aspx.cs`).
* **Nhập kho & Nhà phân phối:** Quản lý danh sách Nhà phân phối (NPP), lập phiếu nhập hàng, gán dải Serial vật lý vào phiếu nhập (`PhieuNhap.aspx.cs`).
* **Thêm / Xóa Serial hàng loạt:** Công cụ sinh mã Serial tự động theo quy tắc `MaSP-ThuocTinh-Index`, hỗ trợ xóa Serial theo dải an toàn (`TonKho.aspx.cs`).
* **Báo cáo tồn kho & Cảnh báo:** Đèn cảnh báo tồn kho (`Sắp hết`, `Hết hàng`), biểu đồ phân bổ tồn kho theo Thương hiệu và Danh mục, xuất báo cáo Excel/CSV (`BaoCaoTonKho.aspx.cs`).

### 5. 🛠️ Quản Lý Bảo Hành & Dịch Vụ Kỹ Thuật
* **Tiếp nhận & Xử lý bảo hành:** Quản lý danh sách yêu cầu bảo hành từ khách hàng B2C/B2B, kiểm tra hình ảnh lỗi, cập nhật phản hồi và trạng thái xử lý (`QuanLyBaoHanh.aspx.cs`).
* **Quản lý Dịch vụ sửa chữa:** Tiếp nhận thiết bị hư hỏng (trong kho hoặc ngoài kho), phân công Kỹ thuật viên nội bộ hoặc Thợ lắp đặt đối tác, theo dõi chi phí sửa chữa (`QuanLyDichVu.aspx.cs`).

### 6. 👷 Quản Lý Nhân Sự, Chấm Công & Bảng Lương
* **Chấm công tự động qua IP:** Tự động Check-in khi nhân viên truy cập hệ thống lần đầu trong ngày, ghi nhận địa chỉ IP khách và duy trì trạng thái Online (`AdminMaster.master.cs`, `ChamCong.aspx.cs`).
* **Duyệt & Điều chỉnh giờ công:** Quản trị viên duyệt giờ công hàng loạt, điều chỉnh giờ vào/ra có lưu vết lý do đối soát (`ChamCong.aspx.cs`).
* **Tính lương & Đánh giá KPI:** Tính bảng lương thực lĩnh dựa trên giờ công đã duyệt (Lương cố định hoặc Lương theo giờ), đánh giá KPI nhân sự qua số đơn chốt, số phiếu dịch vụ hoàn thành và doanh số mang về. Export file Excel bảng lương chuẩn tiếng Việt (`NhanVien.aspx.cs`).

### 7. 📊 Báo Cáo & Quản Trị Hệ Thống (Dashboard & Analytics)
* **Dashboard trực quan:** Thống kê doanh thu tháng, tỷ lệ hoàn thành mục tiêu, số lượng đơn hàng mới, thông báo khẩn cấp (`Dashboard.aspx.cs`).
* **Báo cáo doanh thu đa kênh:** Phân tích Gross Revenue, Net Revenue, AOV, tỷ lệ hủy đơn, so sánh doanh thu các kênh (Web, POS, B2B) và doanh số từng thu ngân (`BaoCaoDoanhThu.aspx.cs`).
* **Cấu hình & Khuyến mãi:** Thiết lập thông tin cửa hàng, tài khoản cá nhân, quản lý mã voucher và banner quảng cáo trên trang chủ (`CaiDat.aspx.cs`, `QuanLyVoucher.aspx.cs`).

---

## 👥 Phân Quyền & Vai Trò Người Dùng

Hệ thống xây dựng cơ chế phân quyền RBAC (Role-Based Access Control) chặt chẽ:

| Vai trò (Role) | Mô tả & Quyền hạn |
| :--- | :--- |
| 🔴 **Admin** | Quyền hạn tối cao: Quản lý toàn bộ hệ thống, Nhân sự, Bảng lương, Chấm công, Cài đặt cửa hàng, Báo cáo doanh thu, Cấu hình danh mục và phân quyền. |
| 🔵 **Staff** | Nhân viên kinh doanh/kho: Quản lý đơn hàng, Kho hàng, Phiếu nhập, Bảo hành, Dịch vụ, Đối tác B2B và xem báo cáo tồn kho/doanh thu. |
| 🟢 **Cashier** | Thu ngân: Sử dụng hệ thống bán hàng POS tại quầy, chốt đơn B2C/B2B, lập phiếu thu công nợ, quản lý danh sách đơn hàng. |
| 🟡 **Technician** | Kỹ thuật viên: Tiếp nhận và xử lý các phiếu dịch vụ sửa chữa, bảo hành thiết bị được phân công. |
| ⚪ **Customer** | Khách hàng mua lẻ / Đại lý: Đăng ký, đăng nhập, tìm kiếm sản phẩm, đặt hàng B2C, quản lý lịch sử đơn hàng, gửi yêu cầu bảo hành / dịch vụ. |

---

## 📦 Kiến Trúc Hệ Thống & Cấu Trúc Mã Nguồn

```text
THTech_WebApplication/
├── DAO/                        # Layer kết nối dữ liệu
│   └── DataProvider.cs         # Pattern Singleton thực thi Stored Procedures ADO.NET
├── Admin/                      # Phân hệ Quản trị & Vận hành (Admin MasterPage)
│   ├── AdminMaster.master.cs   # Layout MasterPage Admin, Phân quyền menu, Heartbeat & Check-in
│   ├── Dashboard.aspx.cs       # Bảng điều khiển trung tâm & Chỉ số KPI
│   ├── BaoCaoDoanhThu.aspx.cs  # Báo cáo doanh thu đa kênh & Xuất Excel/CSV
│   ├── BaoCaoTonKho.aspx.cs   # Báo cáo tồn kho & Cảnh báo hết hàng
│   ├── POS.aspx.cs             # Giao diện bán hàng thu ngân tại quầy
│   ├── TonKho.aspx.cs          # Quản lý kho theo Số Serial vật lý
│   ├── PhieuNhap.aspx.cs       # Quản lý Phiếu nhập & Nhà phân phối
│   ├── QuanLyDoiTac.aspx.cs    # Quản lý Đại lý B2B & Công nợ
│   ├── DonHang.aspx.cs         # Quản lý & Đối soát đơn hàng
│   ├── QuanLyBaoHanh.aspx.cs   # Tiếp nhận & Xử lý bảo hành
│   ├── QuanLyDichVu.aspx.cs    # Quản lý phiếu sửa chữa & Phân công KTV
│   ├── ChamCong.aspx.cs        # Duyệt giờ công & Lịch sử chấm công IP
│   ├── NhanVien.aspx.cs        # Quản lý nhân sự, Tính bảng lương & Xuất KPI
│   ├── NguoiDung.aspx.cs       # Quản lý tài khoản khách hàng
│   ├── SanPham.aspx.cs         # Quản lý sản phẩm & Album hình ảnh
│   ├── HangSanXuat.aspx.cs     # Quản lý thương hiệu / hãng sản xuất
│   ├── QuanLyVoucher.aspx.cs   # Quản lý mã giảm giá & Banner khuyến mãi
│   └── CaiDat.aspx.cs          # Cài đặt cá nhân & Thông tin cửa hàng
├── Web B2C Portal/             # Phân hệ Khách hàng (Site MasterPage)
│   ├── Site.master.cs          # Layout MasterPage Khách hàng & Mega Menu ngành hàng
│   ├── Default.aspx.cs         # Trang chủ, Hero Banner & AJAX lọc sản phẩm
│   ├── ChiTietSanPham.aspx.cs # Chi tiết sản phẩm, cấu hình & album ảnh
│   ├── GioHang.aspx.cs         # Giỏ hàng & Kiểm tra voucher
│   ├── ThanhToan.aspx.cs       # Thanh toán đơn hàng B2C
│   ├── InHoaDon.aspx.cs        # In hóa đơn bán lẻ B2C
│   ├── InHoaDonB2B.aspx.cs     # In hóa đơn bán buôn B2B
│   ├── LichSuDonHang.aspx.cs   # Lịch sử mua hàng, Đổi trả & Gửi yêu cầu bảo hành
│   ├── DichVuRieng.aspx.cs     # Gửi yêu cầu sửa chữa thiết bị ngoài kho
│   ├── Wishlist.aspx.cs        # Danh sách sản phẩm yêu thích
│   └── TaiKhoan.aspx.cs        # Đăng ký, Đăng nhập & Quên mật khẩu
└── Uploads / images / banner/  # Thư mục lưu trữ hình ảnh & tài liệu upload
```

---

## 🗄️ Cơ Sở Dữ Liệu & Stored Procedures

Hệ thống tối ưu hóa toàn bộ các thao tác xử lý nghiệp vụ thông qua **Stored Procedures** trên SQL Server, bảo đảm tính an toàn, toàn vẹn dữ liệu và hiệu năng cao:

* **Xử lý Đơn hàng & POS:** `sp_Web_CreateOrder`, `sp_Admin_QuickUpdateOrderStatus`, `sp_AutoKichHoatBaoHanh`, `sp_Admin_CancelOrderAdmin`.
* **Nghiệp vụ Kho Serial:** `sp_TonKho_GetSerialGrid`, `sp_TonKho_InsertSerial`, `sp_TonKho_DeleteSerial_Safe`, `sp_TonKho_GetListTheoSP`.
* **Nghiệp vụ B2B & Công nợ:** `sp_Admin_B2B_CreateOrder`, `sp_Admin_B2B_InsertPhieuThu`, `sp_B2B_GetInvoiceInfo`, `sp_Admin_B2B_UpsertDoiTac`.
* **Báo cáo & KPI:** `sp_B2C_Revenue_KPI`, `sp_B2C_Revenue_Chart`, `sp_Admin_GetNhanVienKPI`, `sp_Admin_GetBangLuong`, `sp_B2C_Stock_KPI`.
* **Chấm công & Tài khoản:** `sp_ChamCong_CheckIn`, `sp_ChamCong_CheckOut`, `sp_User_UpdateActivity`, `sp_Admin_ChamCong_DuyetHangLoat`.

---

## 🛠️ Hướng Dẫn Cài Đặt & Vận Hành

### 1. Yêu cầu Hệ thống
* **Server Environment:** Windows Server / Windows 10/11 với IIS (Internet Information Services)
* **Framework:** .NET Framework 4.8 hoặc phiên bản tương đương
* **Database:** Microsoft SQL Server 2019 trở lên

### 2. Cấu hình CSDL & Connection String
1. Thực thi các tệp kịch bản SQL (`.sql`) để khởi tạo Database `THTechDB` và toàn bộ Stored Procedures.
2. Mở tệp `Web.config` trong thư mục gốc dự án và cập nhật chuỗi kết nối:
   ```xml
   <connectionStrings>
     <add name="THTechDB" 
          connectionString="Data Source=YOUR_SERVER;Initial Catalog=THTechDB;Integrated Security=True;" 
          providerName="System.Data.SqlClient" />
   </connectionStrings>
   ```

### 3. Triển khai IIS
1. Mở IIS Manager, tạo một Application Pool mới chọn `.NET CLR Version v4.0`.
2. Tạo Web Application mới trỏ đến thư mục mã nguồn dự án.
3. Đảm bảo thư mục `Uploads/`, `images/`, `banner/` có quyền ghi (`Write`) cho tài khoản `IIS_IUSRS`.

---

<p align="center">
  <b>THTech Web Application</b> — Giải pháp quản trị bán hàng & vận hành công nghệ toàn diện.
</p>

