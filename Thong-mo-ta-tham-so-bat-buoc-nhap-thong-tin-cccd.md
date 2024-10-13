<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### Chủ đề: MÔ TẢ BỔ SUNG THAM SỐ TÙY CHỌN ÁP DỤNG KHI NHẬP THÔNG TIN CMND/CCCD

</div>

###### :eight_spoked_asterisk: Người lập: [**Lê Quốc Thống**](https://github.com/lequocthong29)

###### :eight_spoked_asterisk: Ngày lập: **13/10/2024**

###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**

###### :eight_spoked_asterisk: Xử lý yêu cầu
###### :eight_spoked_asterisk: Thêm tham số: cccd.thongtin

	cccd.thongtin: cảnh báo và chặn nếu không nhập thông tin nơi cấp và ngày cấp CMND/CCCD
 	Giá trị: 
  		- 0: Không bắt buộc
    	- 1: bắt buộc nhập ngày cấp, nơi cấp nếu ô CMND/CCCD có giá trị

Câu SQL Insert tham số:
```sql


INSERT INTO  current.system(id,tents,diengiai,giatri,loai,module)
SELECT (SELECT CAST(MAX(id) AS DECIMAL)+ 1 FROM current.system),
		'cccd.thongtin',
        'cảnh báo và chặn nếu không nhập thông tin nơi cấp và ngày cấp CMND/CCCD' 
        || E'\n' 
        ||'Giá trị:' || E'\n' 
        ||'- 0 (hoặc null): Không bắt buộc.' || E'\n' 
        ||'- 1: bắt buộc nhập ngày cấp, nơi cấp nếu ô CMND/CCCD có giá trị.' || E'\n',
        '0',
        '1',
        '0'
        WHERE NOT EXISTS
        	(
            	SELECT tents FROM current.system
        		WHERE UPPER(tents) = UPPER('cccd.thongtin')
        	);
```
