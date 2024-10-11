# API Data Căn Cước

## 1. Service đọc thẻ căn cước công dân

Service đọc căn cước với giao thức **SocketIo Server** ở địa chỉ IP: `http://192.168.5.1:8000`, bắn dữ liệu qua channel `/event`. Có 4 sự kiện (event) chính sau:

### 1.1. Sự kiện có thẻ quét

**Payload:**

```json
{
  "id": 1,
  "message": "new card!"
}
```

### 1.2. Sự kiện đọc thẻ thành công với dữ liệu text

**Payload:**

```json
{
  "id": 2,
  "message": "read card successfully!",
  "data": {
    "idCode": "{String}", // Số căn cước 12 số
    "oldIdCode": "{String}", // Số chứng minh 9 số
    "personName": "{String}", // Họ tên
    "dateOfBirth": "{String}", // Ngày sinh
    "gender": "{String}", // Giới tính
    "nationality": "{String}", // Quốc tịch
    "race": "{String}", // Dân tộc
    "religion": "{String}", // Tôn giáo
    "originPlace": "{String}", // Quê quán
    "residencePlace": "{String}", // Địa chỉ thường trú
    "personalIdentification": "{String}", // Đặc điểm nhận dạng
    "issueDate": "{String}", // Ngày phát hành thẻ
    "expiryDate": "{String}", // Ngày hết hạn
    "fatherName": "{String}", // Họ tên bố
    "motherName": "{String}", // Họ tên mẹ
    "wifeName": "{String}" // Họ tên vợ/chồng (nếu có)
  }
}
```

### 1.3. Sự kiện đọc thẻ thành công với dữ liệu ảnh và dữ liệu raw các phân vùng

**Payload:**

```json
{
  "id": 4,
  "message": "Read raw data successfully!",
  "data": {
    "img_data": "{Base64 string}", // Ảnh chân dung
    "dg2": "{Base64 string}", // Dữ liệu raw phân vùng DG2
    "dg13": "{Base64 string}", // Dữ liệu raw phân vùng DG13
    "dg14": "{Base64 string}", // Dữ liệu raw phân vùng DG14
    "dg15": "{Base64 string}", // Dữ liệu raw phân vùng DG15
    "sod": "{Base64 string}" // Dữ liệu raw phân vùng SOD
  }
}
```

### 1.4. Sự kiện quét thẻ thất bại

**Payload:**

```json
{
  "id": 3,
  "message": "{String}" // Thông tin lỗi
}
```

## 2. Service đọc webcam

Service đọc ảnh webcam với giao thức **SocketIo Server** ở địa chỉ IP: `http://192.168.5.1:9000`, bắn dữ liệu qua channel `/image`.

**Payload:**

```json
{
  "data": "{Base64 string}" // Ảnh từ camera
}
```

## 3. Sự kiện lấy Serial Number của thiết bị

Sử dụng giao thức **SocketIo Server** ở địa chỉ IP: `http://192.168.5.1:8000`, bắn dữ liệu qua channel `/info`.
