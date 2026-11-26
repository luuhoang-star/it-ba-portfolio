# TÀI LIỆU ĐẶC TẢ CÂU CHUYỆN NGƯỜI DÙNG & TIÊU CHÍ CHẤP NHẬN (USER STORIES & GHERKIN AC)

* **Tên dự án:** Nền tảng Thương mại Điện tử Quần Áo Nam (Men's Fashion E-Commerce)
* **Tác giả / IT Business Analyst:** Lưu Văn Hoàng
* **Phiên bản:** v1.0
* **Phương pháp phát triển:** Agile / Scrum & BDD (Behavior-Driven Development)
* **Quy chuẩn đặc tả:** Chuẩn quốc tế Gherkin Syntax (`GIVEN - WHEN - THEN`)

---

## 1. TỔNG QUAN VỀ BỘ USER STORIES

Trong dự án Quần Áo Nam, tài liệu này gồm **5 User Stories quan trọng nhất** đại diện cho toàn bộ hành trình mua hàng của khách nam: từ khâu chọn size, xem màu, thanh toán đến đổi trả sau mua:

| Mã Story | Tên tính năng | Phân hệ | Độ ưu tiên | Điểm ước lượng (Story Points) |
| :--- | :--- | :--- | :--- | :--- |
| **US-001** | Tư vấn gợi ý Size thông minh theo Chiều cao & Cân nặng | Catalog & PDP | **P1 (Bắt buộc)** | 5 SP |
| **US-002** | Chọn ma trận Biến thể (Màu sắc x Size) đổi ảnh thực tế | PDP | **P1 (Bắt buộc)** | 3 SP |
| **US-003** | Khóa giữ hàng tạm thời 15 phút (Soft-Lock Inventory) | Giỏ hàng & Kho | **P1 (Bắt buộc)** | 5 SP |
| **US-004** | Thanh toán 1 bước bằng mã QR VNPay không cần đăng ký | Checkout | **P1 (Bắt buộc)** | 8 SP |
| **US-005** | Đăng ký đổi Size áo tận nhà trong 7 ngày | Sau bán hàng (Post-Order) | **P2 (Nên có)** | 5 SP |

---

## 2. CHI TIẾT TỪNG USER STORY & KỊCH BẢN GHERKIN

---

### 📋 US-001: Tư vấn gợi ý Size quần áo nam thông minh
* **Vai trò & Mục tiêu:**
  > **Là một** khách hàng nam mua sắm online,  
  > **Tôi muốn** hệ thống tự động gợi ý kích cỡ chuẩn xác dựa vào chiều cao và cân nặng của tôi,  
  > **Để** tôi mua được chiếc áo vừa vặn mà không cần tốn thời gian đo đạc hay nhắn tin chờ nhân viên tư vấn.

#### Tiêu chí chấp nhận (Acceptance Criteria):

```gherkin
Kịch bản 1: Gợi ý size thành công và tự động chọn size (Happy Path)
  GIVEN Khách hàng đang ở màn hình xem "Áo Polo Nam Classic Pique"
    AND Khách hàng mở hộp công cụ "Tư vấn chọn Size chuẩn"
   WHEN Khách hàng nhập Chiều cao = "172 cm" và Cân nặng = "68 kg"
    AND Bấm nút "Tính Size ngay"
   THEN Hệ thống hiển thị kết quả: "Size L là lựa chọn hoàn hảo nhất cho vóc dáng của bạn (Độ chính xác 95%)"
    AND Nút chọn kích cỡ "L" trên màn hình tự động chuyển sang trạng thái được chọn (Active)
    AND Giá bán và số lượng tồn kho hiển thị đúng theo Size L

Kịch bản 2: Size gợi ý bị hết hàng ở màu đang xem (Edge Case - Tồn kho bằng 0)
  GIVEN Hệ thống tính toán và gợi ý Size "L" cho khách hàng
    BUT Màu "Đen Nhám" của Size L hiện tại có tồn kho bằng 0
   WHEN Kết quả gợi ý xuất hiện
   THEN Hệ thống hiển thị thông báo thân thiện: "Size L vừa vặn với bạn nhưng màu Đen Nhám hiện đã tạm hết. Bạn có thể chọn màu Xanh Navy hoặc Trắng (vẫn còn Size L)"
    AND Nút chọn Size L màu Đen bị mờ (Disable) và không cho bấm thêm vào giỏ

Kịch bản 3: Người dùng nhập sai định dạng chiều cao / cân nặng (Validation Error)
  GIVEN Khách hàng đang ở ô nhập thông số
   WHEN Khách hàng nhập Chiều cao = "50 cm" hoặc nhập chữ "abc"
   THEN Hệ thống báo lỗi ngay dưới ô nhập: "Vui lòng nhập chiều cao thực tế từ 140cm đến 210cm"
    AND Nút "Tính Size ngay" bị vô hiệu hóa cho đến khi nhập đúng
```

---

### 📋 US-002: Chọn biến thể Màu sắc x Kích thước đồng bộ Album ảnh thực tế
* **Vai trò & Mục tiêu:**
  > **Là một** khách hàng nam,  
  > **Tôi muốn** khi bấm chọn màu áo nào thì toàn bộ ảnh mẫu mặc màu áo đó hiển thị ngay lập tức,  
  > **Để** tôi nhìn rõ màu sắc thực tế và phom dáng trước khi quyết định chi tiền.

#### Tiêu chí chấp nhận (Acceptance Criteria):

```gherkin
Kịch bản 1: Đổi màu áo cập nhật album ảnh tương ứng (Happy Path)
  GIVEN Khách hàng đang xem sản phẩm áo sơ mi nam, đang hiển thị màu mặc định là "Trắng"
   WHEN Khách hàng bấm chọn ô màu "Xanh Navy"
   THEN Toàn bộ thư viện ảnh sản phẩm chuyển sang hiển thị album ảnh người mẫu mặc áo màu "Xanh Navy" (không còn lẫn ảnh áo màu Trắng)
    AND Danh sách các nút kích thước (S, M, L, XL) tự động cập nhật trạng thái còn/hết hàng theo màu "Xanh Navy"
```

---

### 📋 US-003: Cơ chế Giữ hàng tồn kho 15 phút (Soft-Lock Inventory)
* **Vai trò & Mục tiêu:**
  > **Là một** khách hàng đã quyết định mua hàng,  
  > **Tôi muốn** chiếc áo tôi chọn được giữ lại cho riêng tôi trong 15 phút khi tôi đang mở app ngân hàng quét mã,  
  > **Để** không bị người khác nhanh tay mua mất chiếc áo cuối cùng trong đợt khuyến mãi.

#### Tiêu chí chấp nhận (Acceptance Criteria):

```gherkin
Kịch bản 1: Giữ hàng thành công trong thời gian thanh toán (Happy Path)
  GIVEN Trong kho chỉ còn duy nhất 1 chiếc áo "Khoác Gió Nam - Size XL"
   WHEN Khách hàng bấm nút "Tiến hành Thanh toán"
   THEN Hệ thống tăng số lượng khóa tạm (Locked Quantity) = 1 và giảm số lượng mở bán (Available Quantity) = 0
    AND Đồng hồ đếm ngược 15 phút (900 giây) bắt đầu chạy trên màn hình thanh toán
    AND Nếu một khách hàng khác xem chiếc áo này trên web sẽ thấy trạng thái "Tạm thời hết hàng"

Kịch bản 2: Tự động nhả hàng về kho khi quá 15 phút khách không thanh toán (Timeout Case)
  GIVEN Khách hàng được giữ chiếc áo trong 15 phút
    BUT Đã hết 15 phút (00:00) mà hệ thống chưa nhận được tiền từ ngân hàng
   WHEN Bộ đếm thời gian kết thúc
   THEN Hệ thống tự động hủy phiên giao dịch
    AND Tự động hoàn trả 1 chiếc áo về lại số lượng mở bán (Available Quantity = 1) để khách khác mua được
    AND Màn hình hiển thị: "Phiên thanh toán đã hết hạn, sản phẩm đã được hoàn lại kho"
```

---

### 📋 US-004: Thanh toán 1 bước bằng mã QR VNPay không cần đăng ký tài khoản
* **Vai trò & Mục tiêu:**
  > **Là một** khách hàng nam thích sự tiện lợi,  
  > **Tôi muốn** quét mã QR chuyển khoản ngay trên màn hình mà không bắt buộc tạo tài khoản rườm rà,  
  > **Để** tôi hoàn thành đơn hàng chỉ trong 30 giây.

#### Tiêu chí chấp nhận (Acceptance Criteria):

```gherkin
Kịch bản: Quét mã QR thanh toán thành công
  GIVEN Khách hàng nhập xong Họ tên, Số điện thoại và Địa chỉ nhận hàng
    AND Chọn phương thức thanh toán "Quét mã VNPAY-QR"
   WHEN Khách hàng mở App Ngân hàng trên điện thoại quét mã QR hiển thị trên web và xác nhận chuyển tiền
   THEN Cổng thanh toán VNPay gửi tín hiệu xác nhận về hệ thống trong vòng tối đa 3 giây
    AND Màn hình web tự động chuyển sang trang "Đặt hàng thành công - Mã đơn hàng #NF1024"
    AND Hệ thống gửi tin nhắn SMS xác nhận kèm đường link theo dõi bưu kiện cho khách hàng
```

---

### 📋 US-005: Đăng ký yêu cầu đổi Size áo tận nhà trong 7 ngày
* **Vai trò & Mục tiêu:**
  > **Là một** khách hàng đã nhận hàng nhưng mặc thử thấy hơi chật/rộng,  
  > **Tôi muốn** bấm yêu cầu đổi size trực tiếp trên đơn hàng và shipper mang size mới đến tận nhà đổi,  
  > **Để** tôi có được chiếc áo vừa vặn mà không phải tự mang ra bưu cục gửi phiền phức.

#### Tiêu chí chấp nhận (Acceptance Criteria):

```gherkin
Kịch bản 1: Yêu cầu đổi size hợp lệ trong thời hạn 7 ngày
  GIVEN Đơn hàng có trạng thái "Giao hàng thành công" chưa quá 7 ngày
   WHEN Khách hàng vào mục Tra cứu đơn hàng, chọn "Yêu cầu Đổi Size" và chọn Size muốn đổi
   THEN Hệ thống tạo phiếu đổi hàng, khóa giữ 1 sản phẩm size mới trong kho
    AND Tự động thông báo shipper GHN sẽ mang áo size mới đến tận nhà đổi lấy áo cũ trong 2 ngày làm việc

Kịch bản 2: Đơn hàng đã quá hạn 7 ngày
  GIVEN Đơn hàng đã giao thành công được 8 ngày
   WHEN Khách hàng mở trang chi tiết đơn hàng
   THEN Nút "Yêu cầu Đổi Size" bị ẩn (hoặc hiển thị thông báo: "Đơn hàng đã hết thời hạn hỗ trợ đổi size theo chính sách 7 ngày")
```

---

## 3. GÓC PHỎNG VẤN IT BA (CHUẨN BỊ CHO LƯU VĂN HOÀNG)

Khi người phỏng vấn xem bộ User Stories này, họ sẽ đặt các câu hỏi chuyên sâu:

> **Câu hỏi 1:** *"Tại sao em lại viết tiêu chí chấp nhận (AC) theo cú pháp Gherkin Given-When-Then mà không viết gạch đầu dòng?"*  
> **Cách bạn trả lời:**  
> *"Dạ thưa anh/chị, viết theo chuẩn Gherkin có 3 ưu điểm vượt trội:  
> 1. Xóa bỏ hoàn toàn sự hiểu nhầm giữa BA và Lập trình viên vì kịch bản được chia rõ: Điều kiện ban đầu (Given) &rarr; Hành động kích hoạt (When) &rarr; Kết quả hệ thống (Then).  
> 2. Đội ngũ Kiểm thử (QA/Tester) có thể lấy thẳng kịch bản này chuyển hóa thành Test Case tự động (Automation Test) mà không mất thời gian viết lại.  
> 3. Bắt buộc BA phải tư duy bao quát cả luồng thành công (Happy path) lẫn các trường hợp lỗi/ngoại lệ (Edge cases)."*

> **Câu hỏi 2:** *"Trong US-003, làm sao hệ thống biết chính xác hết 15 phút để nhả tồn kho mà không làm chậm server?"*  
> **Cách bạn trả lời:**  
> *"Dạ, về mặt kỹ thuật, em đề xuất sử dụng Redis Key Expiration (hoặc thiết lập Message Queue Delayed Task với thời gian TTL = 900 giây). Khi hết hạn 15 phút, hệ thống tự động bắn ra một sự kiện (Event) để trigger cập nhật lại bảng tồn kho trong Database, không cần server phải chạy vòng lặp liên tục kiểm tra, đảm bảo tối ưu tài nguyên hệ thống."*

---

*Tài liệu Bước 2 hoàn thành bởi Lưu Văn Hoàng – Sẵn sàng chuyển tiếp sang Bước 3 (Bảng dữ liệu Ma trận biến thể & Wireframe).*
