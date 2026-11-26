# TÀI LIỆU ĐẶC TẢ GIAO DIỆN & QUY TẮC HIỂN THỊ (WIREFRAME & UI LOGIC SPECIFICATION)

* **Tên dự án:** Nền tảng Thương mại Điện tử Quần Áo Nam (Men's Fashion E-Commerce)
* **Tác giả / IT Business Analyst:** Lưu Văn Hoàng
* **Màn hình trọng tâm:** Trang Chi Tiết Sản Phẩm (Product Detail Page - PDP)
* **Phiên bản:** v1.0
* **Trạng thái:** Bàn giao UI/UX Designer & Frontend Developer

---

## 1. MỤC ĐÍCH CỦA BÀI TOÁN BƯỚC 3

Trong quy trình phát triển phần mềm:
* **BA không phải là người vẽ đồ họa màu mè** (đó là việc của UI/UX Designer).
* **Nhiệm vụ của BA trong Bước 3:**
  1. Vẽ **Khung sườn bố cục (Low-fidelity Wireframe)**: Nút nào đặt ở đâu? Thông tin nào quan trọng nhất với khách nam?
  2. Đặc tả **Quy tắc hiển thị (UI Logic Rules)**: Bấm vào nút này thì màn hình đổi ra sao? Khi nào nút bị mờ không cho bấm?
  3. Xây dựng **Bảng ma trận dữ liệu biến thể (Color x Size x SKU)**: Giúp Lập trình viên thiết kế cơ sở dữ liệu (Database) chuẩn xác.

---

## 2. BẢNG MA TRẬN DỮ LIỆU BIẾN THỂ (PRODUCT VARIANT MATRIX)

Trong ngành thời trang, một sản phẩm cha (Parent Product: *Áo Polo Nam Classic*) sẽ phân nhánh thành nhiều mã sản phẩm con (**SKU - Stock Keeping Unit**):

| Mã SKU con | Tên biến thể | Màu sắc | Kích cỡ | Tồn kho thực tế | Trạng thái hiển thị trên Web |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `POLO-DEN-S` | Áo Polo Nam - Đen Nhám - Size S | Đen Nhám | S | 15 chiếc | Cho phép mua bình thường |
| `POLO-DEN-M` | Áo Polo Nam - Đen Nhám - Size M | Đen Nhám | M | 28 chiếc | Cho phép mua bình thường |
| `POLO-DEN-L` | Áo Polo Nam - Đen Nhám - Size L | Đen Nhám | L | **0 chiếc** | **Nút gạch chéo, không cho chọn** |
| `POLO-DEN-XL`| Áo Polo Nam - Đen Nhám - Size XL | Đen Nhám | XL | 8 chiếc | Cảnh báo *"Chỉ còn 8 chiếc"* |
| `POLO-XANH-S`| Áo Polo Nam - Xanh Navy - Size S | Xanh Navy | S | 20 chiếc | Cho phép mua bình thường |
| `POLO-XANH-M`| Áo Polo Nam - Xanh Navy - Size M | Xanh Navy | M | 35 chiếc | Cho phép mua bình thường |
| `POLO-XANH-L`| Áo Polo Nam - Xanh Navy - Size L | Xanh Navy | L | 18 chiếc | Cho phép mua bình thường |
| `POLO-XANH-XL`| Áo Polo Nam - Xanh Navy - Size XL| Xanh Navy | XL | 12 chiếc | Cho phép mua bình thường |

---

## 3. BỐ CỤC KHUNG SƯỜN MÀN HÌNH (WIREFRAME STRUCTURE)

Bố cục màn hình sản phẩm thời trang nam được thiết kế tối ưu cho trải nghiệm mua sắm nhanh của nam giới (Chia làm 2 cột chính):

```
+-----------------------------------------------------------------------------------------+
| [Thanh tìm kiếm quần áo nam]                          [Giỏ hàng (2)]   [Tài khoản]      |
+-----------------------------------------------------------------------------------------+
| [ CỘT TRÁI: HÌNH ẢNH MẪU THỰC TẾ ]     | [ CỘT PHẢI: THÔNG TIN & RA QUYẾT ĐỊNH MUA ]    |
|                                         |                                               |
|  +-----------------------------------+  |  ÁO POLO NAM CLASSIC PIQUE CO GIÃN 4 CHIỀU    |
|  |                                   |  |  Mã SP: #POLO-2026 | ⭐⭐⭐⭐⭐ (4.9 sao)       |
|  |     ẢNH MẪU MẶC THEO MÀU          |  |  Giá: 299.000 ₫ (Tiết kiệm 33%)               |
|  |     (Tỉ lệ chuẩn 3:4)             |  |  -------------------------------------------  |
|  |                                   |  |  MÀU SẮC: [Xanh Navy ✓]  [Đen Nhám]  [Trắng]  |
|  |                                   |  |  -------------------------------------------  |
|  +-----------------------------------+  |  CHỌN SIZE:  [ S ]  [ M ]  [ L ]  [ XL ]      |
|  [Ảnh 1]   [Ảnh 2]   [Ảnh 3]   [Ảnh 4]  |                                               |
|                                         |  +-----------------------------------------+  |
|                                         |  | 💡 TÍNH SIZE THÔNG MINH CHO BẠN:        |  |
|                                         |  | Chiều cao: [ 172 ] cm  Cân nặng: [ 68 ] kg|  |
|                                         |  | [ Nút: TÍNH SIZE CỦA TÔI ]              |  |
|                                         |  | &rarr; Gợi ý: Size L vừa vặn nhất (95%)    |  |
|                                         |  +-----------------------------------------+  |
|                                         |                                               |
|                                         |  [ 🛒 THÊM VÀO GIỎ ]   [ ⚡ MUA NGAY (1 CHẠM) ]|
+-----------------------------------------------------------------------------------------+
```

---

## 4. BẢNG ĐẶC TẢ CHI TIẾT CÁC NÚT & LOGIC NGHIỆP VỤ (FIELD SPECIFICATIONS)

Bảng này là tài liệu cốt lõi để bàn giao cho Lập trình viên Frontend (Dev giao diện):

| Tên thành phần trên màn hình | Loại điều khiển (Control) | Dữ liệu & Quy tắc hiển thị (Business Logic) |
| :--- | :--- | :--- |
| **Nút chọn Màu sắc** | Radio Button dạng Box | Bấm chọn màu nào &rarr; Hệ thống tự động thay thế toàn bộ album ảnh bên cột trái bằng ảnh chụp của màu đó. Cập nhật lại tồn kho của các nút Size. |
| **Nút chọn Kích cỡ (Size)** | Button đơn chọn | - Nếu SKU còn hàng: Bấm chọn bình thường (Viền xanh viền đậm).<br>- Nếu SKU = 0: Nút bị làm mờ, gạch chéo chéo, con trỏ chuột đổi thành `not-allowed`. |
| **Ô nhập Chiều cao** | Textbox định dạng số | Giới hạn số nguyên từ `140` đến `210` cm. Mặc định để placeholder: *"Vd: 170"*. Nếu gõ chữ &rarr; Tự động chặn không cho gõ. |
| **Ô nhập Cân nặng** | Textbox định dạng số | Giới hạn số nguyên từ `40` đến `130` kg. Mặc định để placeholder: *"Vd: 65"*. |
| **Nút "Tính Size của tôi"** | Action Button | Khi bấm &rarr; Gọi thuật toán tính toán BMI kết hợp phom áo. Hiển thị dòng đề xuất size trong 0.2 giây và **tự động tick chọn nút Size đó** ở mục chọn size phía trên. |
| **Nút "Mua ngay"** | Primary Button | Bấm &rarr; Bỏ qua bước vào giỏ hàng, chuyển thẳng đến màn hình Quét mã QR VNPay (One-step checkout), kích hoạt Soft-lock 15 phút. |

---

## 5. BỘ CÂU HỎI PHỎNG VẤN IT BA (DÀNH CHO LƯU VĂN HOÀNG)

> **Câu hỏi 1:** *"Theo em, điểm khác nhau lớn nhất giữa Wireframe của một BA và Wireframe của Designer là gì?"*  
> **Cách bạn trả lời:**  
> *"Dạ thưa anh/chị, Designer tập trung vào tính thẩm mỹ: màu sắc, độ bóng (shadow), font chữ và bố cục hài hòa. Còn Wireframe của BA tập trung vào **Logic nghiệp vụ và luồng xử lý thông tin**: nút này bấm thì dữ liệu gửi đi đâu, ô nhập có điều kiện ràng buộc gì, khi hết hàng thì giao diện phản ứng ra sao. Wireframe của BA là kim chỉ nam để Designer biết cần vẽ những màn hình và trạng thái nào, và để Dev biết logic kết nối dữ liệu."*

> **Câu hỏi 2:** *"Tại sao em lại tách bảng Ma trận biến thể (Color x Size x SKU) chi tiết như ở Mục 2?"*  
> **Cách bạn trả lời:**  
> *"Dạ, đối với ngành thời trang, nếu BA chỉ mô tả chung chung 'quần áo có size và màu' thì Lập trình viên Backend rất dễ thiết kế sai Database (chỉ lưu tồn kho trên sản phẩm cha). Việc em đặc tả rõ từng mã SKU con giúp Dev thiết kế chuẩn bảng `Product_Variants` và liên kết chính xác với phân hệ Quản lý kho (WMS), tránh việc bán âm hàng khi một size cụ thể bị hết."*

---

*Tài liệu Bước 3 hoàn thành bởi Lưu Văn Hoàng – Sẵn sàng chuyển sang Bước 4 (Tài liệu Yêu cầu Chức năng FRD & Thiết kế Cơ sở Dữ liệu).*
