<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: MÔ TẢ API ĐĂNG KÝ KHÁM ONLINE - MEDPRO

</div>

###### :eight_spoked_asterisk: Người lập: [**LÊ QUỐC THỐNG**](https://github.com/lequocthong29)

###### :eight_spoked_asterisk: Ngày lập: **24/06/2024**

###### :eight_spoked_asterisk: HIS_URL

- his_url: được cấp tùy theo IP bệnh viện

###### :eight_spoked_asterisk: API
1. GET TOKEN
-  URL: ${HIS_URL}/api/v1/token
-  METHOD: POST
-  REQUEST HEADER:
-  REQUEST:
```cshap
{
  "username": "usermr",
  "password": "123"
}
```
- RESPONSE:
```cshap
{
"token":"eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6ImFkbWluIiwicGFzc3dvcmQiOiIxMjMiLCJuYmYiOjE2NzkyNzc0OTUsImV4cCI6MTY3OTI4MTA5NSwiaWF0IjoxNjc5Mjc3NDk1fQ.YNlHDQEfe2C8m4Zymnnfi5roo7OWbWVbEMv31k5_pYDu8IJgodrOv-3c_ygph4hiXicZUyjr35lA_ebPOfQpSQ"
}
```

2. GET CHUYÊN KHOA
-  URL: ${HIS_URL}/api/v1/subjects
-  METHOD: GET
-  REQUEST HEADER: Authorization Bearer <token>.
-  REQUEST:
-  RESPONSE:
```cshap
{
    "data": [
        {
            "code": "17",
            "name": "Bỏng"
        }, ...
     ]
}
```

3. GET BÁC SĨ
-  URL: ${HIS_URL}/api/v1/doctors
-  METHOD: GET
-  REQUEST HEADER: Authorization Bearer <token>.
-  REQUEST:
-  RESPONSE:
```cshap
{
    "data": [
        {
            "code": "001",
            "name": "BSCKII.Nguyễn Thụy Thúy Ái",
            "sex": "Nu"
        },…
     ]
}
```

4. GET PHÒNG KHÁM
-  URL: ${HIS_URL}/api/v1/rooms
-  METHOD: GET
-  REQUEST HEADER: Authorization Bearer <token>.
-  REQUEST:
-  RESPONSE:
```cshap
{
    "data": [
        {
            "code": "14",
            "name": "Kho thuốc Dược "
        }, …
     ]
}
```

5. GET DỊCH VỤ
-  URL: ${HIS_URL}/api/v1/services
-  METHOD: GET
-  REQUEST HEADER: Authorization Bearer <token>.
-  REQUEST:
-  RESPONSE:
```cshap
{
    "data": [
        {
            "code": "CO29",
            "name": "Công khám dịch vụ (Chọn bác sĩ)"
        }, ...
    ]
}
```

6. TẠO HỒ SƠ BỆNH NHÂN
-  URL: ${HIS_URL}/api/v1/patients
-  METHOD: POST
-  REQUEST HEADER: Authorization Bearer <token>.
-  REQUEST:
```cshap
{
    "mabn":"2022032198"  // mã bệnh nhân (nếu có: cập nhật hồ sơ/
                                               không có : tạo hồ sơ mới)
    ,"surname": "Nguyen Van" // họ và tên lót
    ,"name": "DEMO" // tên
    ,"gender": "1" // giới tính (0:nữ, 1:nam)
    ,"dateOfBirth": "29/11/1997" //(ngày sinh : dd/mm/yyyy)
    ,"phone": "0345856666" // số điện thoại
    ,"cmnd": "334878088" // chứng minh nhân dân
    ,"address": "Cái răng, cần thơ" //địa chỉ
    ,"nationalityId": "VN" // mã quốc gia
    ,"nationId": "01" // mã dân tộc
    ,"jobid": "01" // mã nghề
    ,"wardsid": "0100100001" // mã xã
}
```
-  RESPONSE:
```cshap
{
    "code": "2022032198",  // mã bệnh nhân sau khi tạo hồ sơ thành công
    "message": "tạo hồ sơ thành công"
}
```

7. TÌM BỆNH NHÂN THEO MÃ BỆNH NHÂN
-  URL:${HIS_URL}/api/v1/getPatient/{mabn}
-  METHOD: GET
-  REQUEST HEADER: Authorization Bearer <token>.
-  REQUEST:
-  RESPONSE:
```cshap
{
    "mabn":"2022032198"  // mã bệnh nhân
    ,"surname": "Nguyen Van" // họ và tên lót
    ,"name": "DEMO" // tên
    ,"gender": "1" // giới tính (0:nữ, 1:nam)
    ,"dateOfBirth": "29/11/1997" //(ngày sinh : dd/mm/yyyy)
    ,"phone": "0345856666" // số điện thoại
    ,"cmnd": "334878088" // chứng minh nhân dân
    ,"address": "Cái răng, cần thơ" //địa chỉ
    ,"nationalityId": "VN" // mã quốc gia
    ,"nationId": "01" // mã dân tộc
    ,"jobid": "01" // mã nghề
    ,"wardsid": "0100100001" // mã xã
}
```

8. TÌM BỆNH NHÂN THEO THÔNG TIN BỆNH NHÂN
-  URL: ${HIS_URL}/api/v1/patient/detail
-  METHOD: POST
-  REQUEST HEADER: Authorization Bearer <token>.
-  REQUEST:
```cshap
{
    ,"surname":"Lê Van"
    ,"name":"A"
    ,"gender":"0" 
    ,"dateOfBirth":"1996" // năm sinh
    ,"provinceId":"01" //mã tỉnh
    ,"cmnd":""
    ,"phone":""
}
```
-  RESPONSE:
```cshap
{
    "mabn":"2022032198"  // mã bệnh nhân
    ,"surname": "Nguyen Van" // họ và tên lót
    ,"name": "DEMO" // tên
    ,"gender": "1" // giới tính (0:nữ, 1:nam)
    ,"dateOfBirth": "29/11/1997" //(ngày sinh : dd/mm/yyyy)
    ,"phone": "0345856666" // số điện thoại
    ,"cmnd": "334878088" // chứng minh nhân dân
    ,"address": "Cái răng, cần thơ" //địa chỉ
    ,"nationalityId": "VN" // mã quốc gia
    ,"nationId": "01" // mã dân tộc
    ,"jobid": "01" // mã nghề
    ,"wardsid": "0100100001" // mã xã
}
```

9. ĐẶT LỊCH KHÁM
-  URL: ${HIS_URL}/api/v1/booking
-  METHOD: POST
-  REQUEST HEADER: Authorization Bearer <token>.
-  REQUEST:
```cshap
{
  "appointments":
  {
    "number":"3",
    "specialityId":"10",
    "roomId":"Y03",
    "examType":"KH129",
    "patientType":"04",
    "date":"13/09/2024",
    "timeslot":"15:00",
    "fee":"150000"
  },
  "patient":
    {
      "hisId":"2024001575"
    },
  "orderId":"T240913TSN1PX",
  "feeAmount":"150000",
  "serviceFeeAmount":"0",
  "status":"CONFIRMED",
  "insuranceDetail":
    {
        "insuranceNumber":"GDxxxxxxxxxxx", // Mã BHYT
        "expiredDate":"24/12/2024", // ngày hết hạn BHYT
        "insuranceStatus":"valid", // Trạng thái hợp lệ của BHYT
        "hospitalId":"79037", // nơi KCB ban đầu
        "detailUrl":"aaaaaaaaaaaaaaa" // link chi tiết (hình ảnh/file giấy chuyển tuyến)
    },
  "relative":
    {
        "fullname": "NGUYỄN VĂN A",//Type:String maxlength:100 Họ tên người quan hệ
        "phone": "Số ĐT",//Type:String maxlength:100
        "CMND": "CMND/CCCD",//Type:String maxlength:100
        "address": "Địa chỉ",//Type:String maxlength:500
        "relativeType": "2",//Type:String maxlength:100 Mã mối quan hệ
        "relativeName": "Cha"//Type:String maxlength:100 Tên mối quan hệ
    }
}
```
-  RESPONSE:
```cshap
{
    "mgntHisId": "2024001575", // mã khám bệnh
    "number": "3", // số thứ tự
    "id":"1"  // id của lịch khám này
}
```

10. HỦY LỊCH KHÁM
-  URL: ${HIS_URL}/api/v1/cancelBooking/{mgntHisId}
-  METHOD: DELETE
-  REQUEST HEADER: Authorization Bearer <token>.
-  REQUEST:
-  RESPONSE:
```cshap
{
    "mgntHisId": "2303104712" //mã khám bệnh của lịch khám đã hủy thành công
}
```

11. GET QUỐC GIA
-  URL: ${HIS_URL}/api/v1/nationalities
-  METHOD: GET
-  REQUEST HEADER: Authorization Bearer <token>.
-  REQUEST:
-  RESPONSE:
```cshap
{
    "data": [
        {
            "code": "AC",
            "name": "Ai Cập"
        }, ...
     ]
}
```

12. GET TỈNH - TP
-  URL: ${HIS_URL}/api/v1/cities
-  METHOD: GET
-  REQUEST HEADER: Authorization Bearer <token>.
-  REQUEST:
-  RESPONSE:
```cshap
{
    "data": [
        {
            "code": "89",
            "name": "An Giang"
        }, ...
     ]
}
```

13. GET HUYỆN
-  URL: ${HIS_URL}/api/v1/districts/{cityid}
-  METHOD: GET
-  REQUEST HEADER: Authorization Bearer <token>.
-  REQUEST:
-  RESPONSE:
```cshap
{
    "data": [
        {
            "code": "89886",
            "name": "Huyện An Phú"
        }, ...
     ]
}
```

14. GET XÃ
-  URL: ${HIS_URL}/api/v1/wards/{districtid}
-  METHOD: GET
-  REQUEST HEADER: Authorization Bearer <token>.
-  REQUEST:
-  RESPONSE:
```cshap
{
    "data": [
        {
            "code": "7775026575",
            "name": "Thị trấn Ngãi Giao"
        }, ...
     ]
}
```

15. GET DÂN TỘC
-  URL: ${HIS_URL}/api/v1/nations
-  METHOD: GET
-  REQUEST HEADER: Authorization Bearer <token>.
-  REQUEST:
-  RESPONSE:
```cshap
{
    "data": [
        {
            "code": "04",
            "name": "Chăm"
        }, ...
     ]
}
```

###### :eight_spoked_asterisk: HƯỚNG DẪN CÀI ĐẶT SERVICE
1. Đảm bảo server cài đặt service có cài đặt NODE.JS
2. Tải file cài đặt: [Tại đây](https://i.imgur.com/54Cs8S9.png)
3. Giải nén file vừa tải về, mở file .env
   ![](https://i.imgur.com/nGyMseW.png)
4. Tại thư mục vừa giải nén file, mở cmd chạy câu lệnh `myapp.exe install` để cài đặt và `myapp.exe start` để chạy service.
   ![](https://i.imgur.com/00wqd4A.png)
5. Mở port: Truy cập vào Windows Defender Firewall -> Advanced settings. Tại cửa sổ Windows Defender Firewall with Advanced security tiến hành mở port.
   ![](https://i.imgur.com/3TTgzgF.png)
   ![](https://i.imgur.com/Uh0HD8K.png)
   ![](https://i.imgur.com/Yd49M13.png)
   ![](https://i.imgur.com/gAzhm4e.png)
   ![](https://i.imgur.com/Cj2EI3W.png)
   
   




