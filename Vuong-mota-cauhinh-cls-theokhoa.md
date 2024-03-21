<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: THỰC HIỆN CẤU HÌNH CLS THƯỜNG DÙNG THEO KHOA (NỘI TRÚ)

</div>

:white_check_mark: **Người lập: NGUYỄN TRIỀU VƯƠNG**

:white_check_mark: **Ngày lập: 21/03/2024**

:white_check_mark: **Ngày dự hoàn thành: 25/03/2024**

:white_check_mark: **Khách hàng: Tất cả**

:white_check_mark: **Xử lý yêu cầu**

    - Thực hiện cấu hình CLS thường dùng khoa

    - Bổ sung bảng:
    ''''
      CREATE TABLE current.clskhoa (
      macls VARCHAR(20) NOT NULL,
      madv VARCHAR(20),
      manv VARCHAR(20),
      stt NUMERIC(6,0) DEFAULT 0,
      CONSTRAINT clskhoa_fk FOREIGN KEY (macls)
        REFERENCES current.dmcls(macls)
        ON DELETE NO ACTION
        ON UPDATE NO ACTION
        NOT DEFERRABLE,
      CONSTRAINT clskhoa_fk1 FOREIGN KEY (madv)
        REFERENCES current.dmdonvi(madv)
        ON DELETE NO ACTION
        ON UPDATE CASCADE
        NOT DEFERRABLE,
      CONSTRAINT clskhoa_fk2 FOREIGN KEY (manv)
        REFERENCES current.dmnhanvien(manv)
        ON DELETE NO ACTION
        ON UPDATE CASCADE
        NOT DEFERRABLE
    ) 
    WITH (oids = false);
    ''''
:white_check_mark: **Treatment**
  - Thêm form cấu hình CLS thường dùng theo khoa
  - Form chỉ định CLS: thêm option tùy chọn ALL CLS hoặc CLS theo khoa
