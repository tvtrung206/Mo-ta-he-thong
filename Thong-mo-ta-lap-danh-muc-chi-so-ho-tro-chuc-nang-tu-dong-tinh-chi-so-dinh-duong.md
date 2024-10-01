<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: MÔ TẢ LẬP CÁC DANH MỤC CHỈ SỐ HỖ TRỢ TÍNH CHỈNH SỐ DINH DƯỠNG TỰ ĐỘNG

</div>

###### :eight_spoked_asterisk: Người lập: [**LÊ QUỐC THỐNG**](https://github.com/lequocthong29)


###### :eight_spoked_asterisk: Ngày lập: **28/06/2024**

###### :eight_spoked_asterisk: Ngày hoàn thành dự kiến: **30/06/2024**

###### :eight_spoked_asterisk: Khách hàng: **Bệnh Viện Nhi Đồng**

###### :eight_spoked_asterisk: Yêu cầu phát sinh

- Thực hiện chức năng tính giá trị dinh dưỡng dựa vào dữ liệu có sẳn

###### :eight_spoked_asterisk: Lập các danh mục chỉ số.
1. Danh mục cân nặng theo độ tuổi
```csharp
      CREATE TABLE current.dmcannangtheotuoi (
        thangtuoi NUMERIC(10,0),
        chiso_l NUMERIC(10,5),
        chiso_m NUMERIC(10,5),
        chiso_s NUMERIC(10,5),
        gioitinh NUMERIC(1,0)
      ) 
      WITH (oids = false);
      
      COMMENT ON COLUMN current.dmcannangtheotuoi.gioitinh
      IS '0: nam , 1: nữ';
```

2. Danh mục cân nặng theo chiều cao
```csharp
      CREATE TABLE current.dmcannangtheochieucao (
        chieucao NUMERIC(10,1),
        chiso_l NUMERIC(10,5),
        chiso_m NUMERIC(10,5),
        chiso_s NUMERIC(10,5),
        gioitinh NUMERIC(1,0)
      ) 
      WITH (oids = false);
      
      COMMENT ON COLUMN current.dmcannangtheochieucao.gioitinh
      IS '0: nam , 1: nữ';
```

3. Danh mục BMI theo độ tuổi
```csharp
      CREATE TABLE current.dmbmitheotuoi (
        thangtuoi NUMERIC(10),
        chiso_l NUMERIC(10,5),
        chiso_m NUMERIC(10,5),
        chiso_s NUMERIC(10,5),
        gioitinh NUMERIC(1,0)
      ) 
      WITH (oids = false);
      
      COMMENT ON COLUMN current.dmbmitheotuoi.gioitinh
      IS '0: nam , 1: nữ';
```

4. Danh mục chiều cao theo độ tuổi
```csharp
      CREATE TABLE current.dmchieucaotheotuoi (
        thangtuoi NUMERIC(10),
        chiso_l NUMERIC(10,5),
        chiso_m NUMERIC(10,5),
        chiso_s NUMERIC(10,5),
        gioitinh NUMERIC(1,0)
      ) 
      WITH (oids = false);
      
      COMMENT ON COLUMN current.dmchieucaotheotuoi.gioitinh
      IS '0: nam , 1: nữ';
```
