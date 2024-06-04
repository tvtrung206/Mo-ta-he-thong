<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: THỰC HIỆN CHECKIN, GỬI HỒ SƠ XML4750

</div>

###### :eight_spoked_asterisk: Người lập: [**ÔNG TRIỆU HẬU**](https://github.com/ongtrieuhau)

###### :eight_spoked_asterisk: Ngày lập: **06/04/2024**

###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**

###### :eight_spoked_asterisk: Yêu cầu phát sinh

- Thực hiện theo [Mô tả 130 - 4750](https://github.com/dh-hos/Mo-ta-he-thong/tree/main/XML130)
- Gửi xml CheckIn theo qui 4750
- Gửi xml HoSo theo qui 4750

###### :eight_spoked_asterisk: Thực hiện yêu cầu

- Sử dụng dll: `DH.XML4750.dll` để thực hiện các thao tác

- Khởi tạo `DH.XML4750.HOSO`:

```     /// <summary>
        /// Khởi tạo HOSO theo đối tượng OTH.Entity.HosBHXH.EGiamDinh.HoSoInfo
        /// </summary>
        /// <param name="hoSoInfo"></param>
        public HOSO(OTH.Entity.HosBHXH.EGiamDinh.HoSoInfo hoSoInfo)
        /// <summary>
        /// Khởi tạo hồ sơ theo thông tin chi tiết
        /// </summary>
        /// <param name="mabn">Mã bệnh nhân</param>
        /// <param name="makb">Mã khám bệnh</param>
        /// <param name="maba">Mã bệnh án</param>
        /// <param name="mabattconbh2">Mã bệnh án thông tin con, hoặc BHYT thứ 2</param>
        /// <param name="loaiHoSoKCB">Loại hồ sơ KCB:  NGOAI_TRU, NGOAI_TRU_XUAT_VIEN, BA_NGOAI_TRU, BA_NOI_TRU, BA_NOI_TRU_THE_BHYT2, BA_NOI_TRU_TTCON </param>
        public HOSO(string mabn, string makb, string maba, string mabattconbh2, OTH.Entity.Enum.BHXH.v_LoaiHoSoKCB loaiHoSoKCB) 
```

- Chức năng: Thực hiện đánh dấu Thực hiện checkIn khi có cận lâm sàng đầu tiên (Thực hiện tại Prescription, Treatment):

```     /// <summary>
        /// Thực hiện đánh dấu Thực hiện checkIn khi có cận lâm sàng đầu tiên,
        ///     Gọi hàm khi thực hiện mỗi lưu chỉ định cls thành công (hàm này sẽ xử lý nếu chưa checkin sẽ thực hiện, ngược lại bỏ qua)
        /// </summary>
        /// <param name="macls">Mã cận lâm sàng đầu tiên trong lần chỉ định</param>
        /// <returns></returns>
        public bool MarkCheckInCanlamsang(string macls)
```

- Chức năng: Thực hiện đánh dấu Thực hiện checkIn khi có thuốc, vtyt đầu tiên (Thực hiện tại Prescription, Treatment):

```     /// <summary>
        /// Thực hiện đánh dấu Thực hiện checkIn khi có thuốc, vtyt đầu tiên
        ///     => Gọi hàm mỗi khi lưu toa thuốc thành công (hàm này sẽ xử lý nếu chưa checkin sẽ thực hiện, ngược lại bỏ qua)
        /// </summary>
        /// <param name="mahhThuoc">Mã hàng hóa thuộc kho THUỐC chỉ định đầu tiên</param>
        /// <param name="mahhVTYT">Mã hàng hóa thuộc kho VTYT chỉ định đầu tiên</param>
        /// <returns></returns>
        public bool MarkCheckInThuocVTYT(string mahhThuoc, string mahhVTYT)
```

- Chức năng: Thực hiện đánh dấu khi bệnh nhân ra viện đối với bệnh án, bệnh nhân ngoại trú in phiếu (Thực hiện tại Prescription, Treatment, Printer):

```     /// <summary>
        /// Thực hiện đánh dấu khi bệnh nhân ra viện đối với bệnh án, bệnh nhân ngoại trú in phiếu
        ///     => Gọi hàm khi Lưu ra viện đối với bệnh án, hoặc In phiếu đối với ngoại trú, hoặc Lập toa xuất viện ngoại trú đối với bệnh án
        /// </summary>
        /// <returns></returns>
        public bool MarkRavien()
```