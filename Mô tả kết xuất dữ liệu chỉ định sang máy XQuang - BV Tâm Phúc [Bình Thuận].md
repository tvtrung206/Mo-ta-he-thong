<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>
<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: MÔ TẢ KẾT XUẤT DỮ LIỆU CHỈ ĐỊNH SANG MÁY XQUANG
</div>

###### :eight_spoked_asterisk: Người lập: [**vinh-dh**](https://github.com/vinh-dh)
###### :eight_spoked_asterisk: Ngày lập: **20/06/2024**
###### :eight_spoked_asterisk: Khách hàng: ****BỆNH VIỆN ÐA KHOA TÂM PHÚC - `60152`****
###### :eight_spoked_asterisk: Yêu cầu phát sinh

- Thực hiện theo yêu cầu chi tiết tại: [Yêu cầu - Mô tả thực hiện hợp đồng kết nối máy X Quang.  #412](https://github.com/dh-hos/To_Lap_Trinh/issues/412)

###### :eight_spoked_asterisk: Xử lý yêu cầu:
:white_check_mark: **Quy trình áp dụng:**

:blue_book: Cấu hình:
 - Tham số `ip_server_pacs`: thư mục chứa tập tin chỉ định XQuang từ DHG.Hospital để máy Xquang sử dụng. Ví dụ: `\\192.168.1.5\xquang`. **Lưu ý**: share thư mục này có quyền ghi/xóa, sau khi DHG.Hospital ghi file chỉ định, máy Xquang đọc xong tập tin sẽ xóa.

:blue_book: DHG.Hospital Diagnose: 
- Tại form danh sách thực hiện bệnh nhân XQuang, bổ sung nút `[Gửi PACS]`: cho phép nhân viên gửi thông tin chỉ định Xquang sang máy Xquang. **Lưu ý**: Chỉ áp dụng đối với cận lâm sàng có `maloai` là `XQ/XQKTS`.

![image](https://github.com/dh-hos/Mo-ta-he-thong/assets/112069710/29d549da-904e-45b9-bfeb-fb8ba36f3c68)

- Quá trình gửi PACS cho mỗi XQuang được thực hiện:
1. Hệ thống sẽ sử dụng tham số `ha.idpacs` để lưu giá trị `ID PACS` mới nhất của mỗi lần gửi PACS. Độ dài giá trị tham số này là 8 ký tự.
2. Tạo ID PACS cho mỗi lần gửi: `idpacs = ha.idpacs + 1`.
3. Tạo tập tin chỉ định theo quy tắc: `"idpacs.txt"`. Ví dụ: `00012345.txt`, trong đó `idpacs = 00012345`. Tập tin được lưu vào `\\192.168.1.5\xquang\00012345.txt` sau mỗi lần gửi.
4. Nội dung tập tin theo quy tắc: `idpacs|hotenbenhnhan|ngaysinh|gioitinh|khoachidinh|tencanlamsang`<br/>
Trong đó:<br/>
⇒ `idpacs`: ID PACS được sinh ra từ bước 2.<br/>
⇒ `hotenbenhnhan`: Họ và tên bệnh nhân.<br/>
⇒ `ngaysinh`: Ngày sinh bệnh nhân. Kiểu chuỗi theo cú pháp: `YYYYMMDD`.<br/>
⇒ `gioitinh`: Giới tính. Giá trị: M (nam), ngược lại F. [^2024-06-23]<br/>
⇒ `khoachidinh`: Tên khoa chỉ định Xquang.<br/>
⇒ `tencanlamsang`: Tên cận lâm sàng Xquang.<br/>
5. Sau khi gửi thành công: cập nhật `chidinhcls.idpacs = idpacs` và tham số `ha.idpacs = idpacs`.
6. Trường hợp gửi lại PACS (đã gửi và phát sinh idpacs trước đó): `idpasc = chidinhcls.idpacs` và thực hiện tiếp tục bắt đầu từ bước 3.
7. Máy Xquang sau khi nhận và đọc thành công thì xóa tập tin đã đọc.

[^2024-06-23]: Thay đổi ngày 23/06/2024: Bổ sung mô tả `gioitinh`.
