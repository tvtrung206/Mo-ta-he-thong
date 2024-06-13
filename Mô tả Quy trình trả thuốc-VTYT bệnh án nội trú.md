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
###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**
###### :eight_spoked_asterisk: Yêu cầu phát sinh

- Thực hiện theo yêu cầu chi tiết tại: [Yêu cầu - Thực hiện mô tả chức năng trả thuốc.  #394](https://github.com/dh-hos/To_Lap_Trinh/issues/394)

###### :eight_spoked_asterisk: Xử lý yêu cầu:

:white_check_mark: Cập nhật cấu trúc: bổ sung các cột vào table `current.pshdxn`
|TT|Tên cột|Kiểu dữ liệu|Diễn giải|
|:-------:|-------|-------|-------|
|1|sohdx|VARCHAR(20)|Ghi nhận số hóa đơn xuất của mặt hàng khi trả.<br/>**Lưu ý**: chỉ áp dụng đối với trường hợp trả thuốc/VTYT.|

:white_check_mark: **Quy trình áp dụng:** [^2024-06-13]

:blue_book: DHG.Hospital Treatment: 
- Trường hợp trả cả toa: Thực hiện như quy trình hiện tại đã có. Bổ sung thêm: cập nhật số hóa đơn của toa xuất vào `pshdxn.sohdx` của lô trả.
- Trường hợp trả từng mặt hàng, tại form trả thuốc/VTYT, thực hiện:<br/>
⇒ Cho phép người dùng chọn từng mặt hàng (thuốc/VTYT) để trả: hiển thị danh sách các lô đã xuất (chưa trả/trả chưa hết số lượng) trước đó, kèm theo các thông tin liên quan đến thông tin đã xuất (số hóa đơn, ngày xuất, số lượng xuất còn lại chưa trả,  đơn giá xuất, số lô, hạn dùng, ...). <br/>
⇒  **Kiểm tra: `[số lượng đang trả] <= [số lượng đã xuất (lô đang chọn)] - [Tổng số lượng đã trả trước đó (nếu có)]`** `[1]`.<br/>
⇒ Khi lưu toa trả: ghi nhận số hóa đơn `[sohd]` xuất của lô đã chọn và cập nhật vào cột `current.pshdxn.sohdx` lô đang trả.

:blue_book: Các phân hệ có tính/tổng hợp chi phí thuốc/VTYT: cấn trừ cho lô trả (nếu có) đối với các lô đã xuất theo trình tự như sau: 

- Nếu `pshdxn.sohdx` của lô trả tồn tại: tra cứu `pshdxn.sohdx` ⇒ vào `pshdxn.sohd` lấy  lô đã xuất dựa vào các điều kiện: `mabn, makh, sohd, mahh, soluong` để cấn trừ thành tiền tương ứng. **Lưu ý:** Phải đảm bảo số lượng trả theo điều kiện `[1]`.
- Các trường hợp khác: Áp dụng theo cách cũ hiện có.

[^2024-06-13]: Cập nhật ngày 13/06/2024: Cải tiến quy trình.
