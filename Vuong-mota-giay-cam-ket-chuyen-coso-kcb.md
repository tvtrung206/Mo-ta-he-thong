<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### Chủ đề: MÔ TẢ GIẤY CAM KẾT CHUYỂN CƠ SỞ KHÁM BỆNH, CHỮA BỆNH

</div>

###### :eight_spoked_asterisk: Người lập: [**Nguyễn Triều Vương**](https://github.com/vuongdh)

###### :eight_spoked_asterisk: Ngày lập: **23/10/2024**

###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**

###### :eight_spoked_asterisk: Xử lý yêu cầu
###### :eight_spoked_asterisk: Thay đổi cấu trúc dữ liệu

```sql

INSERT INTO  current.system(id,tents,diengiai,giatri,loai,module)
SELECT (SELECT CAST(MAX(id) AS DECIMAL)+ 1 FROM current.system),
		'ekip.pttt',
        'Ê kíp phẫu thuật thủ thuật chỉ hiển thị nhân viên có chứng chỉ hành nghề.' 
        || E'\n' 
        ||'Giá trị:' || E'\n' 
        ||'- 0 (hoặc null): Không áp dụng (hiển thị tất cả).' || E'\n' 
        ||'- 1: Áp dụng (chỉ hiển thị nhân viên có chứng chỉ hành nghề).',
        '0',
        '1',
        '0'
        WHERE NOT EXISTS
        	(
            	SELECT tents FROM current.system
        		WHERE UPPER(tents) = UPPER('ekip.pttt')
        	);
```

:white_check_mark: **Treatment**
- Lập phiếu phẫu thuật:
  ![image](https://github.com/user-attachments/assets/dec40ce8-2177-476e-ab62-270c542a0c22)

  - Nếu ekip.pttt = 0: Load tất cả nhân viên
  - Nếu ekip.pttt = 1: Chỉ load nhân viên có chứng chỉ hành nghề
    
:white_check_mark: **Prescription**
- Lập phiếu PT-TT:
  	- Nếu ekip.pttt = 0: Load tất cả nhân viên
  	- Nếu ekip.pttt = 1: Chỉ load nhân viên có chứng chỉ hành nghề
