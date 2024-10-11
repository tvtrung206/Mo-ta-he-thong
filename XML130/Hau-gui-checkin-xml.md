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

```/// <summary>
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

- Chức năng: Thực hiện đánh dấu Thực hiện checkIn khi có cận lâm sàng đầu tiên (Thực hiện tại Prescription, Treatment). [^2024-10-11] ***Bổ sung thêm chức năng ghi nhận checkIn cận lâm sàng khi thực hiện `Lưu khám bệnh` với điều kiện xử lý khác lập hồ sơ Bệnh án (Nội trú, Ngoại trú), để đảm bảo những hồ sơ chuyển viện, hoặc chỉ có thuốc vẫn checkIn được CLS công khám.*** 

```/// <summary>
        /// Thực hiện đánh dấu Thực hiện checkIn khi có cận lâm sàng đầu tiên,
        ///     Gọi hàm khi thực hiện mỗi lưu chỉ định cls thành công (hàm này sẽ xử lý nếu chưa checkin sẽ thực hiện, ngược lại bỏ qua)
        /// </summary>
        /// <param name="macls">Mã cận lâm sàng đầu tiên trong lần chỉ định</param>
        /// <returns></returns>
        public bool MarkCheckInCanlamsang(string macls)
```

- Chức năng: Thực hiện đánh dấu Thực hiện checkIn khi có thuốc, vtyt đầu tiên (Thực hiện tại Prescription, Treatment):

```/// <summary>
        /// Thực hiện đánh dấu Thực hiện checkIn khi có thuốc, vtyt đầu tiên
        ///     => Gọi hàm mỗi khi lưu toa thuốc thành công (hàm này sẽ xử lý nếu chưa checkin sẽ thực hiện, ngược lại bỏ qua)
        /// </summary>
        /// <param name="mahhThuoc">Mã hàng hóa thuộc kho THUỐC chỉ định đầu tiên</param>
        /// <param name="mahhVTYT">Mã hàng hóa thuộc kho VTYT chỉ định đầu tiên</param>
        /// <returns></returns>
        public bool MarkCheckInThuocVTYT(string mahhThuoc, string mahhVTYT)
```

- Chức năng: Thực hiện đánh dấu khi bệnh nhân ra viện đối với bệnh án, bệnh nhân ngoại trú in phiếu (Thực hiện tại Prescription, Treatment, Printer):

```/// <summary>
        /// Thực hiện đánh dấu khi bệnh nhân ra viện đối với bệnh án, bệnh nhân ngoại trú in phiếu
        ///     => Gọi hàm khi Lưu ra viện đối với bệnh án, hoặc In phiếu đối với ngoại trú, hoặc Lập toa xuất viện ngoại trú đối với bệnh án
        /// </summary>
        /// <returns></returns>
        public bool MarkRavien()
```

- [^2024-10-08] Chức năng: Thực hiện đánh dấu Thực hiện checkIn khi thực hiện `Lưu khám bệnh` (Thực hiện tại Prescription), Mã cận lâm sàng sẽ lấy công khám đầu tiên để đánh dấu. **_Xử lý trường hợp không có chỉ định CLS thì không có gửi checkIn được, vd: trường hợp bệnh nhân chuyển viện..._**

```/// <summary>
        /// Thực hiện đánh dấu Thực hiện checkIn khi có cận lâm sàng đầu tiên,
        ///     Gọi hàm khi thực hiện mỗi lưu chỉ định cls thành công (hàm này sẽ xử lý nếu chưa checkin sẽ thực hiện, ngược lại bỏ qua)
        /// </summary>
        /// <param name="macls">Mã cận lâm sàng đầu tiên trong lần chỉ định</param>
        /// <returns></returns>
        public bool MarkCheckInCanlamsang(string macls)
```

###### :eight_spoked_asterisk: Module Services gửi hồ sơ [^2024-10-11]

- Ngày giờ hệ thống: **_Ngày_** để lấy thông tin hồ sơ dựa vào tham số **_`ngaylv`_**, **_Giờ_** sẽ lấy theo `giờ hệ thống` (máy chủ cài PostgreSQL).
- Gửi lên cổng BHXH điều kiện hồ sơ phải có thông tin `mã thẻ`

1. Loại gửi CheckIn dựa vào `xml130.psxml.ngay_checkin` lấy theo ngày bằng với Ngày giờ hệ thống, kèm điều kiện trạng thái gửi (`checkin_cls<=0 và macls<>''`, `checkin_thuoc<=0 và mahh_thuoc<>''`, `checkin_vtyt<=0 và mahh_vtyt<>''`), **_các loại mã này phải được cấu hình mã dùng chung theo qui định_**.
2. Loại gửi Hồ sơ xml4750 dựa vào `xml130.psxml.ngay_ttoan` phải nhỏ hơn ngày giờ hệ thống trừ đi số phút lùi theo tham số `congdulieuBHXH.thoigian` và trạng thái chưa gửi `daguibhxh<=0`

- Xử lý hồ sơ gửi gặp lỗi: nếu xảy ra lỗi trong quá trình gửi hồ sơ, sẽ ghi nhận tại số lần gửi gặp lỗi trong `xml130.psxml.checkin_error`, `xml130.psxml.hoso_error`, đồng thời ghi nhận thông tin lỗi lần cuối tại `xml130.psxml.checkin_error_message`, `xml130.psxml.hoso_error_message`.
- **_Trường hợp một hồ sơ gặp lỗi khi gửi lớn hơn 20 lần, sẽ bỏ qua, không xử lý gửi hồ sơ này nữa._**

[^2024-10-08]: Bổ sung chức năng ngày 2024-10-08
[^2024-10-11]: Bổ sung chức năng ngày 2024-10-11
