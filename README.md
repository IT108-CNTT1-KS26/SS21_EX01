# BÀI LÀM: TỐI ƯU TỪ KHÓA KHI TÌM KIẾM TÀI LIỆU KỸ THUẬT

### 1. Phân tích lý do truy vấn hiện tại là "Bad Query" (Gây nhiễu)
Truy vấn của sinh viên: `"thầy ơi cho em xin tài liệu học html cơ bản của trang mozilla với ạ"`

* **Chứa quá nhiều từ dừng (Stop words) và ngôn ngữ hội thoại:** Các từ như *"thầy ơi"*, *"cho em xin"*, *"với ạ"* mang tính giao tiếp người-người, không mang giá trị ngữ nghĩa kỹ thuật. Công cụ tìm kiếm vẫn có thể quét các từ này và trả về các bài viết trên mạng xã hội, diễn đàn hỏi đáp, hoặc các bài blog tâm sự thay vì tài liệu kỹ thuật.
* **Thiếu tính định danh mục tiêu nguồn:** Cụm từ *"trang mozilla"* được hiểu là từ khóa văn bản thông thường chứ không ràng buộc công cụ tìm kiếm chỉ lấy kết quả từ máy chủ/tên miền của Mozilla. Do đó, các trang web bên thứ ba viết về Mozilla, các trang khóa học trả phí gắn tag "Mozilla" hoặc bài viết SEO quảng cáo vẫn xuất hiện tràn lan.
* **Không loại trừ các nội dung thương mại:** Từ khóa mang tính "xin tài liệu học" rất dễ kích hoạt các thuật toán chạy quảng cáo (Google Ads) từ các trung tâm đào tạo lập trình hoặc các khóa học mất phí.

---

### 2. Viết lại truy vấn tối ưu

**Truy vấn đề xuất:**
```text
site:developer.mozilla.org html basic -ad -course -paid
```
*(Hoặc dạng tiếng Việt/ngắn gọn hơn:)*
```text
site:developer.mozilla.org html cơ bản -quảng_cáo -khóa_học
```

**Thành phần câu lệnh:**
* `site:developer.mozilla.org`: Khoanh vùng tìm kiếm tuyệt đối bên trong tên miền chính thức của Mozilla Developer Network (MDN).
* `html basic` (hoặc `html cơ bản`): Từ khóa kỹ thuật cốt lõi cần tra cứu.
* `-ad -course -paid` (hoặc `-khóa_học`): Sử dụng toán tử loại trừ để triệt tiêu các bài viết giới thiệu khóa học dịch vụ hoặc quảng cáo đi kèm.

---

### 3. Ý nghĩa của việc sử dụng các toán tử tìm kiếm

* **Toán tử `site:`**:
  * Giúp giới hạn phạm vi tìm kiếm vào duy nhất một tên miền hoặc máy chủ cụ thể (`developer.mozilla.org`).
  * Loại bỏ 100% kết quả từ các trang web rác, diễn đàn không chính thống hoặc các website sao chép nội dung (content farm).
  * Tiết kiệm thời gian rà soát giữa hàng triệu kết quả trôi nổi trên internet.

* **Toán tử `-` (Loại trừ):**
  * Buộc công cụ tìm kiếm loại bỏ bất kỳ trang nào chứa từ khóa đứng ngay sau dấu trừ (ví dụ `-ad`, `-khóa_học`).
  * Giúp làm sạch trang kết quả, ngăn chặn các nội dung mang tính thương mại, khóa học trả phí hoặc tài liệu không đúng nhu cầu thực tế.

* **Tối ưu hóa thời gian:** Kết hợp hai toán tử này giúp nhà phát triển đi thẳng tới nguồn tài liệu chuẩn mực (Standard/Official Documentation) ngay ở trang kết quả đầu tiên mà không mất thời gian click vào các đường link không liên quan.
