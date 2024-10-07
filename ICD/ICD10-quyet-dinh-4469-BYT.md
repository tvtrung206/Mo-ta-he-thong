<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: HỖ TRỢ CHẨN ĐOÁN ICD10 THEO QUYẾT ĐỊNH 4469-BYT

</div>

###### :eight_spoked_asterisk: Người lập: [Lê Quốc Thống](https://github.com/lequocthong29)

###### :eight_spoked_asterisk: Ngày lập: 07/10/2024

###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**

###### :eight_spoked_asterisk: Yêu cầu phát sinh

###### :eight_spoked_asterisk: Xử lý yêu cầu

- Hỗ trợ cảnh báo hoặc chặn ICD 10 khi gõ vào chẩn đoán chính theo quyết định 4469-BYT

:white_check_mark: **Thay đổi cấu trúc dữ liệu**
- Bổ sung cột `cdc_loaitru`.
  
   Nội dung : Loại trừ ICD không cho sử dụng làm chẩn đoán chính.
  
        - 0: hoặc null : Không sử dụng
        - 1: Không cho sử dụng làm chẩn đoán chính
```sql
    ALTER TABLE current.dmicd
    ADD COLUMN cdc_loaitru NUMERIC(1);
```


- Bổ sung tham số `sudung.maicd.chandoanchinh`.
  
  `sudung.maicd.chandoanchinh`: Cảnh báo hoặc chặn ICD 10 khi gõ vào chuẩn đoán chính.
  
  Nội dung :
  
        - 0: Không áp dụng
        - 1: Cảnh báo
        - 2: Không cho phép

```sql
   INSERT INTO  current.system(id,tents,diengiai,giatri,loai,module)
   SELECT (SELECT CAST(MAX(id) AS DECIMAL)+ 1 FROM current.system),
  		'sudung.maicd.chandoanchinh',
          'Cấu hình áp dụng khi chỉ định Mã ICD thuộc ICD Loại trừ theo QĐ.4469.BYT vào chẩn đoán chính.' 
          || E'\n' 
          ||'Giá trị:' || E'\n' 
          ||'- 0 (hoặc null): Cho phép.' || E'\n' 
          ||'- 1: Cảnh báo và cho phép.' || E'\n'
          ||'- 2: Cảnh báo và chặn.',
          '0',
          '1',
          '0'
          WHERE NOT EXISTS
          	(
              	SELECT tents FROM current.system
          		WHERE UPPER(tents) = UPPER('sudung.maicd.chandoanchinh')
          	);
```
    

:white_check_mark: **Xử lý nghiệp vụ tại Admin**

- Tại `danh mục ICD` Thêm chức năng hỗ trợ người dùng tự cấu hình mã ICD 10 không được nhập vào chuẩn đoán chính:
- Xử lý :
    + Thêm checkbox hỗ trợ người dùng check chọn loại trừ ICD không cho sử dụng làm chẩn đoán chính
    + Lưu kết quả vào cột `current.dmicd.cdc_loaitru`:
      
        + cdc_loaitru = 0 hoặc null : Cho phép sử dụng làm chẩn đoán chính.      
        + cdc_loaitru = 1 : Không cho phép sử dụng làm chẩn đoán chính.

:white_check_mark: **Xử lý nghiệp vụ tại Prescription và Treatment**

- khi người dùng nhập chẩn đoán chính, thực hiện kiểm tra mã icd theo danh mục icd.
  - Trường hợp `current.dmicd.cdc_loaitru` = 0 :
     - Cho phép lưu chẩn đoán như bình thường.
  
  - Trường hợp `current.dmicd.cdc_loaitru` = 1 :
     - Kiểm tra tham số `sudung.maicd.chandoanchinh` :
       + `sudung.maicd.chandoanchinh` = 0 : Cho phép lưu chẩn đoán như bình thường.       
       + `sudung.maicd.chandoanchinh` = 1 : Cảnh báo mã ICD không được phép chọn làm chẩn đoán chính -> vẫn cho phép lưu chẩn đoán.     
       + `sudung.maicd.chandoanchinh` = 2 : Cảnh báo mã ICD không được phép chọn làm chẩn đoán chính -> Không cho phép lưu chẩn đoán.
       
