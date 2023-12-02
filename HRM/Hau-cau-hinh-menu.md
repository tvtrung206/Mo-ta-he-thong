<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: CẤU HÌNH ẨN/HIỆN MENU CHÍNH

</div>

###### :eight_spoked_asterisk: Người lập: [**ÔNG TRIỆU HẬU**](https://github.com/ongtrieuhau)


###### :eight_spoked_asterisk: Ngày lập: **03/12/2023**

###### :eight_spoked_asterisk: Ngày hoàn thành dự kiến: **03/12/2023**

###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**

###### :eight_spoked_asterisk: Yêu cầu phát sinh

- Thêm chức năng ẩn hiện menu chính (nhân viên DH sẽ thực hiện chỉnh cấu hình)

###### :eight_spoked_asterisk: Xử lý yêu cầu

:white_check_mark: **Thay đổi cấu trúc dữ liệu**

- Thêm cấu hình trong `current.coderun` với dòng dữ liệu `code=hrm_menu_visible` với giá trị theo mẫu.
- Cấu hình mẫu (True: Hiện, False: Ẩn) (lưu ý phân biệt hoa thường, khoảng trắng, cách hàng):

``` Cấu hình mẫu
nhansu-Nhân sự:False
    grpdanhmucnhansu-:True
       danhmucnhansu-Danh mục:True
    grpnhansu-:True
       nhanvien-Nhân viên:True
       separatorCommand11-:True
       hopdong-Hợp đồng:False
       quatrinh-Quá trình:False
       khenthuong-Khen thưởng:True
       kyluat-Kỷ luật:True
       separatorCommand12-:True
       daotao-Đào tạo ngắn hạn:True
       congtac-Công tác:True
       thiduathang-Thi đua tháng (ABC):True
       abcqui-ABC quí:True
       danhgiacongchuc-Đánh giá công chức:True
       nghiphep-Nghỉ dài hạn:True
       capnhatnv-Cập nhật nhân viên:True
       bonhiem-Bổ nhiệm:True
       khamsuckhoe-Khám sức khỏe:True
       dskhamsuckhoe-Danh sách KSK tại đơn vị:True
    ribbonGroup2-:True
       dulieuCheckInOut-Dữ liệu chấm công:True
       taolichtruc-Tạo lịch trực:True
       baocaochamcongWise-Báo cáo chấm công:True
    grpbaocaonhansu-:True
       baocaonhansu-Báo cáo:True
luong-Lương:True
    grpdanhmucluong-:True
       danhmucluong-Danh mục:True
    grpchamcong-:True
       chamcong-Chấm công:True
       themgio-Chấm thêm giờ:True
       themgioksk-Thêm giờ KSK:True
    grpkhoantru-:True
       truluong-Trừ lương:True
    grpkhoancong-:True
       tientruc-Tiền trực:True
       tienthemgio-Tiền thêm giờ:True
       phauthuat-Phẫu thuật thủ thuật:True
       dochai-Độc hại:True
       uudainghe-Ưu đãi nghề:True
       tienan-Tiền ăn:True
       tiendienthoai-Tiền điện thoại:True
       congtacphi-Công tác phí:True
       truyluong-Truy nâng lương:True
       pchienvat-Bồi dưỡng hiện vật:True
       tienabc-Tiền ABC:True
       phucapkhac-Phụ cấp khác:True
       bhxhtra-BHXH trả:True
       congvu-Phụ cấp công vụ:True
       separatorCommand9-:True
       luonghopdong-Lương hợp đồng:True
       tinhluong-Tính lương:True
       chuyenatm-Chuyển ATM:True
    grpthuong-:True
       thuong-Tiền thưởng:True
    grpBaoCaoLuong-:True
       baocaoluong-Báo cáo:True
tienich-Tiện ích:True
    ribbonGroup1-:True
       nhatky-Nhật ký thao tác:True
       khoathang-Khóa tháng lương:True
       cauhinhchuky-Cấu hình chữ ký:True
trogiup-Trợ giúp:False
    ribbonGroup7-:True
       gioithieu-Giới thiệu:True
       huongdansudung-Hướng dẫn sử dụng:False
       remote-Hỗ trợ từ xa:True
hethong-Hệ thống:False
    grphethong-:False
       chucnang2-Chức năng:True
       phanquyen2-Phân quyền:True
       separatorCommand14-:True
       thamsohethong2-Tham số hệ thống:True
       cauhinhmay2-Cấu hình máy:True
       cauhinhdulieu2-Cấu hình dữ liệu:True
       khoathangchamcong2-Khóa tháng lương:True
       separatorCommand13-:True
       dangxuat2-Đăng xuất:True
       ketthuc2-Kết thúc:True
```

- SQLScript cập nhật cấu hình

``` SQLScript
UPDATE current.coderun
SET value='
nhansu-Nhân sự:True
    grpdanhmucnhansu-:False
       danhmucnhansu-Danh mục:True
    grpnhansu-:False
       nhanvien-Nhân viên:True
       separatorCommand11-:True
       hopdong-Hợp đồng:False
       quatrinh-Quá trình:False
       khenthuong-Khen thưởng:True
       kyluat-Kỷ luật:True
       separatorCommand12-:True
       daotao-Đào tạo ngắn hạn:True
       congtac-Công tác:True
       thiduathang-Thi đua tháng (ABC):True
       abcqui-ABC quí:True
       danhgiacongchuc-Đánh giá công chức:True
       nghiphep-Nghỉ dài hạn:True
       capnhatnv-Cập nhật nhân viên:True
       bonhiem-Bổ nhiệm:True
       khamsuckhoe-Khám sức khỏe:True
       dskhamsuckhoe-Danh sách KSK tại đơn vị:True
    ribbonGroup2-:True
       dulieuCheckInOut-Dữ liệu chấm công:True
       taolichtruc-Tạo lịch trực:True
       baocaochamcongWise-Báo cáo chấm công:True
    grpbaocaonhansu-:True
       baocaonhansu-Báo cáo:True
luong-Lương:True
    grpdanhmucluong-:True
       danhmucluong-Danh mục:True
    grpchamcong-:True
       chamcong-Chấm công:True
       themgio-Chấm thêm giờ:True
       themgioksk-Thêm giờ KSK:True
    grpkhoantru-:True
       truluong-Trừ lương:True
    grpkhoancong-:True
       tientruc-Tiền trực:True
       tienthemgio-Tiền thêm giờ:True
       phauthuat-Phẫu thuật thủ thuật:True
       dochai-Độc hại:True
       uudainghe-Ưu đãi nghề:True
       tienan-Tiền ăn:True
       tiendienthoai-Tiền điện thoại:True
       congtacphi-Công tác phí:True
       truyluong-Truy nâng lương:True
       pchienvat-Bồi dưỡng hiện vật:True
       tienabc-Tiền ABC:True
       phucapkhac-Phụ cấp khác:True
       bhxhtra-BHXH trả:True
       congvu-Phụ cấp công vụ:True
       separatorCommand9-:True
       luonghopdong-Lương hợp đồng:True
       tinhluong-Tính lương:True
       chuyenatm-Chuyển ATM:True
    grpthuong-:True
       thuong-Tiền thưởng:True
    grpBaoCaoLuong-:True
       baocaoluong-Báo cáo:True
tienich-Tiện ích:True
    ribbonGroup1-:True
       nhatky-Nhật ký thao tác:True
       khoathang-Khóa tháng lương:True
       cauhinhchuky-Cấu hình chữ ký:True
trogiup-Trợ giúp:False
    ribbonGroup7-:True
       gioithieu-Giới thiệu:True
       huongdansudung-Hướng dẫn sử dụng:False
       remote-Hỗ trợ từ xa:True
hethong-Hệ thống:False
    grphethong-:False
       chucnang2-Chức năng:True
       phanquyen2-Phân quyền:True
       separatorCommand14-:True
       thamsohethong2-Tham số hệ thống:True
       cauhinhmay2-Cấu hình máy:True
       cauhinhdulieu2-Cấu hình dữ liệu:True
       khoathangchamcong2-Khóa tháng lương:True
       separatorCommand13-:True
       dangxuat2-Đăng xuất:True
       ketthuc2-Kết thúc:True
'
WHERE code='hrm_menu_visible';
```


:white_check_mark: **HRM**

- Thêm chức năng ẩn hiện menu theo cấu hình

