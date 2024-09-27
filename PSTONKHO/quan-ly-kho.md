<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: QUẢN LÝ KHO

</div>

###### :eight_spoked_asterisk: Người lập: [ÔNG TRIỆU HẬU](https://github.com/ongtrieuhau)

###### :eight_spoked_asterisk: Ngày lập: **2024-09-27**

###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**

###### :eight_spoked_asterisk: Yêu cầu phát sinh

- Các chức năng `[Ra toa tủ trực]` (trừ kho trực tiếp) và chức năng `[Cân kho]` diễn ra đồng thời gây lỗi dữ liệu kho.
- `[Ra toa tủ trực]` (chưa hoàn thành) => `[Cân kho]` => `[Ra toa tủ trực]` (tiếp tục) => Gây lỗi số liệu tồn kho
- Theo luồng công việc [Lỗi - trừ kho tủ trực (BV cái răng)](https://github.com/dh-hos/dhg.hospitalprescription/issues/330)
- Theo luồng công việc [Yêu cầu - Phần tích, mô tả, thực hiện qui trình cho thuốc tủ và cập nhật tồn kho tủ trực)](https://github.com/dh-hos/To_Lap_Trinh/issues/662)

###### :eight_spoked_asterisk: Xử lý yêu cầu

- Hoàn thiện các chức năng xử lý tồn kho để không ảnh hưởng tới số liệu Tồn kho khi thực hiện các nghiệp vụ nhập xuất.
- Xử lý `[Cân kho]`: Ghi nhận trạng thái đã được xử lý cân kho (**_Medicine_**, **_SecondStore_**)
- Xử lý `[Ra toa tủ trực]`: Dựa vào trạng thái trên để tiếp tục xử lý các chức năng liên quan tới tồn kho (**_Prescription_**, **_Treament_**).
- Xử lý `[Các loại xuất]`: Dựa vào trạng thái trên để tiếp tục xử lý các chức năng liên quan tới tồn kho. (**_Medicine_**, **_SecondStore_**)

:white_check_mark: **Thay đổi cấu trúc dữ liệu**

- Thêm cấu trúc **_current.tkdatatemp.da_can_kho (NUMERIC,1,0)_** xác định trạng thái đã xử lý cân kho theo mặt hàng, theo kho
- Nguyên tắc:

  - `1`: Chức năng `[Cân kho]` đã xử lý.

  - `Khác 0`: Chức năng `[Cân kho]` chưa xử lý, chưa tác động tới mặt hàng này. **_Các chức năng xử lý như hiện tại_**.

:white_check_mark: **Xử lý nghiệp vụ**

- Điều kiện xử lý dữ liệu theo thông tin hàng hóa như sau: **_`mahh`_** **_`giaxuat`_** **_`handung`_** **_`khocp`_** **_`tutruc`_** **_`thangkt`_** **_`namkt`_**
- **_`[Cân kho]`_**: Những hàng hóa có thay đổi khi xử lý, sẽ cập nhật giá trị `current.tkdatatemp.da_can_kho = 1`
- **_`[Các loại xuất]`_**: **_Thực hiện thêm thao tác lưu dữ liệu vào bảng_** `current.tkdatatemp` **_(nếu như chưa xử lý)_**
- **_`[Ra toa tủ trực]`_**, **_`[Các loại xuất]`_**: Kiểm tra `current.tkdatatemp.da_can_kho <> 1` xử lý như hiện tại. Ngược lại sẽ xử lý như sau
  - `[Thao tác lưu]`: Tiếp tục trừ kho thêm 1 lần nữa khi lưu khi xóa dữ liệu `current.tkdatatemp`
  - `[Thao tác Bỏ qua]`, `[Xử lý xóa dữ liệu bảng tạm]` (trường hợp, hai thao `[Lưu]` và `[Bỏ qua]` trên chưa hoàn thành khi thao tác nhập xuất): Không trừ kho khi xóa dữ liệu `current.tkdatatemp`
  - Lưu ý: Chức năng chỉnh toa khi lưu cũng thực hiện kiểm tra theo luồng nguyên tắc trên nếu có xử lý trên bảng `current.tkdatatemp`
