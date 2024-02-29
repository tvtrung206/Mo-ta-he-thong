<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>MÔ TẢ BỔ SUNG PHIẾU PHỤC HỒI CHỨC NĂNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: BỔ SUNG PHIẾU PHỤC HỒI CHỨC NĂNG

</div>

:white_check_mark: **Người lập: NGUYỄN TRIỀU VƯƠNG**

:white_check_mark: **Ngày lập: 22/02/2024**

:white_check_mark: **Ngày dự hoàn thành: 01/03/2024**

:white_check_mark: **Khách hàng: Tất cả**

:white_check_mark: **Xử lý yêu cầu**

![image](https://github.com/dh-hos/Mo-ta-he-thong/assets/32563776/8170dbf0-eb81-4d8f-8c45-a47f1c2a0d21)

    - Thực hiện bổ sung phiếu phục hồi chứng năng

:white_check_mark: **Thay đổi cấu trúc dữ liệu**
- Thêm bảng (phcn)
![image](https://github.com/dh-hos/Mo-ta-he-thong/assets/32563776/1400348f-b895-4bd9-ad58-492417f955a6)
```
CREATE TABLE current.phcn (
 id VARCHAR(20) NOT NULL,
  mabn VARCHAR(20),
  makb VARCHAR(20),
  maba VARCHAR(20),
  madv VARCHAR(20),
  macls VARCHAR(20),
  idchidinh VARCHAR(20),
  iddienbien VARCHAR(20),
  ngay TIMESTAMP WITHOUT TIME ZONE,
  manv VARCHAR(20),
  phut NUMERIC(4,0),
  xoa NUMERIC(1,0),
  ngayxoa TIMESTAMP WITHOUT TIME ZONE,
  taikhoan VARCHAR(20),
  tenmay VARCHAR(20),
  thangkt VARCHAR(2),
  namkt VARCHAR(4),
  mota VARCHAR,
  CONSTRAINT phcn_pkey PRIMARY KEY(id)
) 
WITH (oids = true);


ALTER TABLE current.phcn
  OWNER TO postgres;
```


:white_check_mark: **Xử lý**
- **Treatment**
   - Bổ sung thêm chức năng lập phiếu phục hồi chức năng
    ![image](https://github.com/dh-hos/Mo-ta-he-thong/assets/32563776/799cee83-de19-49e4-a478-24df61ac16b7)
    ![image](https://github.com/dh-hos/Mo-ta-he-thong/assets/32563776/8699b28a-dbdf-404f-9316-bd5bb78e8bc4)

   - Chọn cận lâm sàng có phân loại tt-pt từ chỉ định:
     ![image](https://github.com/dh-hos/Mo-ta-he-thong/assets/32563776/47e6a8fe-a876-4056-a4d6-b747c400884d)
   - Nhập ngày giờ thực hiện
   - Chọn nhân viên thực hiện
   - Nhập số phút thực hiện
   - Nhập mô tả
   - In phiếu
     ![image](https://github.com/dh-hos/Mo-ta-he-thong/assets/32563776/687fa47c-6579-4380-9977-1ba083411d39)

  


