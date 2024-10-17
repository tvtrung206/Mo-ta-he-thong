

<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: CẬP NHẬT THAM SỐ HỆ THỐNG

</div>

###### :eight_spoked_asterisk: Người lập: [**NGHỊ VĂN BI**](https://github.com/ongtrieuhau)

###### :eight_spoked_asterisk: Ngày lập: **12/10/2024**

###### :eight_spoked_asterisk: Khách hàng: **92118 - Bệnh viện phụ sản Cần thơ**

###### :eight_spoked_asterisk: Yêu cầu phát sinh

- Phân loại bệnh nhân có nguy cơ té ngã, ghi nhận các dấu hiệu.
- Hiển thị chỉ thỉ màu theo phân loại bệnh nhân có nguy cơ té ngã.

###### :eight_spoked_asterisk: Xử lý yêu cầu

:white_check_mark: **Thay đổi cấu trúc dữ liệu**

+ Cập nhật cấu trúc:
Thêm bảng dữ liệu "current.pstenga" cụ thể:

CREATE TABLE current.pstenga (

  mabn VARCHAR(20),
  
  makb VARCHAR(20),
  
  nguycocao NUMERIC(1,0),
  
  nguycotrungbinh NUMERIC(1,0),
  
  capcuunang NUMERIC(1,0),
  
  chidinhchamsoc NUMERIC(1,0),
  
  tsdiung NUMERIC(1,0),
  
  nhiem NUMERIC(1,0),
  
  khongnguoinha NUMERIC(1,0),
  
  khuyentat NUMERIC(1,0),
  
  uutienhotro NUMERIC(1,0),
  
  ycdichvu NUMERIC(1,0),
  
  diem NUMERIC(3,0),
  
  loai NUMERIC(1,0)
  
) 

WITH (oids = false);


COMMENT ON COLUMN current.pstenga.loai
IS 'Phân loại bệnh nhân té ngã';

ALTER TABLE current.pstenga
  OWNER TO postgres;
  
:white_check_mark: **Xử lý**
1. Module Register:

- Bổ sung các control ghi nhận phận loại và dấu hiệu bệnh nhân có nguy cơ té ngã.
- Cập nhật với current.pstenga theo lần khám.
- Cập nhật in tem vòng tay với 4 dấu hiệu từ trên xuống theo thứ tự.
  
2. Module Prescription:

- Thể hiện thêm thông tin chỉ thị màu theo phân loại té ngã (nếu có) tại danh sách khám, cụ thể (R,G,B):
  + current.loai = 1 -->  (255, 0, 0);
  + current.loai = 2 -->  (255, 255, 0);
  + current.loai = 3 -->  (128, 0, 128);
  + current.loai = 4 -->  (192, 192, 192);
  + current.loai = 5 -->  (0, 176, 240);

  
