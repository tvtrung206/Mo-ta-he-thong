<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: THANH TOÁN PHẪU THUẬT SỬ DỤNG PHƯƠNG PHÁP VÔ CẢM GÂY TÊ

</div>

###### :eight_spoked_asterisk: Người lập: [**ÔNG TRIỆU HẬU**](https://github.com/ongtrieuhau)

###### :eight_spoked_asterisk: Ngày lập: **15/04/2023**

###### :eight_spoked_asterisk: Ngày hoàn thành dự kiến: **17/04/2023**

###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**

###### :eight_spoked_asterisk: Yêu cầu phát sinh

- Thực hiện theo công văn: [31-BHXH-GĐBHYT-Công văn vv mã hóa tạm thời đối với dịch vụ kỹ thuật sử dụng phương pháp vô cảm gây tê chư quy định giá.pdf](../CONGVAN-YEUCAU/31-BHXH-G%C4%90BHYT-C%C3%B4ng%20v%C4%83n%20vv%20m%C3%A3%20h%C3%B3a%20t%E1%BA%A1m%20th%E1%BB%9Di%20%C4%91%E1%BB%91i%20v%E1%BB%9Bi%20d%E1%BB%8Bch%20v%E1%BB%A5%20k%E1%BB%B9%20thu%E1%BA%ADt%20s%E1%BB%AD%20d%E1%BB%A5ng%20ph%C6%B0%C6%A1ng%20ph%C3%A1p%20v%C3%B4%20c%E1%BA%A3m%20g%C3%A2y%20t%C3%AA%20ch%C6%B0%20quy%20%C4%91%E1%BB%8Bnh%20gi%C3%A1.pdf)
- [^2023-06-13] Thực hiện theo [công văn PHỤ SẢN CẦN THƠ](../CONGVAN-YEUCAU/1067-BVPS%20vv%20de%20nghi%20bo%20sung%20mot%20so%20chuc%20nang%20phan%20mem%20DGH.Hospital.pdf)

###### :eight_spoked_asterisk: Xử lý yêu cầu

:white_check_mark: **Thay đổi cấu trúc dữ liệu**

1. Thêm cột `dmcls.vocamgayte` `NUMERIC (1,0)` `(0: Bình thường, 1: Thuộc phẫu thuật vô cảm gây tê)`

2. Thêm tham số sử dụng chung `XML.vocamgayte` `Thanh toán phẫu thuật sử dụng phương pháp vô cảm gây tê theo Công văn 1731-BHXH-GĐĐT (0: Không áp dụng, 1: Áp dụng)`

3. [^2023-06-13] Thêm tham số sử dụng chung `XML.vocamgayte.cauhinh` `Cấu hình trường XML được ghép thêm chuỗi (khi XML.vocamgayte=1), nếu áp dụng nhiều trường thì cách nhau dấu | . Ví dụ: XML3.MA_DICH_VU | XML3.TEN_DICH_VU. [Ghi chú các giá trị chấp nhận: XML3.MA_DICH_VU, XML3.TEN_DICH_VU, XML2.MA_THUOC. XML được ghép như sau (XML3.MA_DICH_VU + '_GT'; XML3.TEN_DICH_VU + '[gây tê]', XML2.MA_THUOC + XML3.MA_DICH_VU + '_GT')]`

- `ALTER TABLE current.dmcls ADD COLUMN vocamgayte NUMERIC(1,0) DEFAULT 0;
COMMENT ON COLUMN current.dmcls.vocamgayte IS '(0: Bình thường, 1: Thuộc phẫu thuật vô cảm gây tê)';`

- `INSERT INTO current.system (id,tents,diengiai,giatri,loai,module)
SELECT (SELECT max(id)+1 FROM current.system),
 'XML.vocamgayte',
 'Thanh toán phẫu thuật sử dụng phương pháp vô cảm gây tê theo Công văn 1731-BHXH-GĐĐT (0: Không áp dụng, 1: Áp dụng)',
    0,0,1
WHERE NOT EXISTS (SELECT tents FROM current.system WHERE tents = 'XML.vocamgayte');`

- [^2023-06-13] `INSERT INTO current.system (id,tents,diengiai,giatri,loai,module)
SELECT
 (SELECT max(id)+1 FROM current.system),
    'XML.vocamgayte.cauhinh', E'Cấu hình trường XML được ghép thêm chuỗi (khi XML.vocamgayte=1), nếu áp dụng nhiều trường thì cách nhau dấu |. \r\n - [Ghi chú các giá trị chấp nhận: XML3.MA_DICH_VU, XML3.TEN_DICH_VU, XML2.MA_THUOC.\r\n XML được ghép như sau (XML3.MA_DICH_VU + ''_GT''; XML3.TEN_DICH_VU + ''[gây tê]'', XML2.MA_THUOC + XML3.MA_DICH_VU + ''_GT'')]. \r\n - Ví dụ: XML3.MA_DICH_VU | XML3.TEN_DICH_VU.',
    'XML3.MA_DICH_VU|XML3.TEN_DICH_VU|XML2.MA_THUOC'
    ,
    0,
    1
WHERE NOT EXISTS (SELECT tents FROM current.system WHERE tents = 'XML.vocamgayte.cauhinh');`

:white_check_mark: **Module Admin - Thêm chức năng cấu hình những cận lâm sàng thuộc Phẫu thuật sử dụng phương pháp vô cảm gây tê**

1. Thêm checkbox để xác định những cận lâm sàng thuộc loại vô cảm gây tê dựa vào giá trị của `dmcls.vocamgayte`

:white_check_mark: **Module + Chức năng xuất XML4210**

1. Khi tham số `XML.vocamgayte != 1`: thực hiện bình thường không thay đổi theo mô tả này.
2. Khi tham số `XML.vocamgayte = 1` và cận lâm sàng có cấu hình `dmcls.vocamgayte = 1` sẽ áp dụng theo nguyên tắc sau:

[^2023-06-13] Dựa vào tham số `XML.vocamgayte.cauhinh` để xác định các trường cần nối chuỗi khi xuất XML theo dạng có chứa chuỗi. VD: `XML.vocamgayte.cauhinh` = `XML3.MA_DICH_VU | XML3.TEN_DICH_VU` thì khi xuất XML sẽ thực hiện ghép chuỗi đối 2 trường là `XML3.MA_DICH_VU` và `XML3.TEN_DICH_VU`. Nguyên tắc nối chuỗi như sau:

- `XML3.MA_DICH_VU` sẽ nối thêm chuỗi `_GT` khi thực hiện xuất XML
- `XML3.TEN_DICH_VU` sẽ nối thêm chuỗi `[gây tê]` khi thực hiện xuất XML
- Áp dụng đối với những hàng hóa thuộc [Toa Vật tư kèm theo] những cận lâm sàng có cấu hình `dmcls.vocamgayte = 1`, `XML2.MA_THUOC` sẽ nối thêm chuỗi XML3.MA_DICH_VU và `_GT` theo cú pháp `MATHUOC_MADVKT_GT` [Theo yêu cầu](https://github.com/dh-hos/dhg.hospitaladmin/issues/36) khi thực hiện xuất XML

[^2023-06-13]: Thay đổi ngày 2023-06-13.
