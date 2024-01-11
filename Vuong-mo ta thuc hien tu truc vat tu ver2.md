<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: THỰC HIỆN QUẢN LÝ TỦ TRỰC VẬT TƯ VERSION 2

</div>

:white_check_mark: **Người lập: NGUYỄN TRIỀU VƯƠNG**

:white_check_mark: **Ngày lập: 10/01/2024**

:white_check_mark: **Ngày dự hoàn thành: 15/01/2024**

:white_check_mark: **Khách hàng: Tất cả**

:white_check_mark: **Xử lý yêu cầu**

    - Thực hiện quản lý tủ trực thứ 2: tủ trực vật tư
    - Do cách lưu trữ hiện tại không đáp ứng được yêu cầu --> Thay đổi cách lưu trữ cho tủ trực

    - Bổ sung cấu trúc: bảng chungtu và pshdxn
      
        ALTER TABLE current.chungtu
          ADD COLUMN loaitoatt NUMERIC(1,0) DEFAULT 0;
        COMMENT ON COLUMN current.chungtu.loaitoatt
        IS '0: Toa bình thường
        1: Toa tủ trực dược
        2: Toa tủ trực nhà thuốc
        3: Toa tủ trực vật tư';
    
        ALTER TABLE current.pshdxn
          ADD COLUMN loaitoatt NUMERIC(1,0) DEFAULT 0;
        COMMENT ON COLUMN current.pshdxn.loaitoatt
        IS '0: Toa bình thường
        1: Toa tủ trực dược
        2: Toa tủ trực nhà thuốc
        3: Toa tủ trực vật tư';
    
      - Lưu toa thuốc: 
        
            - chungtu.toatutruc = 1
            - chungtu.loaitoatt = 0: Toa bình thường, 1: Toa tủ trực dược, 2: Toa tủ trực nhà thuốc, 3: Toa tủ trực vật tư'
            
            - pshdxn.toatutruc = 1
            - pshdxn.loaitoatt = 0: Toa bình thường, 1: Toa tủ trực dược, 2: Toa tủ trực nhà thuốc, 3: Toa tủ trực vật tư'
            
:white_check_mark: **Script hỗ trợ (nếu cần)**
- Dành cho BV THỐT NỐT:

        ABORT;
        BEGIN;
        --chứng từ
        UPDATE current.chungtu set toatutruc = 1, loaitoatt = 3
        FROM (
                SELECT distinct a.kyhieu, a.sohd, a.toatutruc, mabn, makh, a.khochan
                 FROM current.chungtu a 
                WHERE coalesce(a.xoa,0) = 0
                   AND coalesce(a.toacon,0) = 0
                   AND lower(a.loaixn) = 'xbb'
                   AND coalesce(a.noitru,0) = 1
                   AND coalesce(a.toatutruc,0) = 2
              ) as tam
        WHERE current.chungtu.kyhieu = tam.kyhieu
              AND current.chungtu.sohd= tam.sohd
              AND current.chungtu.toatutruc= tam.toatutruc
              AND current.chungtu.khochan= tam.khochan
              AND current.chungtu.mabn= tam.mabn
              AND current.chungtu.makh= tam.makh;
              
        --chứng từ
        UPDATE current.pshdxn set toatutruc = 1, loaitoatt = 3
        FROM (
                SELECT distinct a.kyhieu, a.sohd, a.toatutruc, mabn, makh, a.khochan
                 FROM current.chungtu a 
                WHERE coalesce(a.xoa,0) = 0
                   AND coalesce(a.toacon,0) = 0
                   AND lower(a.loaixn) = 'xbb'
                   AND coalesce(a.noitru,0) = 1
                   AND coalesce(a.toatutruc,0) = 2
              ) as tam
        WHERE current.pshdxn.kyhieu = tam.kyhieu
              AND current.pshdxn.sohd= tam.sohd
              AND current.pshdxn.toatutruc= tam.toatutruc
              AND current.pshdxn.khochan= tam.khochan
              AND current.pshdxn.mabn= tam.mabn
              AND current.pshdxn.makh= tam.makh;
        COMMIT;
  
- Dành cho BV PSCT:

        ABORT;
        BEGIN;
        --chứng từ
        UPDATE current.chungtu set toatutruc = 1, loaitoatt = 2
        FROM (
                SELECT distinct a.kyhieu, a.sohd, a.toatutruc, mabn, makh, a.khochan
                 FROM current.chungtu a 
                WHERE coalesce(a.xoa,0) = 0
                   AND coalesce(a.toacon,0) = 0
                   AND lower(a.loaixn) = 'xbb'
                   AND coalesce(a.noitru,0) = 1
                   AND coalesce(a.toatutruc,0) = 2
              ) as tam
        WHERE current.chungtu.kyhieu = tam.kyhieu
              AND current.chungtu.sohd= tam.sohd
              AND current.chungtu.toatutruc= tam.toatutruc
              AND current.chungtu.khochan= tam.khochan
              AND current.chungtu.mabn= tam.mabn
              AND current.chungtu.makh= tam.makh;
              
        --chứng từ
        UPDATE current.pshdxn set toatutruc = 1, loaitoatt = 2
        FROM (
                SELECT distinct a.kyhieu, a.sohd, a.toatutruc, mabn, makh, a.khochan
                 FROM current.chungtu a 
                WHERE coalesce(a.xoa,0) = 0
                   AND coalesce(a.toacon,0) = 0
                   AND lower(a.loaixn) = 'xbb'
                   AND coalesce(a.noitru,0) = 1
                   AND coalesce(a.toatutruc,0) = 2
              ) as tam
        WHERE current.pshdxn.kyhieu = tam.kyhieu
              AND current.pshdxn.sohd= tam.sohd
              AND current.pshdxn.toatutruc= tam.toatutruc
              AND current.pshdxn.khochan= tam.khochan
              AND current.pshdxn.mabn= tam.mabn
              AND current.pshdxn.makh= tam.makh;
        COMMIT;

:white_check_mark: **Cấu hình**
  
![image](https://github.com/dh-hos/Mo-ta-he-thong/assets/32563776/abaa3e17-3185-4477-a410-7c29600d5d42)

:white_check_mark: **Form ra toa**
  
![image](https://github.com/dh-hos/Mo-ta-he-thong/assets/32563776/f9047644-94ad-4ce8-9976-18d3f21a1bfc)


  



