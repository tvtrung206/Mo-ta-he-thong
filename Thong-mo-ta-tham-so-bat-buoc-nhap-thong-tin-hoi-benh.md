<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### Chủ đề: MÔ TẢ BỔ SUNG THAM SỐ TÙY CHỌN ÁP DỤNG KHI NHẬP THÔNG TIN HỎI BỆNH

</div>

###### :eight_spoked_asterisk: Người lập: [**Lê Quốc Thống**](https://github.com/lequocthong29)

###### :eight_spoked_asterisk: Ngày lập: **01/10/2024**

###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**

###### :eight_spoked_asterisk: Xử lý yêu cầu
###### :eight_spoked_asterisk: Thêm tham số: kbhoibenh

	kbkhambenh: cảnh báo hoặc chặn nếu không nhập thông tin hỏi bệnh
 	Giá trị: 
  		- 0: Không bắt buộc
    	- 1: Bắt buộc đối với đối tượng BHYT và trẻ em
    	- 2: Bắt buộc đối với tất cả các đối tượng

Câu SQL Insert tham số:
```sql


INSERT INTO  current.system(id,tents,diengiai,giatri,loai,module)
SELECT (SELECT CAST(MAX(id) AS DECIMAL)+ 1 FROM current.system),
		'kbhoibenh',
        'Cảnh báo hoặc chặn nếu không nhập hỏi bệnh tại form khám bệnh' 
        || E'\n' 
        ||'Giá trị:' || E'\n' 
        ||'- 0 (hoặc null): Không bắt buộc.' || E'\n' 
        ||'- 1: Bắt buộc với đối tượng BHYT + Trẻ em.' || E'\n'
        ||'- 2: Bắt buộc tất cả các đối tượng.',
        '0',
        '1',
        '0'
        WHERE NOT EXISTS
        	(
            	SELECT tents FROM current.system
        		WHERE UPPER(tents) = UPPER('kbhoibenh')
        	);
```

:white_check_mark: **Prescription**
- Kiểm tra thông tin hỏi bệnh:
 ![image](https://i.imgur.com/1tO2q0x.png)
