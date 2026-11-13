# BÀI 9: TRÍCH XUẤT PHIẾU BÁO HỎNG THIẾT BỊ THÀNH MARKDOWN TABLE 4 CỘT

## PHẦN 1. XÁC ĐỊNH YÊU CẦU BÀI TẬP

### 1.1. Bài tập yêu cầu làm gì?

TechShop nhận được nhiều tin nhắn báo hỏng thiết bị từ khách hàng qua Zalo. Nội dung tin nhắn thường viết tự do, không theo một mẫu cố định.

Bài tập yêu cầu sử dụng AI để đọc các tin nhắn, lấy thông tin cần thiết và chuyển thành bảng Markdown gồm 4 cột để dễ dàng quản lý.

### 1.2. Các kỹ thuật sử dụng

- **Markdown Table:** Trình bày dữ liệu dưới dạng bảng có hàng và cột.
- **Delimiters:** Sử dụng dấu phân cách để xác định nội dung cần AI đọc.
- **Negative Constraints:** Quy định những nội dung AI không được xuất ra, ví dụ lời chào hỏi và giải thích.
- **Data Extraction:** Trích xuất thông tin cần thiết từ văn bản.

## PHẦN 2. XÂY DỰNG PROMPT TRÍCH XUẤT DỮ LIỆU

### 2.1. Prompt hoàn chỉnh

```text
VAI TRÒ:
Bạn là trợ lý AI của trung tâm bảo hành TechShop.

NHIỆM VỤ:
Đọc các tin nhắn báo hỏng thiết bị của khách hàng
và trích xuất thông tin thành bảng Markdown gồm 4 cột.

DỮ LIỆU ĐẦU VÀO:

<<<BAT_DAU_TIN_NHAN>>>

[Dán các tin nhắn báo hỏng của khách hàng vào đây]

<<<KET_THUC_TIN_NHAN>>>

CẤU TRÚC BẢNG BẮT BUỘC:

| Mã đơn hàng | Khách hàng & Khu vực |
| Thiết bị & Lỗi phát sinh | Mức độ ưu tiên |

YÊU CẦU TRÍCH XUẤT:

1. Mã đơn hàng:
- Lấy đúng mã đơn hàng trong tin nhắn.

2. Khách hàng & Khu vực:
- Lấy tên khách hàng và khu vực sinh sống.

3. Thiết bị & Lỗi phát sinh:
- Ghi tên thiết bị và mô tả lỗi.
- Giữ lại các thông tin quan trọng.

4. Mức độ ưu tiên:
- Gấp: Khách cần sửa ngay hoặc trong hôm nay.
- Bình thường: Khách có thể chờ trong thời gian ngắn.
- Thấp: Khách không vội, có thể chờ nhiều ngày.

RÀNG BUỘC:

- Chỉ lấy thông tin có trong tin nhắn.
- Không tự ý thêm thông tin.
- Mỗi tin nhắn tương ứng một hàng trong bảng.
- Không bỏ sót tin nhắn.
- Nếu thiếu thông tin, ghi "Không rõ".
- Chỉ sử dụng 3 mức ưu tiên: Gấp, Bình thường, Thấp.

NEGATIVE CONSTRAINTS:

- Không chào hỏi.
- Không giải thích kết quả.
- Không viết lời mở đầu hoặc kết luận.
- Không thêm nội dung ngoài bảng.
- Không tự ý thay đổi tên 4 cột.
- Không tạo thêm cột mới.

ĐẦU RA:
Chỉ xuất duy nhất một bảng Markdown hợp lệ gồm 4 cột.
```

### 2.2. Giải thích Prompt

| Thành phần | Ý nghĩa |
|---|---|
| Vai trò | Xác định AI là trợ lý bảo hành. |
| Nhiệm vụ | Yêu cầu AI trích xuất thông tin. |
| Delimiters | Phân cách phần tin nhắn đầu vào. |
| Cấu trúc bảng | Quy định 4 cột bắt buộc. |
| Quy tắc | Hướng dẫn cách lấy và phân loại dữ liệu. |
| Negative Constraints | Ngăn AI thêm lời chào hoặc giải thích. |

## PHẦN 3. PHÂN TÍCH TIN NHẮN MẪU

### 3.1. Tin nhắn 1

- Khách hàng: Hoàng.
- Khu vực: Quận 7.
- Mã đơn hàng: DH-8812.
- Thiết bị: Laptop Asus TUF.
- Lỗi: Màn hình xanh, sập nguồn liên tục.
- Thời gian: Cần sửa trong hôm nay.
- Ưu tiên: Gấp.

### 3.2. Tin nhắn 2

- Khách hàng: Linh.
- Khu vực: Bình Thạnh.
- Mã đơn hàng: DH-9921.
- Thiết bị: Tai nghe Sony.
- Lỗi: Bên tai phải nghe nhỏ hơn bên tai trái.
- Thời gian: Tuần sau lấy cũng được.
- Ưu tiên: Thấp.

### 3.3. Tin nhắn 3

- Khách hàng: Minh.
- Khu vực: Tân Bình.
- Mã đơn hàng: DH-7734.
- Thiết bị: Chuột Logitech.
- Lỗi: Double click, bấm một lần thành hai lần.
- Thời gian: Không đề cập.
- Ưu tiên: Bình thường.

## PHẦN 4. KẾT QUẢ OUTPUT MARKDOWN TABLE

| Mã đơn hàng | Khách hàng & Khu vực | Thiết bị & Lỗi phát sinh | Mức độ ưu tiên |
|---|---|---|---|
| DH-8812 | Hoàng - Quận 7 | Laptop Asus TUF - Màn hình xanh, sập nguồn liên tục | Gấp |
| DH-9921 | Linh - Bình Thạnh | Tai nghe Sony - Bên tai phải nghe nhỏ hơn bên tai trái | Thấp |
| DH-7734 | Minh - Tân Bình | Chuột Logitech - Bị double click, bấm một lần thành hai lần | Bình thường |

## PHẦN 5. KẾT LUẬN

Qua bài tập, em đã hiểu cách sử dụng Prompt để chuyển các tin nhắn báo hỏng không có cấu trúc thành bảng dữ liệu dễ quản lý.

Em đã thực hiện:

- Sử dụng Delimiters để xác định nội dung đầu vào.
- Sử dụng Negative Constraints để loại bỏ lời chào và nội dung thừa.
- Trích xuất thông tin khách hàng, mã đơn hàng và lỗi thiết bị.
- Phân loại mức độ ưu tiên thành Gấp, Bình thường và Thấp.
- Tạo bảng Markdown gồm đúng 4 cột theo yêu cầu.
