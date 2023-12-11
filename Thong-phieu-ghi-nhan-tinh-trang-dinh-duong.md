<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: FORM PHIẾU GHI NHẬP TÌNH TRẠNG DINH DƯỠNG, BÁO CÁO

</div>

###### :eight_spoked_asterisk: Người lập: [**LÊ QUỐC THỐNG**](https://github.com/lequocthong29)


###### :eight_spoked_asterisk: Ngày lập: **06/12/2023**

###### :eight_spoked_asterisk: Ngày hoàn thành dự kiến: **8/12/2023**

###### :eight_spoked_asterisk: Khách hàng: **Bệnh Viện Nhi Đồng**

###### :eight_spoked_asterisk: Yêu cầu phát sinh

- Mô tả cấu trúc và thực hiện phiếu ghi nhận tình trạng dinh dưỡng, báo cáo (DLL).

###### :eight_spoked_asterisk: Xử lý yêu cầu

:white_check_mark: **Thay đổi cấu trúc dữ liệu**

- Thêm bảng `current.tinhtrangdinhduong`: quản lý thông tin chỉ số dinh dưỡng.
- SQLScript: 

```
      CREATE TABLE current.tinhtrangdinhduong (
      stt NUMERIC NOT NULL,
      cannangrv NUMERIC(5,0),
      cannang_dg NUMERIC(1,0),
      sutcan1thang_dg NUMERIC(1,0),
      luongan1tuan_dg NUMERIC(1,0),
      duongnuoian_khct NUMERIC(1,0),
      hoichuandd_khct NUMERIC(1,0),
      taidanhgia_khct NUMERIC(1,0),
      ketluan NUMERIC(1,0),
      ngaylap TIMESTAMP(0) WITHOUT TIME ZONE,
      mabn VARCHAR(20),
      maba VARCHAR(20),
      makb VARCHAR(20),
      dalap NUMERIC(1,0),
      CONSTRAINT tinhtrangdinhduong_pkey PRIMARY KEY(stt)
    ) 
    WITH (oids = false);
    
    COMMENT ON COLUMN current.tinhtrangdinhduong.cannang_dg
    IS '1: > -1SD
    2: -1 SD đến > -2SD
    3: ≤ -2 SD';
    
    COMMENT ON COLUMN current.tinhtrangdinhduong.sutcan1thang_dg
    IS '1: Không sụt cân
    2: Tăng cân < 50% so với chuẩn ở trẻ < 2 tuổi
    3: Tăng cân < 25% so với chuẩn ở trẻ < 2 tuổi
    4: Sụt cân 7.5% trọng lượng ở trẻ ≥ 2 tuổi
    5: Sụt cân 10% trọng lượng ở trẻ ≥ 2 tuổi';
    
    COMMENT ON COLUMN current.tinhtrangdinhduong.luongan1tuan_dg
    IS '1: Không giảm hoặc giảm nhẹ
    2: Giảm ≥ 50% trong tuần qua
    3: Giảm ≥ 75% trong tuần qua';
    
    COMMENT ON COLUMN current.tinhtrangdinhduong.duongnuoian_khct
    IS '1: Đường miệng
    2: Ống thông
    3: Tĩnh mạch';
    
    COMMENT ON COLUMN current.tinhtrangdinhduong.hoichuandd_khct
    IS '1: có
    2: không';
    
    COMMENT ON COLUMN current.tinhtrangdinhduong.taidanhgia_khct
    IS '1: Sau 7 ngày (ở bệnh nhi không suy dinh dưỡng)
    2: Sau 3 ngày (ở bệnh nhi suy dinh dưỡng)';
    
    COMMENT ON COLUMN current.tinhtrangdinhduong.ketluan
    IS '1: Không SDD
    2: Suy dinh dưỡng';
    
    ALTER TABLE current.tinhtrangdinhduong
      OWNER TO postgres;
```


:white_check_mark: **Hướng dẫn sử dụng dll [**DH.TinhTrangDinhDuong.dll**](https://github.com/dh-hos/oLibraries/blob/main/DH.TinhTrangDinhDuong.dll)**
- **Check phiếu tính trạng dinh dưỡng**
  * Kiểm tra trước khi khám phiếu dinh dưỡng đã lậy chưa.
  TinhTrangDinhDuong TTDD = new TinhTrangDinhDuong(conn, mabn, maba, makb);
  
  Boolean CHECK = TTDD.CHECKPHIEU();
  
  - Nếu CHECK = **true** => phiếu đã lập (dữ liệu bảng current.tinhtrangdinhduong đã có).
  - Nếu CHECK = **false** => phiếu chưa được lập(dữ liệu bảng current.tinhtrangdinhduong chưa phát sinh) - mở form cho người dùng nhập phiếu.
    + conn : connections.
    + mabn \<string\> : mã bệnh nhân.   
    + maba \<string\> : mã bệnh án. 
    + makb \<string\> : mã khám bệnh.
    
- **Phiếu tình trạng dinh dưỡng**

  FrmTinhTrangDinhDuong(ngaylv, conn, mabn, maba, makb);
  + ngaylv \<DateTime\> : ngày làm việc.  
  + conn : connections.
  + mabn \<string\> : mã bệnh nhân.   
  + maba \<string\> : mã bệnh án. 
  + makb \<string\> : mã khám bệnh.
- **Báo cáo**
    
  FrmBCTinhTrangDinhDuong(conn, thangkt, namkt);
  + conn : connections.
  + thangkt \<string\> : tháng làm việc.    
  + namkt \<string\> : năm làm việc.

  
