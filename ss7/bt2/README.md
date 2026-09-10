# BÀI TẬP: KHỬ QUAN HỆ NHIỀU-NHIỀU BẰNG ASSOCIATION CLASS (RIKKEI LEARN)

## 1. Báo cáo giải trình thiết kế và Bội số (Multiplicity)

### Phân rã quan hệ nhiều-nhiều (n-n)
Trong thiết kế ban đầu, mối quan hệ trực tiếp giữa `Student` và `Course` là nhiều-nhiều (`* -- *`). Thiết kế này gặp hạn chế lớn về mặt cơ sở dữ liệu: không thể lưu trữ các thông tin phát sinh từ chính sự kiện giao dịch (ví dụ: ngày đăng ký cụ thể của ai vào khóa học nào). 

Để giải quyết triệt để, ta áp dụng kỹ thuật Association Class: 
* Xóa bỏ đường nối trực tiếp giữa 2 lớp.
* Chèn thêm một Lớp trung gian tên là `Enrollment` ở giữa.
* Thêm thuộc tính `- enrollDate: Date` vào Lớp `Enrollment` để lưu trữ ngày đăng ký.

### Giải trình Bội số (Multiplicity)
Đường nối `* -- *` ban đầu được phân rã thành hai đường nối một-nhiều (`1 -- 0..*`) tuân thủ nghiêm ngặt các quy tắc nghiệp vụ:

* **Từ Student sang Enrollment (`1 -- 0..*`):**
  * Theo bẫy dữ liệu, học viên mới tạo tài khoản có thể chưa đăng ký khóa nào. Nếu có học, họ có thể học nhiều khóa $\rightarrow$ Bội số tại đầu `Enrollment` là **`0..*`**.
  * Ngược lại, mỗi một phiếu đăng ký (`Enrollment`) bắt buộc phải là của đích danh 1 học viên duy nhất $\rightarrow$ Bội số tại đầu `Student` là **`1`**.

* **Từ Course sang Enrollment (`1 -- 0..*`):**
  * Tương tự, khóa học mới mở có thể chưa có ai đăng ký, tối đa thì có vô số học viên $\rightarrow$ Bội số tại đầu `Enrollment` là **`0..*`**.
  * Một phiếu đăng ký (`Enrollment`) bắt buộc phải ghi danh cho đích danh 1 khóa học cụ thể $\rightarrow$ Bội số tại đầu `Course` là **`1`**.

---

## 2. Sơ đồ Class Diagram hoàn chỉnh (TO-BE)

Dưới đây là sơ đồ lớp đã được chuẩn hóa để lưu trữ dữ liệu an toàn:

<img src="./Biểu đồ không có tiêu đề.drawio (2).png" alt="Sơ đồ Class Diagram khử n-n" width="600">

