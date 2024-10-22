<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: CHẨN ĐOÁN KHI XUẤT XML4750

</div>

###### :eight_spoked_asterisk: Người lập: [**ÔNG TRIỆU HẬU**](https://github.com/ongtrieuhau)

###### :eight_spoked_asterisk: Ngày lập: **22/10/2024**

###### :eight_spoked_asterisk: Ngày hoàn thành dự kiến: **31/10/2024**

###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**

###### :eight_spoked_asterisk: Yêu cầu phát sinh

- Thực hiện theo [Yêu cầu - Mở rộng tham số bắt chuẩn đoán 12 mã bệnh và ghi nhận chẩn đoán tại XML1](https://github.com/dh-hos/To_Lap_Trinh/issues/711)
- Hạn chế số lượng tối đa khi thực hiện gửi XML4750 theo tham số `ma_benh_kt.soluong`
- Các trường trên XML4750 ảnh hưởng: `chan_doan_rv` `ma_benh_chinh` `ma_benh_kt`
- Các module chức năng liên quan tới việc xuất XML4750

###### :eight_spoked_asterisk: Xử lý yêu cầu

:white_check_mark: **Thêm chức năng cấu hình phương thức thực hiện**

- ![](https://i.imgur.com/PjMaoRK.png)

- `Sử dụng (Chỉ lấy thông tin chẩn đoán khi Ra viện)`
  - Khi xuất XML4750 chỉ lấy các mã ICD, chẩn đoán được ghi nhận trên chức năng xuất viện đối với BA Nội trú, BA Ngoại trú.
  - Trường hợp Khám Ngoại trú vẫn gom hết tất cả ICD, chẩn đoán của cả đợt điều trị.
  - Kiểm tra số lượng tối đa ICD theo tham số `ma_benh_kt.soluong` chỉ thực hiện trên chức năng Ra viện của hồ sơ BA.
  - `chan_doan_rv`: `[Ngoại trú]=psdangky.kqcdoan` `[Bệnh án]:bnnoitru.kqcdoan + ‘;’ + bnnoitru.kqcdoanp`
  - `ma_benh_chinh`: `[Ngoại trú]=psdangky.maicd` `[Bệnh án]:bnnoitru.maicd`
  - `ma_benh_kt`: `[Ngoại trú]=psdangky.maicdp` `[Bệnh án]:bnnoitru.maicdp`
- `Không sử dụng (Lấy tất cả thông tin chẩn đoán trong Đợt điềut trị)`
  - Khi xuất XML4750 lấy tất cả ICD, chẩn đoán của cả đợt điều trị.
  - Kiểm tra số lượng tối đa ICD theo tham số `ma_benh_kt.soluong` trên các chức năng có nhập liệu thông tin ICD (Khám bệnh, Thay đổi diễn biến...)
  - `chan_doan_rv`: `[Ngoại trú]=psdangky.kqcdoan` `[Bệnh án]:bnnoitru.kqcdoan + ‘;’ + bnnoitru.kqcdoanp`
  - `ma_benh_chinh`: `[Ngoại trú]=psdangky.maicd` `[Bệnh án]:bnnoitru.maicdxml`
  - `ma_benh_kt`: `[Ngoại trú]=psdangky.maicdp` `[Bệnh án]:bnnoitru.maicdpxml`

:white_check_mark: **Thực hiện kiểm tra số lượng ICD theo tham số: ma_benh_kt.soluong**
