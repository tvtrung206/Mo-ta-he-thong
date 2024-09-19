<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>MÔ TẢ QUI TRÌNH TRẢ THUỐC</h1>  
</div>
<div align="center">

#### Chủ đề: QUI TRÌNH TẢ THUỐC BỆNH NHÂN NỘI TRÚ

</div>

###### :eight_spoked_asterisk: Người lập: [**Nguyễn Triều Vương**](https://github.com/vuongdh)

###### :eight_spoked_asterisk: Ngày lập: **19/09/2024**

###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**

:white_check_mark: **Thông tin bệnh nhân** 

![image](https://github.com/user-attachments/assets/8330c969-ddf4-4639-904d-30e5f14b1801)

Thông tin ghi trong bản bnnoitru:
![image](https://github.com/user-attachments/assets/a577b150-fcd5-48cb-a302-71528f8384d9)

:white_check_mark: **Qui trình trả thuốc, có 2 giai đoạn: trước và sau khi bổ sung cột pshdxn.sohdx** 

:white_check_mark: **Qui trình xuất thuốc, ghi nhận tại pshdxn** 

![image](https://github.com/user-attachments/assets/d1aa482c-dcdb-47de-acd2-a50dad04ea42)

:white_check_mark: **Qui trình trả thuốc, ghi nhận tại pshdxn**  

![image](https://github.com/user-attachments/assets/f8f9bae7-b455-471c-bf44-daed595103ba)

:white_check_mark: **Thuốc xuất - trừ trả** 

- Khi không có cột sohdx trong phiếu trả:
    - Trên form: cấn trừ theo mahh, ngayhd, madt
    - Trên 6556:
          - Cấn trứ theo mahh, madt, phần trăm chi trả ghi nhận theo thông tin trên bnnoitru hoặc ttcon (con hoặc thẻ 2)
      
          - Thông tin mã thẻ: được lấy từ thông tin thẻ 1 hoặc thẻ 2
      
          - Trường hợp có ngày miễn giảm:
      
                - Cấn trừ theo mã mahh, madt, ngayhd (xuất/trả): phần trăm chi trả trong giai đoạn miễn giảm ghi 100 ngược lại ghi theo thông tin thẻ

- Khi có cột sohdx phiếu trả:
    - Trên form: cấn trừ theo số lượng xuất - số lượng trả (theo mahh, madt, sohdx = sohd): phần trăm chi trả ghi theo thông tin thẻ
      
    - Thông tin mã thẻ: được lấy từ thông tin thẻ 1 hoặc thẻ 2
      
          - Trường hợp có ngày miễn giảm:
      
                - Cấn trừ theo số lượng xuất - số lượng trả (theo mahh, madt, sohdx = sohd): phần trăm chi trả trong giai đoạn miễn giảm ghi 100 ngược lại ghi theo thông tin thẻ

:white_check_mark: **Ví dụ**

Thông tin bệnh nhân:

![image](https://github.com/user-attachments/assets/8330c969-ddf4-4639-904d-30e5f14b1801)

![image](https://github.com/user-attachments/assets/6cca69a8-7466-4594-aa7e-5e1508207faa)

Tổng kết:

![image](https://github.com/user-attachments/assets/889f4e93-552c-482b-870e-5512107522a4)

![image](https://github.com/user-attachments/assets/1329d008-6619-49f5-b4d4-c912c3d1bf3f)

![image](https://github.com/user-attachments/assets/3124212b-503b-4f6e-8298-7c0de21f2b4d)



