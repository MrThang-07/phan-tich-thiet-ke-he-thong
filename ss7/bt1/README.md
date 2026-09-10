# BÀI TẬP: THIẾT KẾ ĐÓNG GÓI LỚP HỌC VIÊN (RIKKEI LEARN)

## Phần 1 - Cập nhật sơ đồ Lớp (Class Diagram)

Dưới đây là sơ đồ lớp `Student` đã được bổ sung các Bổ từ truy cập (Access Modifiers) chuẩn xác nhằm bảo mật thông tin hồ sơ theo đúng yêu cầu đề bài:
* Các thuộc tính được thiết lập Private (`-`) để cấm truy cập trực tiếp từ bên ngoài.
* Các phương thức được thiết lập Public (`+`) để làm kênh giao tiếp hợp lệ.

<img src="./Biểu đồ không có tiêu đề.drawio (1).png" alt="Sơ đồ Class Diagram Student" width="500">

---

## Phần 2 - Mô tả logic cập nhật điểm an toàn trong setScore()

Để đảm bảo tính toàn vẹn dữ liệu, thuộc tính `averageScore` đã được đóng gói (Encapsulation). Việc cập nhật điểm bắt buộc phải đi qua phương thức "gác cổng" là `setScore(score: float)`. 

Dưới đây là logic mã giả (Pseudocode) để chặn việc gán điểm âm hoặc lớn hơn 10:

```text
BẮT ĐẦU PHƯƠNG THỨC setScore(score: float)

    // Kiểm tra xem tham số điểm (score) truyền vào có nằm trong dải [0, 10] không
    NẾU (score >= 0.0) VÀ (score <= 10.0) THÌ
        // Hợp lệ -> Tiến hành cập nhật dữ liệu cho thuộc tính của lớp
        this.averageScore = score
        IN RA: "Cập nhật điểm thành công."
        
    NGƯỢC LẠI
        // Bị kẹt lại ở cổng kiểm tra -> Báo lỗi và từ chối cập nhật
        IN RA LỖI: "Cập nhật thất bại. Điểm số phải nằm trong khoảng từ 0 đến 10!"
        
    KẾT THÚC NẾU
    
KẾT THÚC PHƯƠNG THỨC