<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: FORM GIÁM ĐỊNH Y KHOA

</div>

###### :eight_spoked_asterisk: Người lập: [**LÊ QUỐC THỐNG**](https://github.com/lequocthong29)


###### :eight_spoked_asterisk: Ngày lập: **04/12/2023**

###### :eight_spoked_asterisk: Ngày hoàn thành dự kiến: **09/12/2023**

###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**

###### :eight_spoked_asterisk: Yêu cầu phát sinh

- Mô tả cấu trúc và thực hiện phiếu ghi nhận tình trạng dinh dưỡng, báo cáo (DLL).

###### :eight_spoked_asterisk: Xử lý yêu cầu

:white_check_mark: **Thay đổi cấu trúc dữ liệu**

:white_check_mark: **Hướng dẫn sử dụng dll [**DH.PSGiamDinhYKhoa.dll**](https://github.com/dh-hos/oLibraries/blob/main/DH.PSGiamDinhYKhoa.dll)**
    
- **Form giám định y khoa**

  FrmPsGiayKhamYKhoa(conn, mabn, maba, makb,noitru );
  + conn : connections.
  + mabn \<string\> : mã bệnh nhân.   
  + maba \<string\> : mã bệnh án. 
  + makb \<string\> : mã khám bệnh.
  + noitru \<numeric\> : nội trú.
  
