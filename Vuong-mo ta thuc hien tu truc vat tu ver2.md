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
            

:white_check_mark: **Cấu hình**
  
![image](https://github.com/dh-hos/Mo-ta-he-thong/assets/32563776/abaa3e17-3185-4477-a410-7c29600d5d42)

:white_check_mark: **Form ra toa**
  
  ![image](https://github.com/dh-hos/Mo-ta-he-thong/assets/32563776/39d4e36d-82ed-4bf7-b4dd-880428b8e2a8)

  



