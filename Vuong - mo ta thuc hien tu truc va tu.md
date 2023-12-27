<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: THỰC HIỆN QUẢN LÝ TỦ TRỰC VẬT TƯ

</div>

:white_check_mark: **Người lập: NGUYỄN TRIỀU VƯƠNG**

:white_check_mark: **Ngày lập: 27/12/2023**

:white_check_mark: **Ngày dự hoàn thành: 29/12/2023**

:white_check_mark: **Khách hàng: Tất cả**

:white_check_mark: **Xử lý yêu cầu**

    - Thực hiện quản lý tủ trực thứ 2: tủ trực vật tư
    - Do cách lưu trữ hiện tại không đáp ứng được yêu cầu --> Thay đổi cách lưu trữ cho tủ trực

    - Cách cũ: 
    
        - Lưu toa tủ trực dược: 
        
            - chungtu.toatutruc = 1 and chungtu.tutruc = mã tủ trực and chungtu.khochan = 14 (kho chẵn dược)
            - pshdxn.toatutruc = 1 and pshdxn.tutruc = mã tủ trực and pshdxn.khochan = 14 (kho chẵn dược)
            
        - Lưu toa tủ trực nhà thuốc: 
        
            - chungtu.toatutruc = 1 and chungtu.tutruc = mã tủ trực and chungtu.khochan = 13 (kho chẵn nhà thuốc)
            - pshdxn.toatutruc = 1 and pshdxn.tutruc = mã tủ trực and pshdxn.khochan = 13 (kho chẵn nhà thuốc)
            
    - Cách lưu trữ mới:

        - Lưu toa tủ trực dược: 
        
            - chungtu.toatutruc = 1 and chungtu.tutruc = mã tủ trực and chungtu.khochan = 14 (kho chẵn dược)
            - pshdxn.toatutruc = 1 and pshdxn.tutruc = mã tủ trực and pshdxn.khochan = 14 (kho chẵn dược)
            
        - Lưu toa tủ trực nhà thuốc: 
        
            - chungtu.toatutruc = 2 and chungtu.tutruc = mã tủ trực nhà thuốc and chungtu.khochan = 13 (kho chẵn nhà thuốc)
            - pshdxn.toatutruc = 2 and pshdxn.tutruc = mã tủ trực nhà thuốc and pshdxn.khochan = 13 (kho chẵn nhà thuốc)
            
        - Lưu toa tủ trực vật tư: 
        
            - chungtu.toatutruc = 2 and chungtu.tutruc = mã tủ trực vật tư and chungtu.khochan = mã kho chẵn vật tư
            - pshdxn.toatutruc = 2 and pshdxn.tutruc = mã tủ trực vật tư and pshdxn.khochan = mã kho chẵn vật tư

    - Các module rà soát lại và cập nhật các chứng năng có liên quan đến cột toatutruc

:white_check_mark: **Cấu hình**
  
![image](https://github.com/dh-hos/Mo-ta-he-thong/assets/32563776/abaa3e17-3185-4477-a410-7c29600d5d42)

:white_check_mark: **Form ra toa**
  
  ![image](https://github.com/dh-hos/Mo-ta-he-thong/assets/32563776/39d4e36d-82ed-4bf7-b4dd-880428b8e2a8)

  


