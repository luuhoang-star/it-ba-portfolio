# 👔 IT BA Portfolio: E-Commerce Fashion Sizing & Checkout System
> **Dự án chuẩn đầu ra Vị trí Fresher / Junior IT Business Analyst**  
> **Tác giả:** Lưu Văn Hoàng  
> **Lĩnh vực (Domain):** E-Commerce / Thời trang nam (Men's Apparel)  
> **Sản phẩm:** Single-Page Interactive BA Portfolio & System Specification  
> 🌐 **Live Demo Website:** [https://luuhoang-star.github.io/it-ba-portfolio/](https://luuhoang-star.github.io/it-ba-portfolio/)  

---

## 📌 1. Giới thiệu Dự án (Executive Summary)

Dự án mô phỏng toàn diện quá trình phân tích và đặc tả yêu cầu nghiệp vụ cho tính năng **"Smart Size Advisor & Multi-variant Checkout System"** (Tư vấn chọn size thông minh & Đặt hàng biến thể thời trang nam) cho hệ sinh thái bán lẻ **NovaFashion Men**.

### 🎯 Bài toán Kinh doanh (Business Problems):
1. **Tỷ lệ đổi trả hàng do sai kích cỡ đạt 28%:** Nam giới mua online thường ngại đo số đo cơ thể hoặc bảng size quá phức tạp, dẫn đến chọn sai size (chi phí logistics đổi trả tốn kém).
2. **Xung đột tồn kho biến thể (Overselling):** Khách đặt áo màu Đen - Size L nhưng kho thực tế đã hết do đơn hàng khác đang thanh toán chưa trừ kho.
3. **Tỷ lệ bỏ giỏ hàng (Cart Abandonment) cao (68%):** Luồng chọn biến thể rườm rà, thiếu minh bạch về trạng thái còn/hết hàng theo từng SKU.

### 💡 Giải pháp Phân tích Nghiệp vụ (BA Solutions):
- **Bước 1: Tối ưu Quy trình nghiệp vụ (Business Process Flowchart):** Tái thiết kế quy trình từ AS-IS sang TO-BE, bổ sung cơ chế kiểm tra biến thể và **Soft-lock tồn kho 15 phút** trong phiên checkout.
- **Bước 2: Đặc tả User Stories & BDD Gherkin (Acceptance Criteria):** Chuẩn hóa User Story theo mẫu INVEST và tiêu chí nghiệm thu chi tiết `GIVEN - WHEN - THEN - AND - BUT` cho cả luồng Happy Path và Edge Cases (hết hàng, hủy phiên).
- **Bước 3: Wireframe Chú thích & UI Logic (Interactive Prototype):** Xây dựng Wireframe trang chi tiết sản phẩm (PDP) với ma trận biến thể Màu sắc x Kích cỡ, kèm **Smart Size Advisor** tự động tính toán size dựa trên Chiều cao & Cân nặng.
- **Bước 4: Kế hoạch Sprint & Ma trận RTM (Traceability & Delivery):** Lập Sprint Backlog 2 tuần, tiêu chuẩn Ready (DoR), tiêu chuẩn Done (DoD) và Ma trận truy xuất nguồn gốc yêu cầu (RTM) đảm bảo độ phủ 100% từ Business Goal đến Test Case.

---

## 📂 2. Cấu trúc Dự án (Repository Structure)

```text
├── index.html        # Ứng dụng Web Single-Page tương tác hoàn chỉnh (Gộp Bước 1 -> 4 + Q&A)
├── README.md         # Tài liệu tổng quan dự án & hồ sơ năng lực IT BA
└── .gitignore        # Cấu hình bỏ qua các tệp không cần thiết
```

Tất cả 4 bước được tích hợp trong **[index.html](file:///c:/Users/luuva/Herd/test/index.html)** với giao diện Dashboard hiện đại, tab navigation mượt mà và widget tương tác thực tế.

---

## 📑 3. Nội dung Chi tiết 4 Bước Phân tích (Detailed Artifacts)

### 🔹 Bước 1: Business Process Flowchart (Sơ đồ Quy trình Nghiệp vụ)
- Phân tích khoảng cách (Gap Analysis) AS-IS vs TO-BE.
- Sơ đồ trực quan 3 giai đoạn bằng Mermaid.js:
  1. *Giai đoạn Duyệt & Lựa chọn biến thể (PDP)*
  2. *Giai đoạn Khóa tạm thời tồn kho (Cart & Checkout)*
  3. *Giai đoạn Xử lý đơn & Cập nhật kho (Order Placement & Payment)*
- Cơ chế **Soft-lock 15 phút** chống overselling khi có nhiều khách hàng cùng mua 1 SKU cuối cùng.

### 🔹 Bước 2: User Stories & BDD Gherkin Acceptance Criteria
- **US-01:** Lựa chọn biến thể Màu sắc & Kích cỡ (Color Swatch & Size Selector).
- **US-02:** Tư vấn chọn size thông minh theo Chiều cao & Cân nặng (Smart Size Advisor).
- **US-03:** Khóa tồn kho tạm thời khi vào bước Checkout (Inventory Soft-lock & Release).
- Toàn bộ tiêu chí nghiệm thu được viết theo chuẩn **BDD (Behavior-Driven Development)** với từng dòng phân biệt `GIVEN`, `WHEN`, `THEN`, `AND`, `BUT` rõ ràng, sẵn sàng cho QA viết Automation Test.

### 🔹 Bước 3: Wireframe Chú thích Kỹ thuật & Interactive Prototype
- Chú thích UI specs từ `[1]` đến `[5]`:
  - `[1]` Bộ sưu tập ảnh & Zoom chi tiết theo màu đã chọn.
  - `[2]` Thông tin SKU, Giá niêm yết, Giá khuyến mãi và Huy hiệu tiết kiệm.
  - `[3]` Color Swatches & Size Buttons với trạng thái Disable/Sold out trực quan.
  - `[4]` Widget Trợ lý chọn size (Interactive: Nhập chiều cao, cân nặng -> Gợi ý size ngay lập tức).
  - `[5]` Nút CTA "Thêm vào giỏ" & "Mua ngay" tự động vô hiệu hóa nếu SKU hết hàng.
- **Demo tương tác thực tế (Live Interactive Demo):** Người dùng có thể click chọn màu, click chọn size, nhập số đo để thấy hệ thống tính size và cập nhật SKU `POLO-XANH-L`, tồn kho còn lại theo thời gian thực.

### 🔹 Bước 4: Kế hoạch Sprint, Tiêu chuẩn DoR/DoD & Ma trận RTM
- **Sprint Backlog:** Mô phỏng Scrum Board trực quan (To Do, In Progress, Code Review/QA, Done) cho Sprint 1 (2 tuần, 24 Story Points).
- **Definition of Ready (DoR):** 6 điều kiện bắt buộc để Dev nhận việc vào Sprint.
- **Definition of Done (DoD):** 7 tiêu chí kiểm duyệt để đóng User Story (Unit Test > 80%, Regression pass, Product Owner duyệt AC).
- **Requirement Traceability Matrix (RTM):** Bảng ma trận ánh xạ 2 chiều từ Business Requirement (BR-01, BR-02, BR-03) sang Functional Req (FR), User Story (US), Wireframe ID và QA Test Case ID.

### 🔹 Phần mở rộng: Sổ tay Phỏng vấn IT BA (Interview Preparation)
- Trả lời chuẩn chỉ 4 câu hỏi phỏng vấn kinh điển về:
  1. Sự khác nhau giữa AS-IS và TO-BE.
  2. Cách xử lý khi PO và Lead Dev bất đồng ý kiến về Requirement.
  3. Cách viết BDD Gherkin chuẩn và giá trị mang lại cho đội ngũ Test.
  4. Quản lý Scope Creep trong quá trình chạy Sprint.

---

## 🚀 4. Hướng dẫn Mở và Trải nghiệm (How to Run)

Không cần cài đặt backend phức tạp, chỉ cần trình duyệt web:

1. Clone repository về máy:
   ```bash
   git clone https://github.com/luuhoang-star/it-ba-portfolio.git
   ```
2. Mở file `index.html` trực tiếp bằng trình duyệt Google Chrome, Edge hoặc Brave.
3. Chuyển đổi giữa các tab ở thanh Header để khám phá tài liệu từ Tổng quan đến Bước 4.

---

## 👨‍💻 Thông tin Tác giả (Author Profile)
- **Họ và tên:** Lưu Văn Hoàng
- **Vị trí mục tiêu:** Fresher / Junior IT Business Analyst
- **Kỹ năng cốt lõi:** Requirement Elicitation, Business Process Modeling (BPMN / Flowchart), Agile Scrum, User Story & BDD Gherkin Writing, Wireframing & UI/UX Logic, Traceability Matrix (RTM), SQL cơ bản, API Specification.
