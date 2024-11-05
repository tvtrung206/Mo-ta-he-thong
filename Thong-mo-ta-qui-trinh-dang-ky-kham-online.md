<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: QUI TRÌNH ĐĂNG KÝ KHÁM ONLINE

</div>

###### :eight_spoked_asterisk: Người lập: [**LÊ QUỐC THỐNG**](https://github.com/lequocthong29)

###### :eight_spoked_asterisk: Ngày lập: **05/11/2024**

###### :eight_spoked_asterisk: Qui trình xử lý
1. Đăng ký khám online thông qua API: [Mô tả API](https://github.com/dh-hos/Mo-ta-he-thong/tree/main/dang-ky-online).
  
2. Khi khách hàng đăng ký khám online thông qua API, dữ liệu sẽ được lưu vào bảng `datlichkham.dangkykol` :
    + date (DATE) : Ngày khám.
    + timeslot VARCHAR(50) : Thời gian khám sự kiện.
    + fee VARCHAR(20) : Phí khám của lịch khám này.
    + providerid VARCHAR(10) : Mã bác sỹ.
    + specialityid VARCHAR(10) : Mã khoa.
    + roomid VARCHAR(10) : Mã phòng.
    + examtype VARCHAR(10) : Mã dịch vụ.
    + patienttype VARCHAR(10) : Mã đối tượng.
    + hisid VARCHAR(10) : Mã bệnh nhân.
    + hiqrcode VARCHAR(255) : Mã thẻ BHYT.
    + orderid VARCHAR(20) : Mã đơn hàng.
    + feeamount NUMERIC(12,0) : Tổng chi phí.
    + servicefeeamount NUMERIC(12,0) : Phí dịch vụ.
    + status VARCHAR(255) : Trạng thái thanh toán.
    + mgnthisid VARCHAR(12) : Mã khám bệnh.
    + number NUMERIC(10,0) : Số thứ tự.
    + insurancenumber VARCHAR(15) : Mã BHYT.
    + expireddate DATE : Ngày hết hạn BHYT.
    + insurancestatus VARCHAR(10) : Trạng thái hợp lệ của BHYT.
    + hospitalId VARCHAR(10) : Nơi khám chữa bệnh ban đầu.
    + detailUrl TEXT : Link chi tiết (hình ảnh/ giấy chuyển tuyến)
    + fullname VARCHAR(100) : Họ tên người quan hệ.
    + phone VARCHAR(100) : SĐT.
    + CMND VARCHAR(100) : Chứng minh nhân dân.
    + address VARCHAR(500) : Địa chỉ.
    + relativeType VARCHAR(100) : Mã mối quan hệ.
    + relativeName VARCHAR(100) : Tên mối quan hệ.
    
3. Sau khi dữ liệu được phát sinh vào bảng `datlichkham.dangkykol`, moduel Register sẻ hiển thị danh sách bệnh nhân đăng ký khám theo ngày khám (datlichkham.dangkykol.date) và mã đơn vị (datlichkham.dangkykol.specialityid).
     ![](https://i.imgur.com/rp3kDKS.png)
3. Để tiếp nhận bệnh nhân, click vào nút đăng ký khám bệnh.
     ![](https://i.imgur.com/Jyy3mO8.gif)

 
