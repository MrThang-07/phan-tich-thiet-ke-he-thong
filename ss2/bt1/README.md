# Báo cáo Hiệu chỉnh Yêu cầu Kho Dược RikkeiCare

## Phần 1 - Bóc tách lỗi sai nghiệp vụ (Sửa lỗi)

### 1. Môi trường hệ thống
* **Nguyên nhân sai:** Thông tư của Bộ Y tế là quy định pháp lý vĩ mô nằm ngoài khả năng tự kiểm soát và thay đổi của bệnh viện, do đó nó phải là Môi trường Bên ngoài.
* **Hậu quả nghiệp vụ:** Nếu xem nhẹ đây là yếu tố nội bộ, đội ngũ phát triển có thể thiết kế hệ thống thiếu tính tuân thủ pháp luật, dẫn đến rủi ro bệnh viện bị phạt hoặc tước giấy phép hoạt động.

### 2. Khảo sát quy trình AS-IS
* **Nguyên nhân sai:** Việc quản lý rủi ro y tế phụ thuộc vào "trí nhớ của con người" là hoàn toàn phi thực tế và phản khoa học, phớt lờ sự thật là đã có bệnh nhân khiếu nại.
* **Hậu quả nghiệp vụ:** Nếu không số hóa việc kiểm soát hạn sử dụng, phần mềm sẽ không có tính năng cảnh báo, dẫn đến nguy cơ tiếp tục xuất nhầm thuốc hết hạn, đe dọa tính mạng bệnh nhân.

### 3. Phân loại yêu cầu
* **Nguyên nhân sai:** Hành động "tự động khóa" là một chức năng, một thao tác xử lý bắt buộc phần mềm phải thực thi được, nên nó phải được xếp vào Yêu cầu Chức năng (FR).
* **Hậu quả nghiệp vụ:** Đội ngũ thiết kế (Dev) có thể hiểu nhầm đây chỉ là ràng buộc phụ và bỏ sót tính năng này, khiến hệ thống mất đi chốt chặn an toàn cốt lõi của kho dược.

---

## Phần 2 - Điền khuyết Bảng Phân loại Môi trường & Yêu cầu

### Bảng Phân loại Môi trường

| Yếu tố khảo sát tại Kho Dược | Thuộc loại Môi trường | Tác động trực tiếp đến phần mềm |
|---|---|---|
| Kỹ năng vi tính & thói quen ghi sổ của Dược sĩ | Môi trường Nội bộ | Cần giao diện tối giản, hỗ trợ quét mã vạch |
| Thông tư & Chế tài xử phạt của Bộ Y tế | Môi trường Bên ngoài | Bắt buộc khóa tự động thuốc hết hạn, lưu audit log |
| **Hạ tầng máy chủ và mạng LAN nội bộ bệnh viện** | **Môi trường Nội bộ** | **Yêu cầu mạng ổn định và bảo mật tuyệt đối để đảm bảo cơ chế xác nhận kép (Dual-Authorization) khi xuất thuốc nhóm RESTRICTED không bị gián đoạn hay giả mạo.** |

### Đặc tả Yêu cầu Chức năng (FR) và Phi chức năng (NFR)

* **Yêu cầu Chức năng (FR):** 
  Hệ thống bắt buộc phải gửi yêu cầu và chờ phê duyệt thông qua cơ chế xác nhận kép (Dual-Authorization) từ tài khoản của Dược sĩ Trưởng khoa mỗi khi có lệnh xuất kho đối với nhóm thuốc kiểm soát đặc biệt (RESTRICTED).

* **Yêu cầu Phi chức năng (NFR):** 
  Thời gian hệ thống xử lý và phản hồi cho thao tác phê duyệt xác nhận kép (Dual-Authorization) của Dược sĩ Trưởng khoa không được vượt quá 2 giây, đảm bảo không làm chậm trễ quy trình cấp cứu/phát thuốc.