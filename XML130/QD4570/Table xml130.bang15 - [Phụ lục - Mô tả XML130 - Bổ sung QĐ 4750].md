<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>PHIẾU MÔ TẢ THAY ĐỔI HỆ THỐNG</h1>  
</div>
<div align="center">

#### Phụ lục: CẤU TRÚC DỮ LIỆU LƯU TRỮ 16 TABLE – CẬP NHẬT THEO QĐ4750
**Table xml130.bang15: Chỉ tiêu thông tin quản lý điều trị bệnh lao.**

</div>

###### :eight_spoked_asterisk: Người lập: [**Nguyễn Viết Vinh**](https://github.com/vinh-dh)
###### :eight_spoked_asterisk: Ngày lập: **27/02/2023**
###### :eight_spoked_asterisk: Ngày cập nhật: **09/06/2024**
###### :eight_spoked_asterisk: Khách hàng: **Tất cả khách hàng sử dụng DHG.Hospital**
###### :eight_spoked_asterisk: Yêu cầu phát sinh
###### :eight_spoked_asterisk: Xử lý yêu cầu

:white_check_mark: **Mô tả tổng thể từ: [Mô tả XML130 - Bổ sung QĐ 4750]()**

|TT QĐ 4750|Tên cột|Kiểu dữ liệu|Bắt buộc|Diễn giải|Index|Ghi chú|
|:-------:|-------|:-------:|:-------:|-------|:-------:|-------|
|1|ma_lk|VARCHAR(100)|X|Là mã đợt điều trị duy nhất (dùng để liên kết giữa Bảng chỉ tiêu tổng hợp khám bệnh, chữa bệnh (bảng XML 1) và các bảng còn lại ban hành kèm theo Quyết định này trong một lần khám bệnh, chữa bệnh (PRIMARY KEY)).|X||
|2|stt|NUMERIC(10)||Là số thứ tự tăng từ 1 đến hết trong một lần gửi dữ liệu.|||
|3|ma_bn|VARCHAR(100)|X|Là mã người bệnh theo quy định của cơ sở KBCB|||
|4|ho_ten|VARCHAR(255)||Là họ và tên của người bệnh.<br/>- **Lưu ý**: Trường hợp trẻ sau khi sinh ra được hưởng quyền lợi BHYT theo quy định của Luật BHYT nhưng chưa được cơ quan BHXH cấp thẻ BHYT do chưa làm thủ tục cấp giấy khai sinh thì cơ sở KBCB thực hiện ghi họ và tên của trẻ theo quy định tại điểm b khoản 1 Điều 10 [Thông tư số 30/2020/TT-BYT](https://vbpl.vn/TW/Pages/vbpq-toanvan.aspx?ItemID=147385) ngày 31 tháng 12 năm 2020 của Bộ trưởng Bộ Y tế quy định chi tiết và hướng dẫn biện pháp thi hành một số điều của [Nghị định số 146/2018/NĐ-CP](https://vanban.chinhphu.vn/?pageid=27160&docid=195119) ngày 17/10/2018 của Chính phủ quy định chi tiết và hướng dẫn biện pháp thi hành một số điều của Luật BHYT, cụ thể:<br/>+ Nếu trẻ sơ sinh có mẹ hoặc cha (bố): ghi theo họ và tên của mẹ hoặc của cha (bố);<br/>+ Nếu trẻ sơ sinh không có mẹ hoặc cha (bố) nhưng có người giám hộ: ghi theo họ và tên của người giám hộ;<br/>+ Nếu trẻ sơ sinh không có người nhận hoặc bỏ rơi tại cơ sở KBCB: ghi tên cơ sở KBCB nơi đang thực hiện việc điều trị cho trẻ.|||
|5|so_cccd|VARCHAR(15)||Ghi số căn cước công dân hoặc số chứng minh thư nhân dân hoặc số hộ chiếu của người bệnh.<br/>Trường hợp không có số căn cước công dân hoặc số chứng minh thư nhân dân hoặc số hộ chiếu thì sử dụng mã tài khoản định danh điện tử.|||
|6|phanloai_lao_vitri|NUMERIC(1,0)|X|Ghi mã phân loại Bệnh nhân lao theo vị trí giải phẫu<br/>  + Mã "1": Lao phổi <br/>  + Mã "2": Lao ngoài phổi|||
|7|phanloai_lao_ts|NUMERIC(1,0)|X|Ghi mã phân loại Bệnh nhân lao theo tiền sử điều trị<br/> + Mã "1": Lao mới <br/> + Mã "2": Tái phát<br/> + Mã "3": Thất bại<br/> + Mã "4": Điều trị lại sau bỏ trị<br/> + Mã "5": Điều trị lại khác<br/> + Mã "6": Không rõ tiền sử điều trị|||
|8|phanloai_lao_hiv|NUMERIC(1,0)|X|Ghi mã phân loại bệnh nhân lao theo tình trạng nhiễm HIV<br/>  - Mã "1": Lao/HIV (+)<br/>  - Mã "2": Lao/HIV (-)<br/>  - Mã "3": BN lao không rõ tình trạng HIV|||
|9|phanloai_lao_vk|NUMERIC(1,0)|X|Ghi mã phân loại Bệnh nhân lao theo bằng chứng vi khuẩn học<br/> + Mã "1": Lao có bằng chứng vi khuẩn học<br/> + Mã "2": Lao không có bằng chứng vi khuẩn học|||
|10|phanloai_lao_kt|NUMERIC(1,0)|X|Ghi mã phân loại BN lao theo tình trạng kháng thuốc<br/>  - Mã "1": Lao kháng đơn thuốc<br/>  - Mã "2": Lao kháng nhiều thuốc<br/>  - Mã "3": Lao đa kháng thuốc<br/>  - Mã "4": Lao kháng Rifampicin-Lao kháng R <br/> - Mã "5": Lao tiền siêu kháng<br/> - Mã "6": Lao siêu kháng thuốc|||
|11|loai_dtri_lao|NUMERIC(1,0)|X| Ghi mã loại điều trị lao, trong đó:<br/> - Mã "0": Không điều trị lao<br/> - Mã "1": Điều trị lao tiềm ẩn<br/> - Mã "2": Điều trị lao nhạy cảm thuốc<br/> - Mã "3": Điều trị lao kháng thuốc|||
|12|ngaybd_dtri_lao|VARCHAR(8)|X|Ghi thời điểm bắt đầu điều trị bệnh lao hoặc lao tiềm ẩn tại cơ sở KBCB, định dạng yyyymmdd.|||
|13|phacdo_dtri_lao|NUMERIC(2,0)|X|Ghi mã phác đồ điều trị:<br/> 1. Lao nhạy cảm thuốc:<br/>  + Mã "1": Phác đồ A1: 2HRZE/4RHE (phác đồ 06 tháng – điều trị lao cho người lớn)<br/>  + Mã "2": Phác đồ A2: 2HRZE/4RH (phác đồ 06 tháng – điều trị lao cho trẻ em )<br/>  + Mã "3": Phác đồ A1a: 2HPMZ/2HPM (phác đồ 4 tháng – điều trị lao cho người từ 12 tuổi trở lên) <br/>  + Mã "4": Phác đồ A2a: 2HRZE/2RH (phác đồ 4 tháng – điều trị lao cho trẻ em từ 3 tháng đến 16 tuổi) <br/>  + Mã "5": Phác đồ B1: 2HRZE/10RHE (phác đồ 12 tháng - điều trị lao cho người lớn)<br/>  + Mã "6": Phác đồ B2: 2HRZE/10RH (phác đồ 12 tháng – điều trị lao cho trẻ em)<br/>  + Mã "7": Phác đồ B2a: 6HRZEto (phác đồ 6 tháng – điều trị lao hệ thần kinh trung ương cho người từ 0 đến 19 tuổi)<br/> + Mã "8": Phác đồ cá thể <br/> 2. Lao Kháng thuốc<br/> + Mã "9": Phác đồ C1a: 4 Bdq[6]-Lfx(Mfx)-Pto-E-Z-Hh-Cfz / 5 Lfx-Cfz-Z-E (người lớn)<br/> + Mã "10": Phác đồ C1b: 4-6Bdq[6]-Lfx-Pto-E[2]-Z-Hh-Cfz / 5 Lfx-Cfz-Z (trẻ em)<br/> + Mã "11": Phác đồ C2a: 4-6 Bdq[6]- Lfx- Lzd [2]- E -Z-Hh- Cfz/ 5 Lfx/Mfx-Cfz-Z-E (người lớn)<br/>+ Mã "12": Phác đồ C2b: 4-6Bdq[6]-Lfx-Lzd[2]-E[2]-Z-Hh-Cfz / 5 Lfx-Cfz-Z (trẻ em)<br/>+ Mã "13": Phác đồ C3: 9-11 Bdq[6]-Lfx-Lzd-Cfz-(Z)<br/> + Mã "14": Phác đồ BPaL-M: 6 Bdq Pa Lzd Mfx<br/> + Mã "15": Phác đồ BPaL: 6-9 Bdq Pa Lzd<br/> + Mã "16": Phác đồ D1: 20 Bdq [6] Lfx Lzd Cfz + 1 thuốc nhóm C<br/> + Mã "17": Phác đồ D2: 20 Lfx Lzd Cfz Cs +1 thuốc nhóm C <br/> + Mã "18": Phác đồ E: Bdq Lzd Cfz Cs +1 thuốc nhóm C hoặc thành phần được xác định bởi hội đồng Lâm sàng<br/> + Mã "19": Phác đồ cá thể khác<br/> 3. Lao tiềm ẩn<br/> + Mã "20": Phác đồ 6H/9H <br/> + Mã "21": Phác đồ 3RH<br/> + Mã "22": Phác đồ 3HP<br/> + Mã "23": Phác đồ 1HP<br/> + Mã "24": Phác đồ 4R<br/> +Mã "25": Phác đồ 6L|||
|14|ngaykt_dtri_lao|VARCHAR(8)||Ghi thời điểm kết thúc điều trị bệnh lao hoặc lao tiềm ẩn tại cơ sở KBCB, định dạng yyyymmdd. <br/>Trường hợp chưa kết thúc điều trị thì để trống trường thông tin này.|||
|15|ket_qua_dtri_lao|NUMERIC(1,0)|X|Ghi mã đánh giá kết quả điều trị, trong đó:<br/> - Mã "1": Khỏi: người bệnh lao phổi có bằng chứng vi khuẩn học tại thời điểm bắt đầu điều trị, có kết quả xét nghiệm đờm trực tiếp hoặc nuôi cấy âm tính tháng cuối của quá trình điều trị và ít nhất 1 lần trước đó.<br/> - Mã "2":Hoàn thành điều trị: người bệnh lao hoàn thành liệu trình điều trị, không có bằng chứng thất bại, nhưng cũng không có xét nghiệm đờm trực tiếp hoặc nuôi cấy âm tính vào tháng cuối của quá trình điều trị và ít nhất 1 lần trước đó, bất kể không làm xét nghiệm hay không có kết quả xét nghiệm.<br/> - Mã "3":Thất bại: người bệnh lao có kết quả xét nghiệm đờm trực tiếp hoặc nuôi cấy dương tính từ tháng thứ 5 trở đi của quá trình điều trị.<br/> - Mã "4":Chết: người bệnh lao chết do bất cứ nguyên nhân gì trước hoặc trong quá trình điều trị lao.<br/> - Mã "5":Không theo dõi được (bỏ): người bệnh lao ngừng điều trị liên tục từ 2 tháng trở lên.<br/> - Mã "6":Không đánh giá: người bệnh lao không được đánh giá kết quả điều trị. Bao gồm các trường hợp chuyển tới đơn vị điều trị khác và không có phản hồi kết quả điều trị, cũng như các trường hợp đơn vị báo cáo không biết kết quả điều trị của bệnh nhân.|||
|16|ma_cskcb|VARCHAR(5)||Ghi mã cơ sở KBCB nơi người bệnh đến khám bệnh, điều trị do cơ quan có thẩm quyền cấp.|||
|17|ngaykd_hiv|VARCHAR(8)||Ghi thời điểm khẳng định HIV của người nhiễm HIV, định dạng yyyymmdd.<br/>Trường hợp điều trị phơi nhiễm thì để trống trường thông tin này.|||
|18|bddt_arv|VARCHAR(8)|X|Ghi thời điểm đầu tiên người bệnh nhận thuốc ARV trong chương trình chăm sóc và điều trị được ghi trong hồ sơ bệnh án của người bệnh; định dạng yyyymmdd.|||
|19|ngay_bat_dau_dt_ctx|VARCHAR(8)|X|Ghi thời điểm bắt đầu điều trị Cotrimoxazol (CTX), định dạng yyyymmdd.|||
|20|du_phong|VARCHAR||Trường dữ liệu dự phòng khi cần thiết.|||
||makb|VARCHAR(20)|X||X||
||mabn|VARCHAR(20)|X||X||
