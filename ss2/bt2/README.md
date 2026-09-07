# Báo cáo Phân tích Stakeholder Hồ sơ EHR RikkeiCare

## Phần 1 - Thanh lọc danh sách & Loại bỏ thực thể kỹ thuật

Dựa trên nguyên tắc quản trị dự án, Stakeholder phải là các cá nhân, nhóm người hoặc tổ chức có quyền lợi/ảnh hưởng đến dự án. Do đó:

*   **Thực thể kỹ thuật (Cần loại bỏ):** `Máy chủ cơ sở dữ liệu Oracle`. Máy chủ chỉ là công cụ, hạ tầng phần cứng, không có khả năng ra quyết định hay có "nhu cầu", nên không phải là Stakeholder. Đề xuất của nhóm cũ (đưa máy chủ vào Manage Closely) là sai kiến thức nền tảng.
*   **Stakeholder thực thụ (Giữ lại):** 
    1. Bác sĩ điều trị trực tiếp.
    2. Ban Giám đốc Bệnh viện RikkeiCare.
    3. Bệnh nhân và Thân nhân người bệnh.
    4. Thanh tra Pháp chế & Bảo mật Y tế (Bộ Y tế).

---

## Phần 2 - Điền khuyết Ma trận Stakeholder 4 ô

| Nhóm chiến lược | Tiêu chí | Stakeholder | Hành động tương tác chủ chốt |
| :--- | :--- | :--- | :--- |
| **Quản lý chặt chẽ (Manage Closely)** | Quyền lực Cao - Quan tâm Cao | Ban Giám đốc Bệnh viện | Báo cáo tiến độ trực tiếp, tham gia mọi quyết định lớn |
| **Giữ hài lòng (Keep Satisfied)** | Quyền lực Cao - Quan tâm Thấp | **Thanh tra Pháp chế & Bảo mật Y tế (Bộ Y tế)** | **Đảm bảo hệ thống tuân thủ 100% luật y tế; cung cấp báo cáo kiểm toán bảo mật khi có đợt thanh tra; không cần làm phiền họ bằng các chi tiết kỹ thuật hằng ngày.** |
| **Giữ thông tin (Keep Informed)** | Quyền lực Thấp - Quan tâm Cao | **Bác sĩ điều trị trực tiếp** | **Tổ chức demo, đào tạo sử dụng phần mềm, liên tục cập nhật các tính năng mới và lấy ý kiến phản hồi để tối ưu UI/UX (vì họ là người dùng cuối trực tiếp).** |
| **Giám sát tối thiểu (Monitor)** | Quyền lực Thấp - Quan tâm Thấp | Bệnh nhân và Thân nhân | Thông báo định kỳ qua email/app, không cần họp riêng |

---

## Phần 3 - Giải pháp dung hòa xung đột (Bảo mật vs. Tiện ích cấp cứu)

Để giải quyết mâu thuẫn giữa Bác sĩ và Cán bộ Pháp chế, hệ thống cần áp dụng giải pháp kép:
1.  **Luồng tiêu chuẩn (Cho Pháp chế):** Vẫn yêu cầu mã xác nhận (Consent) từ bệnh nhân đối với các trường hợp khám chữa bệnh thông thường để đảm bảo bảo mật thông tin nhạy cảm.
2.  **Luồng ngoại lệ (Cho Bác sĩ):** Thiết lập cơ chế **Cấp quyền khẩn cấp (Emergency Override)** (phá vỡ rào cản xác thực) để Bác sĩ có thể mở ngay hồ sơ bệnh án khi bệnh nhân rơi vào tình trạng cấp cứu, hôn mê. Để đảm bảo tính minh bạch pháp lý, hệ thống bắt buộc phải tự động lưu lại toàn bộ hành động này vào **Nhật ký kiểm toán (Audit Log)** để phục vụ công tác hậu kiểm, rà soát tránh lạm dụng quyền.