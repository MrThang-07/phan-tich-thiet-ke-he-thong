# Báo cáo Phân tích và Khảo sát Hệ thống Phòng khám RikkeiCare

**Mục tiêu:** Hoàn thành 5 bước phân tích hệ thống thông tin, phân loại dữ liệu, xác định các bên liên quan, áp dụng kỹ thuật thu thập yêu cầu và đặc tả User Story cho dự án số hóa phòng khám RikkeiCare.

---

## Bước 1: Nhận diện 5 thành phần HTTT và phân biệt Dữ liệu vs Thông tin

### 1. 5 Thành phần HTTT
| Thành phần HTTT | Ví dụ thực tế tại phòng khám RikkeiCare | Vai trò cơ bản |
| :--- | :--- | :--- |
| **1. Phần cứng (Hardware)** | Máy tính để bàn tại quầy lễ tân, máy chủ lưu trữ | Thiết bị vật lý để nhập liệu và xử lý |
| **2. Phần mềm (Software)** | Phần mềm quản lý phòng khám RikkeiCare | Ứng dụng hỗ trợ nghiệp vụ khám chữa bệnh |
| **3. Dữ liệu (Data)** | Danh sách bệnh nhân, hồ sơ bệnh án điện tử | Dữ liệu lưu trữ phục vụ chẩn đoán |
| **4. Con người (People)** | Bác sĩ, Nhân viên tiếp tân, Bệnh nhân | Người trực tiếp sử dụng và vận hành |
| **5. Quy trình (Process)** | Quy trình bệnh nhân đặt lịch, tiếp tân tiếp nhận và phát số thứ tự | Các bước tiếp nhận và phục vụ bệnh nhân |

### 2. Phân biệt Dữ liệu (Data) và Thông tin (Information)
| STT | Nội dung dữ liệu tại phòng khám | Dữ liệu | Thông tin | Lý do phân loại |
| :--- | :--- | :--- | :--- | :--- |
| 1 | 38.5 | [ x ] | [ ] | Số liệu thô, chưa có đơn vị và ngữ cảnh |
| 2 | Bệnh nhân Nguyễn Văn A, thân nhiệt 38.5 độ C, đo lúc 08:30 sáng | [ ] | [ x ] | Đã có ngữ cảnh đầy đủ: Ai, Chỉ số gì, Khi nào |
| 3 | 1500000 | [ x ] | [ ] | Chuỗi số thô, chưa có đơn vị tiền tệ hay mục đích |
| 4 | Tổng doanh thu tiền khám bệnh trong ngày là 15.000.000 VNĐ | [ ] | [ x ] | Số liệu đã qua xử lý (tổng hợp), có đầy đủ ngữ cảnh thời gian và đơn vị mang lại ý nghĩa quản lý |
| 5 | BN001, Trần Thị B, 45, Nữ | [ x ] | [ ] | Các mảnh dữ liệu thô rời rạc, chưa ghép thành câu hoặc chưa rõ mục đích sử dụng cụ thể |

---

## Bước 2: Khảo sát môi trường và xác định Stakeholders

### 1. Phân loại môi trường
| Yếu tố khảo sát tại phòng khám | Thuộc loại môi trường | Tầm ảnh hưởng đến hệ thống |
| :--- | :--- | :--- |
| Kỹ năng máy tính của y tá | Môi trường Nội bộ | Giao diện phần mềm cần đơn giản, dễ thao tác |
| Quy định bảo mật của Bộ Y tế | Môi trường Bên ngoài | Hệ thống bắt buộc phải tuân thủ quy chuẩn pháp lý |
| Hạ tầng mạng nội bộ phòng khám | Môi trường Nội bộ | Ảnh hưởng đến tốc độ vận hành phần mềm |
| Ý kiến phản hồi từ bệnh nhân | Môi trường Bên ngoài | Góp phần cải thiện UI/UX và bổ sung tính năng mới bám sát nhu cầu thực tế |
| Ứng dụng đặt khám từ đối thủ | Môi trường Bên ngoài | Đòi hỏi hệ thống phải có tính cạnh tranh, giao diện mượt mà hoặc tính năng vượt trội để giữ chân bệnh nhân |

### 2. Xác định Stakeholders
| Nhóm Stakeholder | Vai trò trong dự án | Mối quan tâm lớn nhất đối với phần mềm |
| :--- | :--- | :--- |
| **1. Bác sĩ khám bệnh** | Người dùng chuyên môn | Tra cứu nhanh lịch sử bệnh án và kê đơn thuốc tiện lợi |
| **2. Bệnh nhân** | Người thụ hưởng dịch vụ | Đặt lịch khám dễ dàng, không phải chờ đợi lâu |
| **3. Nhân viên tiếp tân** | Người dùng vận hành trực tiếp | Thao tác check-in nhanh gọn, chống trùng lịch hẹn và quản lý trạng thái phòng chờ chính xác |

---

## Bước 3: Lựa chọn kỹ thuật thu thập yêu cầu và soạn câu hỏi mẫu

### 1. Kỹ thuật thu thập yêu cầu
| STT | Tình huống khảo sát thực tế | Kỹ thuật phù hợp nhất | Lý do lựa chọn ngắn gọn |
| :--- | :--- | :--- | :--- |
| 1 | Tìm hiểu mục tiêu chiến lược và ngân sách từ Giám đốc phòng khám | Phỏng vấn (Interview) | Số lượng người ít, cần trao đổi sâu và chi tiết |
| 2 | Thu thập ý kiến từ hơn 1.000 bệnh nhân về sự tiện lợi khi đặt lịch hẹn | Bảng câu hỏi / Khảo sát (Survey) | Số lượng người dùng lớn, thu thập nhanh số liệu định lượng |
| 3 | Xem thực tế quy trình tiếp đón và phát số thứ tự tại quầy tiếp tân | Quan sát (Observation) | Nắm bắt chính xác nghiệp vụ thực tế và phát hiện các "nút thắt" thời gian thực |
| 4 | Nắm rõ quy định về biểu mẫu phiếu khám bệnh và danh mục thuốc | Nghiên cứu tài liệu (Document Analysis) | Biểu mẫu và quy chế là tài liệu có sẵn, mang tính chuẩn mực pháp lý |
| 5 | Tìm hiểu mong muốn sắp xếp ca trực của đội ngũ 20 y tá | Bảng câu hỏi / Khảo sát (Survey) | Tiết kiệm thời gian so với phỏng vấn 1-1, dễ dàng tổng hợp mong muốn chung của số đông |

### 2. Câu hỏi phỏng vấn mẫu dành cho Bác sĩ
* "Thầy/Cô đang gặp những khó khăn lớn nhất nào khi **tra cứu lại lịch sử khám bệnh và đơn thuốc cũ của bệnh nhân trong những khung giờ phòng khám đông người?**"

---

## Bước 4: Phân loại Yêu cầu Chức năng (FR) và Phi chức năng (NFR)

| STT | Phát biểu yêu cầu | Phân loại | Mã định danh | Câu hỏi cốt lõi giải thích |
| :--- | :--- | :--- | :--- | :--- |
| (1) | Bệnh nhân có thể đặt lịch khám theo bác sĩ trên website | FR | FR-01 | Đây là hành động/tính năng hệ thống LÀM GÌ |
| (2) | Thời gian tải trang hiển thị lịch khám không quá 2 giây | NFR | NFR-01 | Tiêu chuẩn hiệu năng: hệ thống chạy TỐT NHƯ THẾ NÀO |
| (3) | Mật khẩu tài khoản phải được mã hóa bảo mật khi lưu trữ | NFR | NFR-02 | Tiêu chuẩn an toàn: bảo mật TỐT NHƯ THẾ NÀO |
| (4) | Bác sĩ có thể nhập kết quả chẩn đoán và kê đơn thuốc điện tử | FR | FR-02 | Đây là tính năng cốt lõi (hành động cụ thể) mà hệ thống bắt buộc phải LÀM ĐƯỢC |
| (5) | Hệ thống phải hoạt động liên tục và ổn định 24/7 | NFR | NFR-03 | Tiêu chuẩn về tính khả dụng và độ tin cậy: hệ thống duy trì hoạt động TỐT NHƯ THẾ NÀO |

---

## Bước 5: Đặc tả User Story chuẩn ba thành phần

**Đặc tả User Story dành cho Bác sĩ:**
*   **Là một:** Bác sĩ khám bệnh
*   **Tôi muốn:** Xem danh sách bệnh nhân đã đăng ký khám trong ngày
*   **Để:** Có thể chủ động phân bổ thời gian, xem trước hồ sơ bệnh án nhằm giúp quá trình chẩn đoán diễn ra nhanh chóng và chính xác.