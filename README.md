# 👔 HỒ SƠ NĂNG LỰC IT BUSINESS ANALYST (IT BA PORTFOLIO)
> **Tác giả:** Lưu Văn Hoàng  
> **Vị trí ứng tuyển:** IT Business Analyst / Junior Product Owner  
> **Dự án thực chiến:** Nền tảng Thương mại Điện tử Bán lẻ Quần Áo Nam Đa Kênh (**NovaFashion Men's Apparel**)  
> **Bộ công cụ & Phương pháp:** Agile / Scrum · BDD Gherkin · BPMN · Atlassian Jira & Confluence · Figma Wireframing · RTM Matrix

---

## 📌 1. TỔNG QUAN DỰ ÁN (PROJECT OVERVIEW)

* **Bối cảnh:** NovaFashion là thương hiệu thời trang nam sở hữu 5 showroom và các kênh bán lẻ online (Website, TikTok Shop, Fanpage).
* **Vấn đề cốt lõi (Pain Point):** Nam giới mua sắm có xu hướng chốt đơn nhanh nhưng ngại đo đạc số đo cơ thể bằng thước dây. Việc chọn size theo cảm tính dẫn đến **tỷ lệ đổi trả hàng lên tới 28%**, làm tăng chi phí vận hành logistics 2 chiều và gây sụt giảm lợi nhuận nghiêm trọng.
* **Mục tiêu chiến lược (SMART Objectives):**
  1. Xây dựng công cụ **Bảng tính & Gợi ý Size thông minh (Smart Size Advisor)** tự động tính toán từ Chiều cao + Cân nặng, hạ tỷ lệ đổi size xuống **dưới 9%**.
  2. Triệt tiêu 100% tình trạng bán âm hàng bằng cơ chế **Soft-Lock giữ tồn kho trong 15 phút** khi khách thanh toán mã QR.
  3. Tối ưu tỷ lệ bỏ giỏ hàng từ 35% xuống **dưới 18%** thông qua luồng Thanh toán 1 bước (One-step checkout) quét mã VNPAY-QR không cần đăng ký tài khoản.

---

## 📂 2. CẤU TRÚC BỘ TÀI LIỆU DỰ ÁN (PORTFOLIO ARTIFACTS)

Dự án được phân rã thành 4 giai đoạn chuẩn mực theo quy trình phát triển phần mềm chuyên nghiệp:

| Giai đoạn | Tên tài liệu chi tiết | Định dạng xem nhanh (Web & Markdown) | Trọng tâm nghiệp vụ |
| :---: | :--- | :--- | :--- |
| **BƯỚC 1** | **Quy trình Nghiệp vụ (Process Flow)** | 🌐 [Xem Giao diện HTML](buoc1_quy_trinh_nghiep_vu.html) <br> 📄 [Xem File Markdown](buoc1_quy_trinh_nghiep_vu.md) | Phân tích chênh lệch AS-IS vs TO-BE, Sơ đồ khối Flowchart 3 chặng trực quan. |
| **BƯỚC 2** | **User Stories & Tiêu chí Gherkin AC** | 🌐 [Xem Giao diện HTML](buoc2_user_stories_gherkin.html) <br> 📄 [Xem File Markdown](buoc2_user_stories_gherkin.md) | 5 User Stories cốt lõi với kịch bản BDD Gherkin (`GIVEN - WHEN - THEN`), bao quát cả Happy Path và Edge Cases lỗi hết hàng. |
| **BƯỚC 3** | **Bản phác thảo Giao diện (Wireframe)** | 🌐 [Xem Giao diện HTML](buoc3_wireframe_va_logic_giao_dien.html) <br> 📄 [Xem File Markdown](buoc3_wireframe_va_logic_giao_dien.md) | Bản vẽ Wireframe có đánh số chú thích `[1]` &rarr; `[6]`, Bảng ma trận biến thể dữ liệu SKU (Color x Size x Tồn kho) và bộ mô phỏng tính size trực tiếp. |
| **BƯỚC 4** | **Kế hoạch Sprint Jira & Ma trận RTM** | 🌐 [Xem Giao diện HTML](buoc4_ke_hoach_sprint_va_ma_tran_rtm.html) <br> 📄 [Xem File Markdown](buoc4_ke_hoach_sprint_va_ma_tran_rtm.md) | Lộ trình 3 Sprint, Bảng Jira Scrum 4 cột, Ma trận truy vết yêu cầu (RTM) đối soát 100% và tiêu chuẩn chất lượng DoR/DoD. |
| **TỔNG HỢP** | **Cổng Portfolio Web Tổng hợp (Single Page)** | 🌐 [index.html](index.html) | Trang web toàn diện tích hợp 9 thẻ điều hướng phục vụ trình chiếu khi đi phỏng vấn. |

---

## 🛠️ 3. KỸ NĂNG VÀ NĂNG LỰC THỂ HIỆN (KEY BA COMPETENCIES)

* **Business Process Modeling:** Thành thạo vẽ sơ đồ nghiệp vụ, phân tích điểm nghẽn (Bottlenecks) và tái thiết kế quy trình (BPR).
* **Agile / Scrum Mastery:** Lập kế hoạch Sprint Backlog, ước lượng Story Points bằng Planning Poker, phân định rõ ràng Definition of Ready (DoR) và Definition of Done (DoD).
* **Behavior-Driven Development (BDD):** Viết tiêu chí chấp nhận chuẩn mực bằng cú pháp Gherkin, tạo cầu nối hoàn hảo giữa BA, Lập trình viên (Dev) và Kiểm thử viên (Tester).
* **Data-driven & Solution Architecture:** Hiểu sâu cấu trúc dữ liệu thương mại điện tử: Sự khác biệt giữa bảng Sản phẩm cha (`Products`) và bảng Biến thể SKU con (`Product_Variants`).
* **Traceability & Quality Assurance:** Vận hành Ma trận RTM đảm bảo không một yêu cầu nào của doanh nghiệp bị bỏ sót.

---

## 🚀 4. HƯỚNG DẪN KÍCH HOẠT GITHUB PAGES ĐỂ LẤY LINK PORTFOLIO ONLINE

Sau khi đẩy dự án này lên tài khoản GitHub của bạn, bạn có thể biến nó thành trang web trực tuyến trong 30 giây:

1. Mở Repository này trên GitHub.
2. Vào mục **Settings** &rarr; Chọn thẻ **Pages** ở thanh menu bên trái.
3. Tại mục **Branch**, chọn nhánh `main` (hoặc `master`) &rarr; Thư mục để mặc định là `/(root)` &rarr; Bấm **Save**.
4. Chờ 1 - 2 phút, GitHub sẽ cấp cho bạn một đường link web cá nhân (ví dụ: `https://<ten-tai-khoan>.github.io/<ten-repo>/`).
5. Đính kèm đường link này ngay đầu CV của bạn!

---

## 📬 5. THÔNG TIN LIÊN HỆ

* **Ứng viên:** Lưu Văn Hoàng
* **Vị trí mục tiêu:** IT Business Analyst / Junior Product Owner
* **Địa điểm:** Hà Nội / TP. Hồ Chí Minh
* **Email:** *(Cập nhật email của bạn tại đây)*
* **LinkedIn:** *(Cập nhật link LinkedIn của bạn tại đây)*

---
*© 2026 Lưu Văn Hoàng. Toàn bộ tài liệu được xây dựng phục vụ mục đích ứng tuyển và chứng minh năng lực nghề nghiệp IT Business Analyst.*
