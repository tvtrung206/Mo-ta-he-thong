<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>
<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: CÁCH GHI NHẬN GIÁ TRỊ CỘT XML1.MA_LYDO_VVIEN (cột 16, bảng 1 - XML4210)
</div>

###### :eight_spoked_asterisk: Người lập: [**vinh-dh**](https://github.com/vinh-dh)
###### :eight_spoked_asterisk: Ngày lập: **24/05/2024**
###### :eight_spoked_asterisk: Ngày cập nhật: **11/06/2024**
###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**
###### :eight_spoked_asterisk: Yêu cầu phát sinh

- Thực hiện theo yêu cầu chi tiết tại: 
1. [Yêu cầu - trường tên bệnh XML bệnh án ngoại trú thanh toán đợt chỉ lấy chẩn đoán cuối khi xuất viện (PK Medic miền đông #12)](https://github.com/dh-hos/Yeu_cau_ho_tro/issues/12)
2. [Yêu cầu - Xác định mã lý do vào viện trên bảng kê 6556 và XML 4210 ( trường hợp bệnh nhân có giấy xác nhận cư trú)  #389](https://github.com/dh-hos/To_Lap_Trinh/issues/389)
3. [Yêu cầu - Đề nghị hỗ trợ trường hợp bệnh nhân có tạm trú trên địa bàn khám bệnh của đơn vị (PK Medic Miền Đông)  #4](https://github.com/dh-hos/Yeu_cau_ho_tro/issues/4)
- Thực hiện theo Quyết định: [4210/QĐ-BYT - ngày 20/09/2017 của Bộ Y tế](https://github.com/dh-hos/Mo-ta-he-thong/files/9967120/QD-2017-4210_20170920.pdf)

###### :eight_spoked_asterisk: Xử lý yêu cầu: Các phân hệ xuất dữ liệu theo 4210

:white_check_mark: **Đối với `khám bệnh ngoại trú`/`toa nội trú xuất viện`/`bệnh án ngoại trú quyết toán ngày`**: Giá trị `XML1.MA_LYDO_VVIEN` được xác định như sau:\
Thực hiện xét điều kiện theo trình tự ưu tiên từ trên xuống:
|TT| GIÁ TRỊ | DIỄN GIẢI | ĐIỀU KIỆN XÉT |
|:-------:|:-------:|-------|-------|
|1|2|Cấp cứu|`khambenh.tinhtrang = 0` (dựa vào dòng dữ liệu khám cuối của: khám bệnh ngoại trú/bệnh án ngoại trú quyết toán ngày) hoặc `bnnoitru.tinhtrangvv = '1'` (toa nội trú xuất viện).|
|2|1|Đúng tuyến|[`psdangky.tuyen = 0` (khám bệnh ngoại trú/bệnh án ngoại trú quyết toán ngày) hoặc `bnnoitru.tuyen = 0` (toa nội trú xuất viện)] và [`psdangky.giayxacnhancutru = 1`] (tham khảo cột `giayxacnhancutru` tại [Mô tả XML130 - Bổ sung QĐ 4750](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750.md)).|
|3|3|Trái tuyến (được hưởng như đúng tuyến)|[`psdangky.tuyen = 0` (khám bệnh ngoại trú/bệnh án ngoại trú quyết toán ngày) hoặc `bnnoitru.tuyen = 0` (toa nội trú xuất viện)] và [`psdangky.tuyenxml = 1`].|
|4|1|Đúng tuyến|[`psdangky.tuyen = 0` (khám bệnh ngoại trú/bệnh án ngoại trú quyết toán ngày) hoặc `bnnoitru.tuyen = 0` (toa nội trú xuất viện)] và [giá trị tham số `tuyenbv = 3` (bệnh viện tuyến tỉnh)].|
|5|1|Đúng tuyến|[`psdangky.tuyen = 0` (khám bệnh ngoại trú/bệnh án ngoại trú quyết toán ngày) hoặc `bnnoitru.tuyen = 0` (toa nội trú xuất viện)] và [`psdangky.mabvdk = psdangky.mabvkb` (khám bệnh ngoại trú/bệnh án ngoại trú quyết toán ngày) hoặc `bnnoitru.mabvdk = bnnoitru.mabvkb` (toa nội trú xuất viện)].|
|6|1|Đúng tuyến|[`psdangky.tuyen = 0` (khám bệnh ngoại trú/bệnh án ngoại trú quyết toán ngày) hoặc `bnnoitru.tuyen = 0` (toa nội trú xuất viện)] và [`dmbvcunghuyen.cunghuyen = 1`, tham chiếu `psdangky.mabvdk = dmbvcunghuyen.mabv` (khám bệnh ngoại trú/bệnh án ngoại trú quyết toán ngày) hoặc `bnnoitru.mabvdk = dmbvcunghuyen.mabv` (toa nội trú xuất viện)].|
|7|1|Đúng tuyến|[`psdangky.tuyen = 0` (khám bệnh ngoại trú/bệnh án ngoại trú quyết toán ngày) hoặc `bnnoitru.tuyen = 0` (toa nội trú xuất viện)] và [`psdangky.mabvdk != psdangky.mabvkb` (khám bệnh ngoại trú/bệnh án ngoại trú quyết toán ngày) hoặc `bnnoitru.mabvdk != bnnoitru.mabvkb` (toa nội trú xuất viện)] và `psdangky.trangthaichuyentuyen IN (2,3,4,5)` (tham khảo cột `trangthaichuyentuyen` tại [Mô tả XML130 - Bổ sung QĐ 4750](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750.md)).|
|8|4|Thông tuyến|[`psdangky.tuyen = 0` (khám bệnh ngoại trú/bệnh án ngoại trú quyết toán ngày) hoặc `bnnoitru.tuyen = 0` (toa nội trú xuất viện)] và [`psdangky.mabvdk != psdangky.mabvkb` (khám bệnh ngoại trú/bệnh án ngoại trú quyết toán ngày) hoặc `bnnoitru.mabvdk != bnnoitru.mabvkb` (toa nội trú xuất viện)].|
|9|3|Trái tuyến|Ngoài các trường hợp trên.|

:white_check_mark: **Đối với `Bệnh án nội trú`/`Bệnh án ngoại trú (quyết toán cuối đợt)`**: Giá trị `XML1.MA_LYDO_VVIEN` được xác định như sau:\
Thực hiện xét điều kiện theo trình tự ưu tiên từ trên xuống:
|TT| GIÁ TRỊ | DIỄN GIẢI | ĐIỀU KIỆN XÉT |
|:-------:|:-------:|-------|-------|
|1|2|Cấp cứu|`bnnoitru.tinhtrangvv = '1'`.|
|2|1|Đúng tuyến|[`bnnoitru.tuyen = 0`] và [`psdangky.giayxacnhancutru = 1`] (tham khảo cột `giayxacnhancutru` tại [Mô tả XML130 - Bổ sung QĐ 4750](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750.md)).|
|3|3|Trái tuyến (được hưởng như đúng tuyến)|[`bnnoitru.tuyen = 0`] và [`bnnoitru.tuyenxml = 1`].|
|4|1|Đúng tuyến|[`bnnoitru.tuyen = 0`] và [giá trị tham số `tuyenbv = 3`].|
|5|1|Đúng tuyến|[`bnnoitru.tuyen = 0`] và [`bnnoitru.mabvdk = bnnoitru.mabvkb`].|
|6|1|Đúng tuyến|[`bnnoitru.tuyen = 0`] và [`dmbvcunghuyen.cunghuyen = 1`, tham chiếu `bnnoitru.mabvdk = dmbvcunghuyen.mabv`].|
|7|1|Đúng tuyến|[`bnnoitru.tuyen = 0`] và [`bnnoitru.mabvdk != bnnoitru.mabvkb`] và `psdangky.trangthaichuyentuyen IN (2,3,4,5)` (tham khảo cột `trangthaichuyentuyen` tại [Mô tả XML130 - Bổ sung QĐ 4750](https://github.com/dh-hos/Mo-ta-he-thong/blob/main/XML130/QD4570/M%C3%B4%20t%E1%BA%A3%20XML130%20-%20B%E1%BB%95%20sung%20Q%C4%90%204750.md)).|
|8|4|Thông tuyến|[`bnnoitru.tuyen = 0`] và [`bnnoitru.mabvdk != bnnoitru.mabvkb`].|
|9|3|Trái tuyến|Ngoài các trường hợp trên.|
