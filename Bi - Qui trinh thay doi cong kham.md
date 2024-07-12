1.	Register:
-	Khi đăng ký khám chữa bệnh, nếu là đối tượng BHYT:
o	Có cấu hình công khám theo phòng:
 
 
	Như hình thì công khám mặc định khi đăng ký phòng khám [13] là [KB16].
o	Không có cấu hình mặc định công khám cho phòng thì  lấy theo công khám mặc định theo đối tượng, cấu hình tại đây:
 
o	 Trường hợp người dùng chọn lại công khám, thực hiện lưu công khám theo người dùng chọn, phụ thuộc tham số này:
 
2.	Presscription:
Khi thực hiện [Lưu] khám bệnh tại đây:
 
+ Thực hiện cập nhật công khám đúng phòng và bác sĩ khám.
+ Nếu có cấu hình công khám chuyên khoa theo danh mục phân loại bệnh:
 
 
+ Xét công khám lúc đăng ký tại mục [1]:
	Nếu (Chidinhcls.dathu = 0 và Chidinhcls.giabh >0):
	Thực hiện đánh dấu xóa công khám tại mục [1], thêm lại công khám chuyên khoa theo phân loại bệnh cho bác sĩ tại phòng đang khám.
Hoặc (Chidinhcls.dathu = 1 và Chidinhcls.giabh = giabh của công khám chuyên khoa):
	Thực hiện đánh dấu xóa công khám tại mục [1], thêm lại công khám chuyên khoa theo phân loại bệnh cho bác sĩ tại phòng đang khám.
+ Trong trường hợp bệnh nhân khám thêm chuyên khoa (căn cứ theo phân loại bệnh) thì căn cứ vào tham số hình dưới để thêm công khám chuyên khoa tự động:
 
+ Nếu có cấu hình theo phân loại bệnh thì thêm công khám theo cấu hình tại danh mục phân loại bệnh, ngược lại lấy theo đối tượng với giabh tính như sau:
	Chuyên khoa lần 2, lần 3 theo qui định:
if (giabh < (dem * giabh * 30 / 100))
              {

giabh = giabh - ((dem - 1) * giabh * 30 / 100)
       tile  = 10
}
else
{
       giabh = giabh * 30 / 100.
       tile  = 30
                      
}
Với dem: là số công khám đã có hiện tại.

