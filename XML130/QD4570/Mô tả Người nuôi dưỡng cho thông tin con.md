<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### Chủ đề: Mô tả Người nuôi dưỡng cho thông tin con theo [Quyết định 4750/QĐ-BYT](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/4750.pdf).
</div>

###### :eight_spoked_asterisk: Người lập: [**Nguyễn Viết Vinh**](https://github.com/vinh-dh)

###### :eight_spoked_asterisk: Ngày lập: **14/10/2024**

###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**

###### :eight_spoked_asterisk: Yêu cầu phát sinh

###### :eight_spoked_asterisk: Xử lý yêu cầu

:white_check_mark: **Thay đổi cấu trúc dữ liệu**

:blue_book: Cập nhật cấu trúc table **ttcon**:
| STT | TÊN CỘT | KIỂU DỮ LIỆU | GHI CHÚ |
|:-------:|-------|:-------:|-------|
|1|ma_bhxh_nnd|VARCHAR(10)|Ghi mã số BHXH người nuôi dưỡng.|
|2|ma_the_nnd|VARCHAR(15)|Ghi mã thẻ BHYT người nuôi dưỡng.|
|3|ho_ten_nnd|VARCHAR(255)|Ghi họ và tên của người nuôi dưỡng.|
|4|ngaysinh_nnd|DATE|Ghi ngày sinh của người nuôi dưỡng.|
|5|ma_dantoc_nnd|VARCHAR(2)|Ghi mã dân tộc của người nuôi dưỡng theo Danh mục các dân tộc Việt Nam ban hành kèm theo [Quyết định số 121-TCTK/PPCĐ](http://tongdieutradanso.vn/danh-muc-cac-dan-toc-viet-nam.html) ngày 02 tháng 3 năm 1979 của Tổng cục trưởng Tổng cục Thống kê để điền chi tiết). Tra cứu mã dân tộc tại đường link: [http://tongdieutradanso.vn/danh-muc-cac-dan-toc-viet-nam.html](http://tongdieutradanso.vn/danh-muc-cac-dan-toc-viet-nam.html)|
|6|so_cccd_nnd|VARCHAR(15)|Ghi số chứng minh nhân dân hoặc số căn cước công dân hoặc số hộ chiếu của người nuôi dưỡng.|
|7|ngaycap_cccd_nnd|DATE|Ghi ngày cấp chứng minh nhân dân hoặc căn cước công dân hoặc hộ chiếu của người nuôi dưỡng.|
|8|noicap_cccd_nnd|VARCHAR(1024)|Ghi nơi cấp chứng minh nhân dân hoặc căn cước công dân hoặc hộ chiếu của người nuôi dưỡng.|
|9|noi_cu_tru_nnd|VARCHAR(1024)|Ghi địa chỉ nơi cư trú hiện tại của người nuôi dưỡng.<br/>**Lưu ý**:<br/>- Nếu là người Việt Nam: Ghi địa chỉ nơi cư trú theo địa danh 4 cấp: Thôn/bản, xã/phường/thị trấn, quận/huyện/ thành phố thuộc tỉnh, tỉnh/thành phố trực thuộc trung ương;<br/>- Trường hợp người nước ngoài có địa chỉ nơi cư trú tại Việt Nam thì ghi giống như người Việt Nam;<br/>- Trường hợp người nước ngoài không có địa chỉ nơi cư trú tại Việt Nam nhưng sinh đẻ tại cơ sở y tế của Việt Nam thì ghi tên tỉnh/thành phố/bang và quốc gia nơi họ đang sinh sống.|
|10|ma_quoctich_nnd|VARCHAR(3)|Ghi mã quốc tịch của người nuôi dưỡng theo quy định tại Phụ lục 2 [Thông tư số 07/2016/TT-BCA](https://congan.quangngai.gov.vn/documents/8878324/9231653/0_20200704221919.pdf/fcd11c17-3599-43f0-ae40-0d5e467bb10d) ngày 01 tháng 2 năm 2016 của Bộ trưởng Bộ Công an.|
|11|id_cu_tru_nnd|VARCHAR(20)|Ghi mã ID cư trú của người nuôi dưỡng theo `dmxa4750.id`.|

:white_check_mark: **Quy trình áp dụng**

:blue_book: **Module Treatment**:

- Tại form **[Thông tin con sản phụ]**: Thiết kế bổ sung các control *(có thể tạo form riêng)* hỗ trợ cập nhật dữ liệu thông tin người nuôi dưỡng, chi tiết gồm:<br/>
➡️ **Mã số BHXH**: tương ứng với `ttcon.ma_bhxh_nnd`.<br/>
➡️ **Mã thẻ BHYT**: tương ứng với  `ttcon.ma_the_nnd`.<br/>
➡️ **Họ và tên**: tương ứng với  `ttcon.ho_ten_nnd`.<br/>
➡️ **Ngày sinh**: tương ứng với  `ttcon.ngaysinh_nnd`.<br/>
➡️ **Dân tộc**: tương ứng với `ttcon.ma_dantoc_nnd`, lấy dữ liệu từ `dmdantoc.ma4750`. <br/>
➡️ **CMND/CCCD/Hộ chiếu**: tương ứng với  `ttcon.so_cccd_nnd`. Lưu ý: Quy tắt ghi nhận và hiệu chỉnh thông tin này xem chi tiết [tại đây](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750.md#user-content-fnref-2024-10-11-03-f331f7b8761be633652c83e6f0e58e9f).<br/>
➡️ **Ngày cấp CMND/CCCD/Hộ chiếu**: tương ứng với  `ttcon.ngaycap_cccd_nnd`. Lưu ý: nếu ô `[CMND/CCCD/Hộ chiếu]` khác rỗng thì bắt buộc nhập giá trị cột này.<br/>
➡️ **Nơi cấp CMND/CCCD/Hộ chiếu**: tương ứng với  `ttcon.noicap_cccd_nnd`. Lưu ý: nếu ô `[CMND/CCCD/Hộ chiếu]` khác rỗng thì bắt buộc nhập giá trị cột này.<br/>
➡️ **Nơi cư trú**: tương ứng với  `ttcon.noi_cu_tru_nnd`. Đây là địa chỉ người nuôi dưỡng. Quy tắt ghi nhận/lưu giống với `dmbenhnhan.diachi`.<br/>
➡️ **Quốc tịch**: tương ứng với  `ttcon.ma_quoctich_nnd`. lấy dữ liệu từ `dmquocgia.ma4750`.<br/>
➡️ **ID đơn vị hành chánh**: tương ứng với  `ttcon.id_cu_tru_nnd`. lấy dữ liệu từ `dmxa4750.id`. Thiết kế các control cho phép chọn: tỉnh, huyện và xã *(giống như thông tin đơn vị hành chánh của thông tin sản phụ)*.

<p align="center"><img src="https://github.com/user-attachments/assets/dbe3603d-7a5c-4599-a8a3-7f5c2c25b26b" width="70%"></p>

- Các biểu mẫu/thông tin có liên quan người nuôi dưỡng: ưu tiên lấy thông tin từ `ttcon.ho_ten_nnd`, nếu `ttcon.ho_ten_nnd` rỗng thì lấy thông tin người nuôi dưỡng là thông tin của sản phụ `(như cũ)`.

:blue_book: Các phân hệ xuất và load dữ liệu **XML4750**:

- Thực hiện xuất và load dữ liệu theo mô tả tại: [xml130.bang9: Chỉ tiêu dữ liệu giấy chứng sinh](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/Table%20xml130.bang09%20-%20%5BPh%E1%BB%A5%20l%E1%BB%A5c%20-%20M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750%5D.md).
