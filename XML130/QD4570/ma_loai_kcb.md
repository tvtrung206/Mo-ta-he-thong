# 📘Phụ lục: Bảng giá trị cho cột `ma_loai_kcb`
Chi tiết xem tại Phụ lục 1 (Danh mục mã loại hình khám bệnh, chữa bệnh) – [Quyết định 824/QĐ-BYT](https://github.com/dh-hos/Mo-ta-he-thong/blob/80dfedaffd557024c054fd720545a11becd0b537/XML130/Q%C4%90%20824-B%E1%BB%95%20sung%20m%C3%A3%20d%C3%B9ng%20chung.pdf) ngày 15/02/2023.

Ghi nhận giá trị ưu tiên từ trên xuống:
|Giá trị|Diễn giải|Điều kiện|
|:-------:|-------|-------|
|07|Khám ngoại trú: nhận thuốc theo hẹn (không khám bệnh).|`psdangky.trangthaichuyentuyen = (5 hoặc 6)`[^2024-09-12-01]|
|08|Khám bệnh ngoại trú.|`MAX(khambenh.songaydt) > 0`|
|05|Bệnh án ngoại trú thanh toán ngày (có khám bệnh và lĩnh thuốc).|[`bnnoitru.namvien = 0` và `bnnoitru.bant = 1`] và [`KHÔNG phát sinh cận lâm sàng, trừ công khám`] và [`CÓ toa thuốc`]|
|01|Khám bệnh ngoại trú.||
|02|Bệnh án ngoại trú thanh toán cuối đợt.|[`bnnoitru.namvien = 0` và `bnnoitru.bant = 0`]|
|03|Bệnh án nội trú.||
|09|Bệnh án nội trú (dưới 4 giờ).||

[^2024-09-12-01]: Thay đổi ngày 12/09/2024: Cập nhật điều kiện  đối với `ma_loai_kcb = '07'`.  Thay đổi theo yêu cầu [tại đây](https://github.com/dh-hos/THEO-DOI-THUC-HIEN/issues/127).
