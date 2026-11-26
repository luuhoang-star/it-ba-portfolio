# TÀI LIỆU KẾ HOẠCH SPRINT & MA TRẬN TRUY VẾT YÊU CẦU (SPRINT BACKLOG & RTM MATRIX)

* **Tên dự án:** Nền tảng Thương mại Điện tử Quần Áo Nam (Men's Fashion E-Commerce)
* **Tác giả / IT Business Analyst:** Lưu Văn Hoàng
* **Phương pháp quản trị:** Agile / Scrum (Sprint 2 tuần)
* **Phiên bản:** v1.0
* **Trạng thái:** Sẵn sàng nghiệm thu (Ready for Release)

---

## 1. MỤC ĐÍCH CỦA BƯỚC 4 TRONG QUY TRÌNH BA

Sau khi đã có **Quy trình (Bước 1)**, **User Story (Bước 2)**, và **Wireframe (Bước 3)**, một IT BA chuyên nghiệp cần thực hiện 2 việc sống còn:
1. **Lên kế hoạch Sprint (Sprint Planning):** Chia nhỏ công việc thành các kỳ chạy nước rút 2 tuần, ước lượng điểm độ phức tạp (Story Points) để đội ngũ Dev và Tester hoàn thành đúng hạn.
2. **Lập Ma trận truy vết (RTM - Requirement Traceability Matrix):** Đảm bảo **100% mục tiêu kinh doanh ban đầu** đều được hiện thực hóa thành code và có kịch bản kiểm thử (Test Case) tương ứng, không bỏ sót bất kỳ yêu cầu nào.

---

## 2. KẾ HOẠCH PHÂN BỔ 3 KỲ SPRINT (RELEASE ROADMAP)

Dự án triển khai theo mô hình Agile với 3 Sprint chính:

```
+-----------------------------------------------------------------------------------------+
| SPRINT 1 (Tuần 1 - 2)       | SPRINT 2 (Tuần 3 - 4)       | SPRINT 3 (Tuần 5 - 6)       |
| "Nền tảng & Chọn Size"     | "Giỏ hàng & Thanh toán"     | "Giao vận & Hậu mãi 7 ngày" |
| --------------------------  | --------------------------  | --------------------------  |
| - Ma trận biến thể SKU      | - Soft-lock kho 15 phút     | - Đẩy đơn tự động GHN API   |
| - Đổi màu áo cập nhật ảnh   | - Thanh toán QR VNPay       | - Cổng đổi size tận nhà     |
| - Tính năng Gợi ý Size      | - Áp dụng Voucher đa tầng   | - SMS thông báo hành trình  |
| => Vận tốc: 34 Story Points | => Vận tốc: 36 Story Points | => Vận tốc: 30 Story Points |
+-----------------------------------------------------------------------------------------+
```

---

## 3. MÔ PHỎNG BẢNG JIRA KANBAN BOARD (SPRINT 2 HIỆN TẠI)

Đây là bảng theo dõi tiến độ hằng ngày (Daily Scrum) của nhóm gồm: **1 BA (Lưu Văn Hoàng), 2 Lập trình viên (Dev), 1 Kiểm thử viên (Tester)**:

| CẦN LÀM (TODO) | ĐANG LÀM (IN PROGRESS) | ĐANG TEST (QA TESTING) | HOÀN TẤT (DONE) |
| :--- | :--- | :--- | :--- |
| **[NF-104]** Tích điểm thành viên (Loyalty) - *5 SP* | **[NF-101]** Tích hợp Webhook QR VNPay - *8 SP* | **[NF-098]** Cơ chế Soft-lock kho 15p - *5 SP* | **[NF-091]** Bộ lọc quần áo nam đa tầng - *5 SP* |
| **[NF-105]** Đánh giá sản phẩm kèm ảnh - *3 SP* | **[NF-102]** Tự động sinh mã vận đơn GHN - *8 SP* | **[NF-099]** Logic mã Voucher & Freeship - *5 SP* | **[NF-092]** Bảng tính Size áo thông minh - *5 SP* |
| **[NF-106]** Gửi thông báo đẩy SMS - *2 SP* | | | **[NF-093]** Đổi màu áo cập nhật album ảnh - *3 SP* |

---

## 4. MA TRẬN TRUY VẾT YÊU CẦU (REQUIREMENT TRACEABILITY MATRIX - RTM)

Đây là tài liệu quan trọng nhất thể hiện **tư duy kiểm soát chất lượng toàn diện của Lưu Văn Hoàng**. Bảng này chứng minh mọi mục tiêu của sếp/khách hàng đều được ánh xạ rõ ràng:

| Mã Yêu cầu | Mục tiêu Kinh doanh (BO) | Yêu cầu Chức năng (FR) | User Story liên kết | Kịch bản Kiểm thử (Test Case) | Trạng thái Nghiệm thu |
| :---: | :--- | :--- | :---: | :--- | :---: |
| **REQ-01** | **BO-01:** Hạ tỷ lệ đổi trả hàng do sai size xuống dưới 9% | Thuật toán tính toán chỉ số phom dáng và đề xuất Size tự động | **US-001** | `TC-SIZE-001`: Nhập 172cm/68kg gợi ý Size L<br>`TC-SIZE-002`: Xử lý size L màu Đen hết hàng | <span style="color:#15803d; font-weight:700;">✅ ĐÃ NGHIỆM THU</span> |
| **REQ-02** | **BO-02:** Đồng bộ tồn kho ma trận 100%, chống bán khống | Quản lý tồn kho theo từng mã SKU con (Color x Size) | **US-002** | `TC-STOCK-001`: Đổi màu áo cập nhật đúng album ảnh<br>`TC-STOCK-002`: Nút size hết hàng bị gạch chéo mờ | <span style="color:#15803d; font-weight:700;">✅ ĐÃ NGHIỆM THU</span> |
| **REQ-03** | **BO-02:** Chống tranh giành hàng khi Flash Sale | Cơ chế Soft-Lock giữ hàng trong kho đúng 15 phút | **US-003** | `TC-LOCK-001`: Giữ hàng 15:00 khi mở thanh toán<br>`TC-LOCK-002`: Tự nhả hàng về kho khi hết 15 phút | <span style="color:#b45309; font-weight:700;">🔄 ĐANG TEST</span> |
| **REQ-04** | **BO-03:** Giảm tỷ lệ bỏ giỏ hàng xuống dưới 18% | Thanh toán 1 bước qua mã QR VNPay không cần đăng ký | **US-004** | `TC-PAY-001`: Quét mã QR thành công trong 3s<br>`TC-PAY-002`: Xử lý khi ngân hàng báo lỗi timeout | <span style="color:#b45309; font-weight:700;">🔄 ĐANG TEST</span> |
| **REQ-05** | **BO-04:** Tiết kiệm 80% thời gian đóng gói tại kho | Tích hợp Open API Giao Hàng Nhanh tạo vận đơn tự động | **US-005** | `TC-SHIP-001`: Tự tính phí ship theo địa chỉ quận/huyện<br>`TC-SHIP-002`: In mã vận đơn mã vạch tự động | <span style="color:#1d4ed8; font-weight:700;">⏳ SPRINT 3</span> |
| **REQ-06** | **BO-01:** Nâng cao độ an tâm khi mua đồ nam online | Cổng đăng ký đổi Size áo miễn phí tận nhà trong 7 ngày | **US-005** | `TC-RET-001`: Đổi size trong vòng 7 ngày hợp lệ<br>`TC-RET-002`: Ẩn nút đổi size khi đơn quá 7 ngày | <span style="color:#1d4ed8; font-weight:700;">⏳ SPRINT 3</span> |

---

## 5. BỘ TIÊU CHUẨN ĐỊNH NGHĨA (DOR & DOD CHUẨN AGILE)

Để nhóm làm việc không cãi nhau về việc *"Đã xong việc hay chưa"*, BA Lưu Văn Hoàng thiết lập 2 bộ quy tắc:

### 5.1. Definition of Ready (DoR - Khi nào User Story đủ điều kiện đưa vào code?)
* Story có mô tả rõ ràng theo cú pháp: *Là một... Tôi muốn... Để...*
* Tiêu chí chấp nhận (AC) đã viết đầy đủ theo chuẩn Gherkin: *Given - When - Then* cho cả trường hợp bình thường lẫn trường hợp lỗi.
* Có đính kèm bản vẽ Wireframe đã được đánh số chú thích rõ ràng.
* Đã được Tech Lead và QA ước lượng Story Points (không vượt quá 8 SP/story).

### 5.2. Definition of Done (DoD - Khi nào một tính năng được coi là hoàn tất 100%?)
* Mã nguồn đã được Lập trình viên viết xong và được Tech Lead Review (Code Review Passed).
* Đội Kiểm thử (Tester) đã chạy hết 100% Test Case trong RTM và không còn lỗi nghiêm trọng (Zero Blocker/Critical Bugs).
* Đã triển khai lên môi trường UAT (User Acceptance Testing) và được BA Lưu Văn Hoàng cùng Giám đốc Kinh doanh nghiệm thu thành công.
* Tài liệu hướng dẫn sử dụng hoặc API Docs đã được cập nhật lên Confluence.

---

## 6. GÓC PHỎNG VẤN IT BA (CHUẨN BỊ CHO LƯU VĂN HOÀNG)

> **Câu hỏi 1:** *"Tại sao em phải mất công lập bảng Ma trận RTM ở Mục 4?"*  
> **Cách bạn trả lời:**  
> *"Dạ thưa anh/chị, trong các dự án thực tế, rất nhiều trường hợp Lập trình viên chỉ thích code những tính năng họ thích mà quên mất mục tiêu kinh doanh ban đầu của công ty. Bảng RTM là công cụ đối soát sống còn của BA để đảm bảo: 100% mục tiêu kinh doanh (BO) đều được chuyển hóa thành User Story và mọi User Story đều phải có Test Case kiểm thử nghiệm thu. Bảng này giúp sếp và khách hàng nhìn vào là biết dự án đã hoàn thành được bao nhiêu % tiến độ một cách minh bạch."*

> **Câu hỏi 2:** *"Nếu đến ngày cuối Sprint mà Dev chưa code xong tính năng Soft-Lock (NF-098), em sẽ xử lý thế nào?"*  
> **Cách bạn trả lời:**  
> *"Dạ, theo nguyên lý Agile Scrum, em tuyệt đối không thỏa hiệp bằng cách 'nghiệm thu ép' khi tính năng chưa đạt chuẩn DoD. Em sẽ phân tích nguyên nhân cùng Dev: nếu chỉ vướng ở khâu test nhỏ, nhóm có thể tập trung hỗ trợ để đóng task. Nếu tính năng thực sự chưa ổn định, em sẽ chuyển phần việc còn lại sang Sprint Backlog của kỳ tiếp theo, đồng thời cập nhật lại vận tốc (Velocity) của nhóm để điều chỉnh kế hoạch Sprint tới chính xác hơn."*

---

*Tài liệu Bước 4 hoàn thành bởi Lưu Văn Hoàng – Trọn bộ 4 Bước của Portfolio IT BA đã hoàn tất 100%!*
