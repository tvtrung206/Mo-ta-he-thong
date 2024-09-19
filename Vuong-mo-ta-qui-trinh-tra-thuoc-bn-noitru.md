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

| STT | TÊN CỘT | KIỂU DỮ LIỆU | GHI CHÚ |
|:-------:|-------|:-------:|-------|
| 1 | qtbenhly | VARCHAR | Ghi nhận tóm tắt quá trình bệnh lý và diễn biến lâm sàng.|
|2|tsbenh|VARCHAR| Ghi nhận tiền sử bệnh của bệnh nhân.|
|3|dhlamsang|VARCHAR| Ghi nhận những dấu hiệu lâm sàng chính.|
|4|ppdieutri|NUMERIC(1,0)| Ghi nhận phương pháp điều trị nội khoa. <br/>Giá trị:<br/> - 0: Không</br> - 1: Có |
|5|ppdieutri_ghichu|VARCHAR| Ghi rõ phương pháp điều trị nếu giá trị cột ppdieutri = 1. |
|6|pttt|NUMERIC(1,0)| Ghi nhận có phẫu thuật, thủ thuật. <br/>Giá trị:<br/> - 0: Không</br> - 1: Có |
|7|pttt_ghichu|VARCHAR| Ghi rõ phương pháp phẫu thuật nếu giá trị cột pttt = 1. |

:blue_book: **Mô tả thực hiện và diễn giải số liệu**: [^2024-07-31]
- **Thực hiện**:
  - Mở form tóm tắt bệnh án:
    
    ![image](https://github.com/user-attachments/assets/a28f4400-d924-4117-9b04-96dd35bcc85b)

  - Form tóm tắt bệnh án:

    ![image](https://github.com/user-attachments/assets/e24b2715-802c-4d95-bfe9-5607bd664467)

    (1): Thực hiện thêm/sửa/xóa tóm tắt bệnh án
    
    (2): Kết quả xét nghiệm: dữ liệu được lấy từ bnnoitru.tomtat_kq (dữ liệu này được thực hiện khi làm thao tác ra viện)
    
    (3): Tình trạng ra viện: dữ liệu được lấy từ dmketqua.ma_medisoft (qua liên kết bnnoitru.makq = dmketqua.makq)
    
        Ghi mã kết quả điều trị, trong đó:
          - Mã “1”: Khỏi;
          - Mã “2”: Đỡ;
          - Mã “3”: Không thay đổi;
          - Mã “4”: Nặng hơn;
          - Mã “5”: Tử vong;
          - Mã “6”: Tiên lượng nặng xin về;
          - Mã “7”: Chưa xác định (không thuộc một trong các mã kết quả điều trị nêu trên).
          - Mã “8”: Tử vong ngoại viện

    - Kết quả in phiếu:
   
      ![image](https://github.com/user-attachments/assets/9c2a3486-7243-4042-a13b-d2d92c761aca)

[^2024-07-31]: Thay đổi ngày 2024-07-31: Bổ sung thêm mô tả thực hiện và dữ liệu

