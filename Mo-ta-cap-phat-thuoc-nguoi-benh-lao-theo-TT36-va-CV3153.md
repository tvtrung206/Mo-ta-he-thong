<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: MÔ TẢ CẤP PHÁT THUỐC NGƯỜI BỆNH LAO THEO TT36 VÀ CV3153
                       CẬP NHẬT CÔNG VĂN 7382

</div>

###### :eight_spoked_asterisk: Người lập: [**NGUYỄN VIẾT VINH**](https://github.com/vinh-dh)
###### :eight_spoked_asterisk: Ngày lập: **17/08/2022**
###### :eight_spoked_asterisk: Người cập nhật: [**NGHỊ VĂN BI**](https://github.com/nghivanbi)
###### :eight_spoked_asterisk: Ngày lập: **20/12/2023**
###### :eight_spoked_asterisk: Ngày hoàn thành dự kiến: **22/12/2023**
###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**
###### :eight_spoked_asterisk: Yêu cầu phát sinh

- Qui trình thực hiện trên phần mềm – triển khai: Chỉ áp dụng cho bệnh nhân khám ngoại trú và bệnh án ngoại trú thanh toán ngày.

###### :eight_spoked_asterisk: Xử lý yêu cầu

:white_check_mark: **Thay đổi cấu trúc dữ liệu**

- Thêm bảng `benhnhan_lao` bảng `current.psdangky` : ghi nhận là người bệnh lao đến nhận thuốc.
- Thêm bảng `mabv_dieutri_lao` bảng `current.psdangky` : ghi nhận mã bệnh viện cấp giấy chứng nhận điều trị nội trú (bệnh lao) của người bệnh.
- Thêm bảng `ngaychungnhan_lao` bảng `current.psdangky` : ghi nhận ngày cấp giấy chứng nhận điều trị nội trú (bệnh lao) của người bệnh.
- SQLScript: 

```
ALTER TABLE current.psdangky ADD COLUMN benhnhan_lao NUMERIC(1,0);
ALTER TABLE current.psdangky ADD COLUMN mabv_dieutri_lao VARCHAR(20);
ALTER TABLE current.psdangky ADD COLUMN ngaychungnhan_lao DATE;

```


:white_check_mark: **Module Treatment**

- bổ sung mẫu “GIẤY XÁC NHẬN ĐIỀU TRỊ NỘI TRÚ” theo mẫu (bên dưới), khổ A4, in đứng.
  
![image](https://github.com/dh-hos/Mo-ta-he-thong/assets/110148171/4479b88e-51e8-468f-968d-237e1b66d6df)


:white_check_mark: **Module Register**

- Bổ sung các control hỗ trợ tiếp nhận người bệnh lao. Chi tiết:
  + Bổ sung CheckBox “Bệnh lao” để người dùng tự xác định đây là bệnh nhân lao đến nhận thuốc (ứng giá trị true thì psdangky.benhnhan_lao = 1 và ngược lại psdangky. benhnhan_lao = 0).
  + Bổ sung control để người dùng nhập mã bệnh viện cấp giấy xác nhận điều trị nội trú (bệnh lao), tương ứng với cột psdangky.mabv_dieutri_lao (chọn đúng mã bệnh viện từ dmbenhvien). Lưu ý: bắt buộc phải có mabv_dieutri_lao nếu CheckBox “Bệnh lao” là true.
  + Bổ sung control để người dùng chọn ngày cấp giấy xác nhận điều trị nội trú (bệnh lao), tương ứng với cột psdangky.ngaychungnhan_lao. Lưu ý: bắt buộc phải có ngaychungnhan_lao nếu CheckBox “Bệnh lao” là true.
- Lưu ý: hướng dẫn bệnh viện tạo đối tượng lao BHYT riêng, chọn công khám 0 đồng (BHYT không thanh toán công khám trong trường hợp này)  để có thể thống kê báo cáo theo đối tượng.


:white_check_mark: **Module Printer**
- In phiếu 01. Kiểm tra nếu psdangky.benhnhan_lao = 1 và khambenh.maicd có chứa mã bệnh Z22.7 thì cập nhật giá trị cột psdangky.kqcdoan = “Cấp thuốc theo Giấy Xác nhận điều trị nội trú của cơ sở khám bệnh, chữa bệnh: <ten_co_so_kcb>, ngày cấp: <ngaychungnhan_lao>”. Trong đó:
  + <ten_co_so_kcb>: được lấy từ dmbenhvien.tenbv thông qua psdangky.mabv_dieutri_lao.
  + <ngaychungnhan_lao>: được lấy từ psdangky.ngaychungnhan_lao, định dạng kiểu DD/MM/YYYY.

:white_check_mark: **Các phân hệ xuất dữ liệu XML4210:**
~~- Bảng 1: xét khi psdangky.benhnhan_lao = 1 thì:
  + Trường 16 (MA_LYDO_VVIEN) = 7 (Lĩnh thuốc ngoài viện do trường hợp bất khả kháng).
  + Trường 35 (MA_LOAI_KCB) = 7 (Nhận thuốc theo hẹn, không khám bệnh).~~
Cập nhật mới:
Bảng 1: xét khi psdangky.benhnhan_lao = 1 thì:
  + Trường 16 (MA_LYDO_VVIEN) = 7.1 (Lĩnh thuốc ngoài viện do trường hợp bất khả kháng).
    Điều trị [current.psdangky.mabv_dieutri_lao = current.psdangky.mabvkb]
    + Trường 35 (MA_LOAI_KCB) = 1 (Khám bệnh).
    Không điều trị [current.psdangky.mabv_dieutri_lao # current.psdangky.mabvkb]
    + Trường 35 (MA_LOAI_KCB) = 7 (Nhận thuốc theo hẹn, không khám bệnh).
  
 
