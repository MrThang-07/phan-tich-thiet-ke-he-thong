# Báo cáo Phân tích và Khảo sát Hệ thống Ngân hàng số RikkeiBank

**Mục tiêu:** Củng cố kiến thức, vận dụng phương pháp phân tích yêu cầu vào nghiệp vụ tài chính - ngân hàng số và đóng vai Chuyên viên Phân tích nghiệp vụ khảo sát hệ thống RikkeiBank.

---

## Bước 1: Nhận diện 5 thành phần HTTT và phân biệt Dữ liệu vs Thông tin

### 1. 5 Thành phần HTTT tại RikkeiBank
| Thành phần HTTT | Ví dụ thực tế tại RikkeiBank | Vai trò cơ bản |
| :--- | :--- | :--- |
| **1. Phần cứng (Hardware)** | Máy chủ xử lý giao dịch Core Banking, máy ATM/POS | Hạ tầng vật lý xử lý và giao tiếp tài chính |
| **2. Phần mềm (Software)** | Ứng dụng RikkeiBank Mobile, hệ thống Internet Banking | Giao diện và logic thực hiện giao dịch số |
| **3. Dữ liệu (Data)** | Số dư tài khoản, lịch sử biến động số dư | Dữ liệu tài chính cốt lõi |
| **4. Con người (People)** | **Khách hàng cá nhân, Giao dịch viên** | Tác nhân trực tiếp tương tác với hệ thống |
| **5. Quy trình (Process)** | **Quy trình nhập mã OTP xác thực và trừ tiền trong tài khoản** | Trình tự các bước xác thực và chuyển khoản |

### 2. Phân biệt Dữ liệu (Data) và Thông tin (Information)
| STT | Nội dung dữ liệu tại RikkeiBank | Dữ liệu | Thông tin | Lý do phân loại |
| :--- | :--- | :--- | :--- | :--- |
| 1 | 50000000 | [ x ] | [ ] | Chuỗi số thô, chưa rõ là tiền gửi, tiền vay hay hạn mức |
| 2 | Khách hàng Trần Văn C chuyển 5.000.000 VNĐ lúc 10:15 ngày 15/08 | [ ] | [ x ] | Đầy đủ ngữ cảnh giao dịch: Ai, Số tiền, Thời gian |
| 3 | 0987654321 | [ x ] | [ ] | Chuỗi số thô, có thể là số điện thoại hoặc số tài khoản |
| 4 | Tổng số dư tiết kiệm trực tuyến của chi nhánh đạt 200 tỷ VNĐ trong tháng 8 | [ ] | [ x ] | **Số liệu đã được tính toán (tổng hợp), có đầy đủ ngữ cảnh về nghiệp vụ (tiết kiệm), địa điểm (chi nhánh) và thời gian (tháng 8)** |
| 5 | TK101, Nguyễn Thị D, Active, Gold | [ x ] | [ ] | **Là các bản ghi rời rạc (Mã TK, Tên, Trạng thái, Hạng thẻ), chưa được ghép thành câu có ý nghĩa hoàn chỉnh** |

---

## Bước 2: Khảo sát môi trường và xác định Stakeholders

### 1. Phân loại môi trường
| Yếu tố khảo sát tại RikkeiBank | Thuộc loại môi trường | Tầm ảnh hưởng đến hệ thống |
| :--- | :--- | :--- |
| Năng lực bảo mật của đội ngũ IT | Môi trường Nội bộ | Quyết định khả năng phòng chống tấn công mạng |
| Thông tư an toàn thông tin Ngân hàng Nhà nước | Môi trường Bên ngoài | Quy định bắt buộc về xác thực sinh trắc học |
| Hệ thống đường truyền liên ngân hàng Napas | Môi trường Bên ngoài | Ảnh hưởng trực tiếp đến tốc độ chuyển tiền liên ngân hàng |
| Thói quen sử dụng điện thoại của người cao tuổi | **Môi trường Bên ngoài** | **Đòi hỏi ứng dụng phải có chế độ giao diện "Đơn giản" (chữ to, ít nút bấm) để nhóm khách hàng này dễ thao tác** |
| Chính sách lãi suất của các ngân hàng đối thủ | **Môi trường Bên ngoài** | **Hệ thống cần có tính năng linh hoạt cập nhật biểu lãi suất và các chương trình khuyến mãi để cạnh tranh** |

### 2. Xác định Stakeholders
| Nhóm Stakeholder | Vai trò trong dự án | Mối quan tâm lớn nhất đối với phần mềm |
| :--- | :--- | :--- |
| **1. Khách hàng cá nhân** | Người dùng dịch vụ cuối | Chuyển tiền nhanh chóng, an toàn, giao diện mượt mà |
| **2. Chuyên viên An ninh mạng** | Giám sát bảo mật | Hệ thống chống rò rỉ mã OTP và mã hóa dữ liệu đầu cuối |
| **3. Giao dịch viên tại quầy** | **Người dùng vận hành nội bộ** | **Hệ thống tải dữ liệu nhanh, đối soát thông tin khách hàng chính xác và không bị treo lúc cao điểm** |

---

## Bước 3: Lựa chọn kỹ thuật thu thập yêu cầu và soạn câu hỏi mẫu

### 1. Kỹ thuật thu thập yêu cầu
| STT | Tình huống khảo sát tại RikkeiBank | Kỹ thuật phù hợp nhất | Lý do lựa chọn ngắn gọn |
| :--- | :--- | :--- | :--- |
| 1 | Khảo sát nhu cầu giao dịch của 50.000 khách hàng trẻ Gen Z | Bảng câu hỏi / Khảo sát (Survey) | Quy mô người dùng cực lớn, thu thập nhanh số liệu định lượng |
| 2 | Làm rõ quy định đối soát và hạn mức chuyển khoản với Giám đốc rủi ro | Phỏng vấn (Interview) | Chuyên gia cấp cao, cần trao đổi sâu về chính sách nghiệp vụ |
| 3 | Xem thực tế thao tác nhập lệnh chuyển tiền quốc tế của giao dịch viên | **Quan sát (Observation)** | **Nhìn thấy trực tiếp các thao tác dư thừa, các lỗi phát sinh (nếu có) trong thực tế để tối ưu giao diện** |
| 4 | Đọc các văn bản hướng dẫn tiêu chuẩn bảo mật thanh toán PCI-DSS | Nghiên cứu tài liệu (Document Analysis) | Tiêu chuẩn quốc tế dạng văn bản quy chuẩn có sẵn |
| 5 | Lấy ý kiến đóng góp của nhóm 15 chuyên viên chăm sóc khách hàng VIP | **Thảo luận nhóm / Bảng câu hỏi (Focus Group / Survey)** | **Số lượng 15 người là vừa đủ để gửi form hoặc họp nhóm để lấy ý kiến tổng hợp nhanh chóng mà không cần tốn thời gian phỏng vấn 1-1** |

### 2. Câu hỏi trắc nghiệm khảo sát khách hàng cá nhân
* **Câu hỏi:** "Khi chuyển tiền trên ứng dụng RikkeiBank, yếu tố nào quan trọng nhất với bạn?"
* **Phương án lựa chọn:**
    * A. Tốc độ chuyển tiền đến tài khoản người nhận ngay lập tức (dưới 3s).
    * B. Các lớp bảo mật an toàn (xác thực khuôn mặt/vân tay, Smart OTP).
    * C. Giao diện trực quan, thao tác ít bước, tự động lưu người nhận cũ.
    * D. Được miễn hoàn toàn các loại phí giao dịch liên ngân hàng.

---

## Bước 4: Phân loại Yêu cầu Chức năng (FR) và Phi chức năng (NFR)

| STT | Phát biểu yêu cầu | Phân loại | Mã định danh | Câu hỏi cốt lõi giải thích |
| :--- | :--- | :--- | :--- | :--- |
| (1) | Khách hàng có thể quét mã QR để thanh toán hóa đơn | FR | FR-01 | Hành động hệ thống cung cấp (LÀM GÌ) |
| (2) | Giao dịch chuyển tiền phải hoàn tất trong vòng dưới 3 giây | NFR | NFR-01 | Tiêu chuẩn tốc độ xử lý (TỐT NHƯ THẾ NÀO) |
| (3) | Mọi giao dịch trên 10 triệu VNĐ bắt buộc xác thực sinh trắc học khuôn mặt | NFR | NFR-02 | Tiêu chuẩn an ninh và bảo mật (TỐT NHƯ THẾ NÀO) |
| (4) | Khách hàng có thể mở sổ tiết kiệm trực tuyến ngay trên ứng dụng | **FR** | **FR-02** | **Đây là một tính năng nghiệp vụ cụ thể (hành động mở sổ) mà hệ thống bắt buộc phải LÀM ĐƯỢC** |
| (5) | Hệ thống Core Banking chịu tải được 10.000 giao dịch đồng thời mỗi giây | **NFR** | **NFR-03** | **Đây là thước đo tiêu chuẩn về hiệu năng và sức chịu tải của hệ thống (TỐT NHƯ THẾ NÀO)** |

---

## Bước 5: Đặc tả User Story chuẩn ba thành phần

**User Story dành cho Khách hàng:**
*   **Là một (Who):** Khách hàng sử dụng ứng dụng RikkeiBank
*   **Tôi muốn (What):** Lưu danh bạ người thụ hưởng thường xuyên chuyển tiền
*   **Để (Why):** **Tôi không phải nhập lại số tài khoản dài dòng và tốn thời gian cho những lần giao dịch sau, giúp quá trình chuyển tiền nhanh chóng và tránh nhập sai số.**