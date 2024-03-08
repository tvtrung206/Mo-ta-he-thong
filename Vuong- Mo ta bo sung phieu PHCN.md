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

    - Thực hiện phiếu phục hồi chức năng: 
        - Phải đáp ứng các tính năng như lập phiếu phẫu thuật: thể hiện lên số phẫu thuật thủ thuật, ...

:white_check_mark: **Thay đổi cấu trúc dữ liệu**
- Dữ liệu tạo thêm cột: phut và mota và bảng phauthuat
- Script:
  '''
  ALTER TABLE current.phauthuat
    ADD COLUMN phut NUMERIC(4,0) DEFAULT 0;
  ALTER TABLE current.phauthuat
    ADD COLUMN mota VARCHAR;
  '''

:white_check_mark: **Thực hiện**
- Bước 1: lập phiếu thủ thuật
- Bước 2: Nhập êkip
- Bước 3 (lập phiếu phục hồi chức năng, bổ sung các trường còn thiếu cho phiếu PHCN):
   - Ngày thực hiện = ngày bắt đầu phẫu thuật/thủ thuật
   - Bác sĩ thực hiện: ekip phẫu thuật
   - Số phút: cập nhật thêm
   - Mô tả: cập nhật thêm
- Bước 4: In phiếu (chỉ in các thủ thuật cận lâm sàng có cập nhật số phút thực hiện (Chưa phân biệt CLS PHCN và CLS khác))

  


