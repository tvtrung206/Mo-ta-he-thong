<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: THỰC HIỆN QUẢN LÝ BỆNH ÁN NGÀY

</div>

:white_check_mark: **Người lập: NGUYỄN TRIỀU VƯƠNG**

:white_check_mark: **Ngày lập: 15/12/2023**

:white_check_mark: **Ngày dự hoàn thành: 22/12/2023**

:white_check_mark: **Khách hàng: Tất cả**

:white_check_mark: **Xử lý yêu cầu**

    - Thực hiện quản lý bệnh án ngày

:white_check_mark: **Thay đổi cấu trúc dữ liệu**

- Thêm cột bangay Numeric(1,0) `current.bnnoitru.bangay`: cột bệnh án ngày
- Giá trị: 
     - 0: bệnh án bình thường
     - 1: bệnh án ngày
- SQLScript: 

```
  ALTER TABLE current.bnnoitru
  ADD COLUMN bangay NUMERIC(1,0) DEFAULT 0;

  COMMENT ON COLUMN current.bnnoitru.bangay
  IS '0: bệnh án bình thường
  1: bệnh án ngày';
```


:white_check_mark: **Xử lý**
- **Prescription**
    - Form nhập viện: thêm tùy chọn bệnh án ngày hay bệnh bình thường
      ![image](https://github.com/dh-hos/Mo-ta-he-thong/assets/32563776/cd92cedd-7dc6-4604-9ef9-a33b642c568d)

- **Treatment**
   - Trang bìa bệnh án: có nhãn "NỘI TRÚ BAN NGÀY" (nếu người dùng chọn hiển thị cho bệnh án ngày)
     ![image](https://github.com/dh-hos/Mo-ta-he-thong/assets/32563776/e8c05774-c003-4948-8b88-6ad8dcb31d39)

   - Thay đổi màu sắc đối với bệnh nhân có bệnh án ngày
   - Điều chỉnh các mẫu báo cáo có tùy chọn xem bệnh án ngày hay bệnh án bình thường:
       - Số xuất viện
       - Sổ lưu trữ
       - Sổ điều trị
   - Xuất dll --> reports sử dụng
- **Report**
   - Cập nhật dll mới 
  

