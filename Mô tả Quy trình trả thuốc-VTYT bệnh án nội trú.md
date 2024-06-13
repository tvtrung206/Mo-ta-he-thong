<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>
<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: MÔ TẢ QUY TRÌNH TRẢ THUỐC/VTYT NGƯỜI BỆNH ĐIỀU TRỊ NỘI TRÚ
</div>

###### :eight_spoked_asterisk: Người lập: [**vinh-dh**](https://github.com/vinh-dh)
###### :eight_spoked_asterisk: Ngày lập: **13/06/2024**
###### :eight_spoked_asterisk: Ngày cập nhật: 
###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**
###### :eight_spoked_asterisk: Yêu cầu phát sinh

- Thực hiện theo yêu cầu chi tiết tại: [Yêu cầu - Thực hiện mô tả chức năng trả thuốc.  #394](https://github.com/dh-hos/To_Lap_Trinh/issues/394)

###### :eight_spoked_asterisk: Xử lý yêu cầu:

:white_check_mark: Cập nhật cấu trúc: bổ sung các cột vào table `current.pshdxn`
|TT|Tên cột|Kiểu dữ liệu|Diễn giải|
|:-------:|-------|-------|-------|
|1|sohdx|VARCHAR(20)|Ghi nhận số hóa đơn xuất của mặt hàng khi trả.<br/>**Lưu ý**: chỉ áp dụng đối với trường hợp trả thuốc/VTYT.|

:white_check_mark: **Quy trình áp dụng:**

:blue_book: DHG.Hospital Treatment: 
- Trường hợp trả cả toa: Thực hiện như quy trình hiện tại đã có.
- Trường hợp trả từng mặt hàng, tại form trả thuốc/VTYT, thực hiện:<br/>
⇒ Cho phép người dùng chọn từng mặt hàng (thuốc/VTYT) để trả: hiển thị danh sách các lô đã xuất (chưa trả/trả chưa hết số lượng) trước đó, kèm theo các thông tin liên quan đến thông tin đã xuất (số hóa đơn, ngày xuất, số lượng xuất còn lại chưa trả,  đơn giá xuất, số lô, hạn dùng, ...). <br/>
⇒  **Kiểm tra**: số lượng trả phải đảm bảo quy tắc luôn nhỏ hơn hoặc bằng số lượng đã xuất.<br/>
⇒ Khi lưu toa trả: ghi nhận số hóa đơn `[sohd]` xuất của lô đã chọn để trả và cập nhật vào cột `current.pshdxn.sohdx`.

:blue_book: Các phân hệ có tính/tổng hợp chi phí thuốc/VTYT: cấn trừ cho lô trả (nếu có) đối với các lô đã xuất theo trình tự như sau:

- Trường hợp trả cả toa: lấy số hóa đơn xuất `current.chungtu.sohdx` ⇒ Tra cứu vào `current.pshdxn.sohd` lấy danh sách các lô đã xuất dựa vào các điều kiện: `mabn, makh, sohd, mahh, soluong` để cấn trừ thành tiền tương ứng.<br/>
- Trường hợp trả từng mặt hàng, xét:<br/>
⇒ Nếu `pshdxn.sohdx` tồn tại: tra cứu `pshdxn.sohdx` ⇒ vào `pshdxn.sohd` lấy  lô đã xuất dựa vào các điều kiện: `mabn, makh, sohd, mahh, soluong` để cấn trừ thành tiền tương ứng. **Lưu ý:** Số lượng trả phải nhỏ hơn hoặc bằng số lượng đã xuất.<br/>
⇒ Các trường hợp khác: kiểm tra `ngay_yl` (`= to_char(ct.ngayhd,'YYYYMMDD') || to_char(ct.giolap,'HH24mi')`) của lô đang trả và chỉ cấn trừ các lô đã xuất theo điều kiện `ngay_yl trả` phải nhỏ hơn `ngay_yl của lô đã xuất`. Nếu danh sách các lô đã xuất nhiều hơn 1 thì phải sắp xếp thứ tự cấn trừ lô theo `ngay_yl xuất` từ nhỏ đến lớn.
