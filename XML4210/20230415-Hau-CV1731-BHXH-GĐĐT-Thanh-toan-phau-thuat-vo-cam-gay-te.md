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

###### :eight_spoked_asterisk: Xử lý yêu cầu

:white_check_mark: **Thay đổi cấu trúc dữ liệu**

1. Thêm cột `dmcls.vocamgayte` `NUMERIC (1,0)` `(0: Bình thường, 1: Thuộc phẫu thuật vô cảm gây tê)`
2. Thêm tham số sử dụng chung `XML.vocamgayte` `Thanh toán phẫu thuật sử dụng phương pháp vô cảm gây tê theo Công văn 1731-BHXH-GĐĐT (0: Không áp dụng, 1: Áp dụng)`

:white_check_mark: **Module Admin - Thêm chức năng cấu hình những cận lâm sàng thuộc Phẫu thuật sử dụng phương pháp vô cảm gây tê**
1. Thêm checkbox để xác định những cận lâm sàng thuộc loại vô cảm gây tê dựa vào giá trị của `dmcls.vocamgayte`

:white_check_mark: **Module + Chức năng xuất XML4210**

1. Khi tham số `XML.vocamgayte != 1`: thực hiện bình thường không thay đổi theo mô tả này.
2. Khi tham số `XML.vocamgayte = 1` và cận lâm sàng có cấu hình `dmcls.vocamgayte = 1` sẽ áp dụng theo nguyên tắc sau:

- `XML3.MA_DICH_VU` sẽ nối thêm chuỗi `_GT` khi thực hiện xuất XML
- `XML3.TEN_DICH_VU` sẽ nối thêm chuỗi `[gây tê]` khi thực hiện xuất XML
- Áp dụng đối với những hàng hóa thuộc [Toa Vật tư kèm theo] những cận lâm sàng có cấu hình `dmcls.vocamgayte = 1`, `XML2.MA_THUOC` sẽ nối thêm chuỗi `_GT` khi thực hiện xuất XML
