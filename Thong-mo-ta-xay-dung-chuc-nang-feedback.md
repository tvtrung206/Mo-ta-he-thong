<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: XÂY DỰNG CHỨC NĂNG FEEDBACK.

</div>

###### :eight_spoked_asterisk: Người lập: [**LÊ QUỐC THỐNG**](https://github.com/lequocthong29)

###### :eight_spoked_asterisk: Ngày lập: **17/09/2024**

###### :eight_spoked_asterisk: Ngày hoàn thành dự kiến: 

###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**

###### :eight_spoked_asterisk: Xử lý yêu cầu:

:white_check_mark: **Tạo cấu trúc dữ liệu**
- tạo table current.dmfeedback để lưu danh mục feedback:
```csharp
CREATE TABLE current.dmfeedback (
                 mafb VARCHAR(10) NOT NULL,
                 tenfb VARCHAR NOT NULL,
                 trangthai NUMERIC(1,0),
                 maloai NUMERIC(1,0),
                 noitru NUMERIC(1,0),
                 PRIMARY KEY(mafb)
        ) 
  WITH (oids = false);
  COMMENT ON COLUMN current.dmfeedback.trangthai
  IS '0:không hiển thị; 1:Hiển thị';

```

- tạo table current.kqfeedback lưu kết quả feedback
```csharp
  CREATE TABLE current.kqfeedback (
             stt serial NOT NULL,
             nguoighiphieu NUMERIC(1,0),
             gioitinh NUMERIC(1,0),
             ngaydienphieu TIMESTAMP(0) WITHOUT TIME ZONE,
             madv VARCHAR(10),
             tendv VARCHAR(255),
             tuoi NUMERIC(3,0),
             sdt VARCHAR(255) NOT NULL,
             songaynamvien NUMERIC(10,0),
             bhyt NUMERIC(1,0),
             ketqua VARCHAR,
             PRIMARY KEY(stt)
) 
WITH (oids = false);

ALTER TABLE current.kqfeedback
 ALTER COLUMN gioitinh SET STATISTICS 0;
COMMENT ON COLUMN current.kqfeedback.nguoighiphieu
IS '0:nguời bệnh; 1: nguời nhà';
COMMENT ON COLUMN current.kqfeedback.gioitinh
IS '0:nữ ; 1:nam';
COMMENT ON COLUMN current.kqfeedback.bhyt
IS '0:không ; 1:có';
COMMENT ON COLUMN current.kqfeedback.ketqua
IS 'kết quả feedback luu dạng mafb:ketqua;
(mã feedback:kết quả feedback;) và cách nhau bởi dấu ";"';

```

:white_check_mark: **Xây dựng form Feedback**
- Chức năng:
  + Load và Hiển thị tiêu chí feedback theo cấu hình của bệnh viện.
  + Cho người dùng chọn và lưu kết quả feedback.

:white_check_mark: **Tạo form hiển thị, tổng hợp kết quả feedback**
- Chức năng: Hiển thị kết quả feedback
