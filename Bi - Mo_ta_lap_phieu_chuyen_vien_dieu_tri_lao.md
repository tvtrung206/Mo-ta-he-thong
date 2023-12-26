
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

###### :eight_spoked_asterisk: Người lập: [**NGHỊ VĂN BI**]

###### :eight_spoked_asterisk: Ngày lập: **26/12/2023**

###### :eight_spoked_asterisk: Khách hàng: **87115 - Bệnh viện Phổi Đồng Tháp**

###### :eight_spoked_asterisk: Yêu cầu phát sinh

- Lập phiếu chuyển viện hỗ trợ điều trị lao

###### :eight_spoked_asterisk: Xử lý yêu cầu

:white_check_mark: **Thay đổi cấu trúc dữ liệu**

Bi cập nhật cấu trúc:
- Thêm bảng chuyenvienlao tương tự các thông tin như bảng chuyenvien (Ghi nhận riêng các phiếu chuyển viện lao)

CREATE TABLE current.chuyenvienlao (
  mabn VARCHAR(20),
  maba VARCHAR(20),
  madv VARCHAR(20),
  maphong VARCHAR(20),
  noitru NUMERIC(1,0),
  maicd VARCHAR(20),
  kqcdoan VARCHAR,
  ngaycv TIMESTAMP WITHOUT TIME ZONE,
  mabv VARCHAR(20),
  lydo VARCHAR(500),
  phuongtien VARCHAR(100),
  manvc VARCHAR(20),
  dauhieuls VARCHAR(500),
  tinhtrang VARCHAR(500),
  manv VARCHAR(20),
  taikhoan VARCHAR(20),
  tenmay VARCHAR(20),
  xoa NUMERIC(1,0),
  ngayxoa TIMESTAMP WITHOUT TIME ZONE,
  thangkt VARCHAR(2),
  namkt VARCHAR(4),
  makb VARCHAR(20),
  sogiuong VARCHAR(20),
  xetnghiem VARCHAR(1000),
  thuoc VARCHAR(1000),
  maicdp VARCHAR(500),
  kqcdoanp VARCHAR,
  noigioithieu NUMERIC(1,0),
  socv VARCHAR(20),
  malydocv VARCHAR(25),
  lydoct NUMERIC(1,0) DEFAULT 0,
  huongdt VARCHAR(1000),
  htchuyen NUMERIC(1,0) DEFAULT 0,
  kqdieutri NUMERIC(1,0) DEFAULT 0,
  tuyencmkt NUMERIC(1,0),
  dudk NUMERIC(1,0) DEFAULT 0,
  chuyenvien NUMERIC(2,0)
) 
WITH (oids = false);
  
:white_check_mark: **Xử lý**
+ Module Prescription, Treatment:
 - Bổ sung chức năng lập phiếu chuyển viện lao ghi nhận vào bảng chuyenvienlao (chuyenvienlao.socv lấy max tăng dần khi lập mới)
 - Các trường và thông tin đầu vào tương tư như phiếu chuyển viện thông thường
  


