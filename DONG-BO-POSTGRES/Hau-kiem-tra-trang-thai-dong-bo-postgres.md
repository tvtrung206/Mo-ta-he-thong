<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: KIỂM TRA TRẠNG THÁI MÁY PHỤ ĐỒNG BỘ DỮ LIỆU POSTGRES

</div>

###### :eight_spoked_asterisk: Người lập: [**ÔNG TRIỆU HẬU**](https://github.com/ongtrieuhau)


###### :eight_spoked_asterisk: Ngày lập: **20/11/2023**

###### :eight_spoked_asterisk: Ngày hoàn thành dự kiến: **21/11/2023**

###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**

###### :eight_spoked_asterisk: Yêu cầu phát sinh

- Kiểm tra trạng thái là máy phụ khi có đồng bộ dữ liệu khi sử dụng những phương thức khác với hình thức công ty đang triển khai (mà việc kiểm tra máy phụ với cách thức hiện tại không đáp ứng được)

###### :eight_spoked_asterisk: Xử lý yêu cầu

:white_check_mark: **LibraryApp.dll**

- Cách kiểm tra hiện tại là dựa vào kết quả của cấu hình `transaction_read_only = 'on'` (`SELECT setting FROM   pg_settings WHERE  name = 'transaction_read_only'`) để xác định đây là máy phụ.
- Thêm phương thức mới: Xác định dựa vào giá trị tham số (do bệnh viện tự cấu hình) để xác định IP đóng vai trò máy phụ để các module Reports
- [^2023-11-20] `iphotstandby`: `INSERT INTO current.system (id,tents,diengiai,giatri,loai,module)
SELECT
 (SELECT max(id)+1 FROM current.system),
    'iphotstandby', E'Cấu hình địa chỉ IP đóng vai trò máy phụ trong cơ chế đồng bộ dữ liệu Postgres (Module Reports xác định đây là máy phụ sẽ không thực hiện thêm dữ liệu)'
    ,
    0,
    0,
    0
WHERE NOT EXISTS (SELECT tents FROM current.system WHERE tents = 'iphotstandby');`

:white_check_mark: **Module Reports - Kiểm tra trạng thái máy phụ**

- Cập nhật dll mới LibraryApp.dll mới (vẫn sử dụng hàm kiểm tra hiện tại `LibraryApp.ClsOtherMethods.CheckHotStandby`)

[^2023-11-20]: Thay đổi ngày 2023-11-20.
