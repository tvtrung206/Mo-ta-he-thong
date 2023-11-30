<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: QUẢN LÝ LOẠI CHI PHÍ NỘI BỘ

</div>

###### :eight_spoked_asterisk: Người lập: [**ÔNG TRIỆU HẬU**](https://github.com/ongtrieuhau)


###### :eight_spoked_asterisk: Ngày lập: **20/11/2023**

###### :eight_spoked_asterisk: Ngày hoàn thành dự kiến: **21/11/2023**

###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**

###### :eight_spoked_asterisk: Yêu cầu phát sinh

- Quản lý các loại chi phí nội bộ (gửi mẫu xét nghiệm,...) theo từng phiếu thu

###### :eight_spoked_asterisk: Xử lý yêu cầu

:white_check_mark: **Thay đổi cấu trúc dữ liệu**

- Thêm bảng `current.dmloaicpnoibo`: quản lý danh mục loại chi phí thuộc nội bộ.
- Thêm `dmloaicpnoibo` vào bảng `current.dmcls`: phân loại các chi phí nội bộ theo danh mục cận lâm sàng.
- SQLScript: 

```
ALTER TABLE current.dmcls ADD COLUMN loaicpnoibo VARCHAR(20);
CREATE TABLE current.dmloaicpnoibo (
  loaicpnoibo VARCHAR(20),
  diengiai VARCHAR(255)
) 
WITH (oids = true);

ALTER TABLE current.dmloaicpnoibo
  OWNER TO postgres;
```


:white_check_mark: **Module Admin**

- Thêm chức năng quản lý danh mục `current.dmloaicpnoibo`
- Thêm chức năng cập nhật thay đổi loại chi phí nội bộ `loaicpnoibo` trong bảng `current.dmcls`

:white_check_mark: **Module Fees**

- Thêm bảng kê chi tiết chi phí nội bộ theo phân loại trên
- Phụ sản yêu cầu mẫu tại đây: [3748-ĐN-BVPS.pdf](File-ho-tro/3748-%C4%90N-BVPS.pdf)
