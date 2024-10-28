<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: MÔ TẢ API ĐĂNG KÝ KHÁM ONLINE - YOUMED

</div>

###### :eight_spoked_asterisk: Người lập: [**LÊ QUỐC THỐNG**](https://github.com/lequocthong29)

###### :eight_spoked_asterisk: Ngày lập: **28/10/2024**

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

2. TẠO HỒ SƠ
-  URL: ${HIS_URL}/api/v1/patients
-  METHOD: POST
-  REQUEST HEADER: Authorization Bearer <token>.
-  REQUEST:
```cshap
{
   "lastname":"LE VAN",  //not null
   "name":"DEMO",  //not null
   "gender":"0",  //not null
   "nationalityId":"VN",
   "nationId":"01",
   "jobid":"99",
   "dateOfBirth":"29/11/1997",  //not null
   "phone":"0340001111",  //not null
   "address":"CanTho" 
}
```
-  RESPONSE:
```cshap
{
    "hisId": "2023003264"
}
```

3. TÌM KIẾM HỒ SƠ THÔNG QUA MÃ BỆNH NHÂN
-  URL: ${HIS_URL}/api/v1/patients?hisId=
-  METHOD: GET
-  REQUEST HEADER: Authorization Bearer <token>.
-  REQUEST:
```cshap
hisId = 20230011  //not null
```
-  RESPONSE:
```cshap
{
    "id": "20230012345",
    "lastname": "LE VAN",
    "name": "DEMO",
    "gender": "0",
    "dateOfBirth": "11/29/1997 12:00:00 AM",
    "phone": "0340001111",
    "address": "CanTho"
}
```


4. TÌM KIẾM HỒ SƠ THÔNG QUA CÁC THÔNG TIN KHÁC
-  URL: ${HIS_URL}/api/v1/patients/search
-  METHOD: POST
-  REQUEST HEADER: Authorization Bearer <token>.
-  REQUEST:
```cshap
{
   "lastname":"LE VAN", //not null
   "name":"DEMO", //not null
   "gender":"0", //not null
   "dateOfBirth":"29/11/1997" //not null
}
```
-  RESPONSE:
```cshap
{
    "id": "20230011",
    "lastname": "LE VAN",
    "name": "DEMO",
    "gender": "0",
    "dateOfBirth": "11/29/1997 12:00:00 AM",
    "phone": "0340001111",
    "address": "CanTho"
}
```



5. LẤY DANH SÁCH QUỐC GIA
-  URL: ${HIS_URL}/api/v1/nationalities
-  METHOD: GET
-  REQUEST HEADER: Authorization Bearer <token>.
-  REQUEST:
-  RESPONSE:
```cshap
{
      "nationalities": 
                      [
                           {
                                   "id": "AC",
                                   "name": "Ai Cập"
                           },....
                       ]
}
```



6. LẤY DANH SÁCH NGHỀ NGHIỆP
-  URL: ${HIS_URL}/api/v1/jobs
-  METHOD: GET
-  REQUEST HEADER: Authorization Bearer <token>.
-  REQUEST:
-  RESPONSE:
```cshap
{
        "jobs":
                       [
                            {
                                     "id": "01",
                                     "name": "Trẻ dưới 6T đi học, dưới 1"
                             },...
                        ]
}
```



6. LẤY DANH SÁCH DÂN TỘC
-  URL: ${HIS_URL}/api/v1/nations
-  METHOD: GET
-  REQUEST HEADER: Authorization Bearer <token>.
-  REQUEST:
-  RESPONSE:
```cshap
{
        "nations": 
                        [
                              {
                                    "id": "16",
                                    "name": "Ấn"
                              },...
                        ]
}
```



7. LẤY DANH SÁCH TỈNH
-  URL: ${HIS_URL}/api/v1/cities
-  METHOD: GET
-  REQUEST HEADER: Authorization Bearer <token>.
-  REQUEST:
-  RESPONSE:
```cshap
{
         "cities":
                        [
                                {
                                    "id": "89",
                                    "name": "An Giang."
                                },...
                         ]
}
```



8. LẤY DANH SÁCH HUYỆN
-  URL: ${HIS_URL}/api/v1/districts?cityid=
-  METHOD: GET
-  REQUEST HEADER: Authorization Bearer <token>.
-  REQUEST:
cityid : mã tỉnh thành  //not null
-  RESPONSE:
```cshap
{
           "districs":
                         [
                                {
                                    "id": "89000",
                                    "name": ""
                                },...
                        ]
}
```



9. LẤY DANH SÁCH XÃ
-  URL: ${HIS_URL}/api/v1/wards?districtid=
-  METHOD: GET
-  REQUEST HEADER: Authorization Bearer <token>.
-  REQUEST:
districtid: mã huyện  //not null
-  RESPONSE:
```cshap
{
            "wards": 
                        [
                                {
                                    "id": "8988600000",
                                    "name": ""
                                },...
                        ]
}
```



10. ĐĂNG KÝ LỊCH KHÁM
-  URL: ${HIS_URL}/api/v1/appointments
-  METHOD: POST
-  REQUEST HEADER: Authorization Bearer <token>.
-  REQUEST:
```cshap
{
       "appointments":
                              {
                               "number": "003", // bõ qua nếu đăng ký trong ngày
                               "providerId": "",
                               "specialityId": "",
                               "roomId": "", //not null
                               "examType": "",
                               "patientType": "",
                               "date": "16/02/2023",
                               "timeslot": "07:00-07:30",  //not null
                                "fee": "100000"  //not null
                                },
        "patient":         {
                                "hisId": "2023003265",  //not null
                                "hiQrCode": "string"
                                },
        "orderId": "string",  //not null
        "feeAmount": "1000000",  //not null
        "serviceFeeAmount": "100000",  //not null
        "status": "CONFIRMED"  //not null
}
```
-  RESPONSE:
```cshap
{
         "mgntHisId": "160223102213",
         "id": "1",
         "number":"1"           
}
```



11. TRUY VẤN LỊCH KHÁM
-  URL: ${HIS_URL}/api/v1/appointments?appointmentsid=
-  METHOD: GET
-  REQUEST HEADER: Authorization Bearer <token>.
-  REQUEST:
appointmentsid
-  RESPONSE:
```cshap
{
    "appointments": {
        "number": "005",
        "providerId": "",
        "specialityId": "",
        "roomId": "",
        "examType": "",
        "patientType": "",
        "date": "16/02/2023",
        "timeslot": "07:00-07:30",
        "fee": "100000"
    },
    "patient": {
        "hisId": "2023003265",
        "hiQrCode": "string"
    },
    "orderId": "string",
    "feeAmount": "",
    "serviceFeeAmount": "100000",
    "status": "CONFIRMED"
}
```



12. TRUY VẤN LỊCH KHÁM
-  URL: ${HIS_URL}/api/v1/appointments?appointmentsid=
-  METHOD: DELETE
-  REQUEST HEADER: Authorization Bearer <token>.
-  REQUEST:
appointmentsid
-  RESPONSE:
```cshap
{
    "id": "15"
}
```




13. TRẢ KẾT QUẢ KHÁM
-  URL: ${HIS_URL}/api/v1/results
-  METHOD: POST
-  REQUEST HEADER: Authorization Bearer <token>.
-  REQUEST:
```cshap
//tra cứu bằng mgnthisid.
{
    "mgnthisid":"2301011220"
}
//or
//tra cứu bằng patientid.
{
     "patientid":"2023003265",
     "month":"01",
     "year":"2023"
}
```
-  RESPONSE:
```cshap
{
    "appoinmentid": "1",
    "patienthisid": "2023003265",
    "detailedDiseaseCode": "I10",
    "diseaseNameVi": "Bệnh lý tăng huyết áp",
    "examDate": "1/9/2023 9:29:43 AM",
    "prescriptions": [
        {
            "id": "GL09",
            "name": "Định lượng Globulin [Máu]",
            "quantity": "1.00",
            "indicationDate": "1/9/2023 9:52:23 AM"
        },...      
    ],
    "medicines": [
        {
            "name": "Amoxicillin Capsules BP 500mg",
            "activeIngredient": "Amoxicilin",
            "total": "10.00",
            "unit": "viên",
            "instruction": "chiều 1 viên"
        },...
    ],
    "status": "CONFIRMED"
}
```



14. LẤY DANH SÁCH KHOA
-  URL: ${HIS_URL}/api/v1/speciality
-  METHOD: GET
-  REQUEST HEADER: Authorization Bearer <token>.
-  REQUEST:
cityid : mã tỉnh thành  //not null
-  RESPONSE:
```cshap
{
            "speciality":
              [
                 {
                    "id": "01",
                    "name": "KHOA NỘI"
                 },
                 {
                    "id": "02",
                    "name": "KHOA Y HỌC CỔ TRUYỀN"
                 },...
             ]
}
```




15. LẤY DANH SÁCH PHÒNG
-  URL: ${HIS_URL}/api/v1/room
-  METHOD: GET
-  REQUEST HEADER: Authorization Bearer <token>.
-  REQUEST:
cityid : mã tỉnh thành  //not null
-  RESPONSE:
```cshap
{
    "room":
      [
        {
            "id": "107.1",
            "name": "[2] Khám Chấn thương chỉnh hình"
        },
        {
            "id": "112.1",
            "name": "[2] Khám Chuyên khoa Nhi"
        },...
      ]
}
```




16. LẤY DANH SÁCH DỊCH VỤ
-  URL: ${HIS_URL}/api/v1/examtype
-  METHOD: GET
-  REQUEST HEADER: Authorization Bearer <token>.
-  REQUEST:
cityid : mã tỉnh thành  //not null
-  RESPONSE:
```cshap
{
    "examtype":
 [
        {
            "id": "CO29",
            "name": "Công khám dịch vụ (Chọn bác sĩ)"
        },...
 ]
}
```



16. LẤY STT TRONG NGÀY THEO PHÒNG
-  URL: ${HIS_URL}/api/v1/appointments/count?roomid=
-  METHOD: GET
-  REQUEST HEADER: Authorization Bearer <token>.
-  REQUEST:
roomid: mã phòng  //not null
-  RESPONSE:
```cshap
{
    "code": "200",
    "stt": "1" // số thứ tự hiện tại
}
```


