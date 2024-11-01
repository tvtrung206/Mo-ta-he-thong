<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### Chủ đề: MÔ TẢ BỔ SUNG THAM SỐ ÁP DỤNG ĐỐI VỚI BỆNH NHÂN BHYT CÓ TOA NGOẠI TRÚ KHI CHỈNH XỬ TRÍ NHẬP VIỆN

</div>

###### :eight_spoked_asterisk: Người lập: [**Lê Quốc Thống**](https://github.com/lequocthong29)

###### :eight_spoked_asterisk: Ngày lập: **01/11/2024**

###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**

###### :eight_spoked_asterisk: Xử lý yêu cầu
###### :eight_spoked_asterisk: Thêm tham số: toangoaitru.nhapvien

	toangoaitru.nhapvien: chặn bệnh nhận BHYT có toa ngoại trú khi chỉnh xử trí thành nhập viện
 	Giá trị: 
  		- 0: Không áp dụng.
    	- 1: Áp dụng.

Câu SQL Insert tham số:
```sql
INSERT INTO  current.system(id,tents,diengiai,giatri,loai,module)
SELECT (SELECT CAST(MAX(id) AS DECIMAL)+ 1 FROM current.system),
		'toangoaitru.nhapvien',
        'Chặn bệnh nhận BHYT có toa ngoại trú khi chỉnh xử trí thành nhập viện' 
        || E'\n' 
        ||'Giá trị:' || E'\n' 
        ||'- 0 (hoặc null): Không bắt buộc.' || E'\n' 
        ||'- 1: Bắt buộc' || E'\n',
        '0',
        '1',
        '0'
        WHERE NOT EXISTS
        	(
            	SELECT tents FROM current.system
        		WHERE UPPER(tents) = UPPER('toangoaitru.nhapvien')
        	);
```

