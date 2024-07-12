1.	Register:
-	Khi đăng ký khám chữa bệnh, nếu là đối tượng BHYT:
	+ Có cấu hình công khám theo phòng:
 	
 	 ![image](https://github.com/user-attachments/assets/6bcc94b8-79f3-4f6c-8866-27544e7ad773)
	 ![image](https://github.com/user-attachments/assets/35e49c42-b5cc-49eb-8810-6d77109ed9f1)

 	Như hình thì công khám mặc định khi đăng ký phòng khám [13] là [KB16].
 
	+ Không có cấu hình mặc định công khám cho phòng thì  lấy theo công khám mặc định theo đối tượng, cấu hình tại đây:
	![image](https://github.com/user-attachments/assets/a473fb69-a900-402e-9a2c-47c0c52e448e)

	+ Trường hợp người dùng chọn lại công khám, thực hiện lưu công khám theo người dùng chọn, phụ thuộc tham số này:
	![image](https://github.com/user-attachments/assets/db55af9c-b909-4cb1-a80d-71982127ccf7)

 2.	Presscription:
- 	Khi thực hiện [Lưu] khám bệnh tại đây:
  
   	![image](https://github.com/user-attachments/assets/46304085-6a2d-4e49-8d62-11ff85f3c9e1)
	+ Thực hiện cập nhật công khám đúng phòng và bác sĩ khám.
	+ Nếu có cấu hình công khám chuyên khoa theo danh mục phân loại bệnh:

 	![image](https://github.com/user-attachments/assets/96d550a4-8398-4b9b-ab33-f0e64d78da2f)
	![image](https://github.com/user-attachments/assets/43b12132-61bc-484b-a6fa-321034a04fe5)

 	+ Xét công khám lúc đăng ký tại mục [1]:

	- Nếu (Chidinhcls.dathu = 0 và Chidinhcls.giabh >0):

	Thực hiện đánh dấu xóa công khám tại mục [1], thêm lại công khám chuyên khoa theo phân loại bệnh cho bác sĩ tại phòng đang khám.

	- Hoặc (Chidinhcls.dathu = 1 và Chidinhcls.giabh = giabh của công khám chuyên khoa):

	Thực hiện đánh dấu xóa công khám tại mục [1], thêm lại công khám chuyên khoa theo phân loại bệnh cho bác sĩ tại phòng đang khám.

  	+ Trong trường hợp bệnh nhân khám thêm chuyên khoa (căn cứ theo phân loại bệnh) thì căn cứ vào tham số hình dưới để thêm công khám chuyên khoa tự động:

	![image](https://github.com/user-attachments/assets/95e9672f-e040-4984-a4ee-ac87b69d5cec)
 
	+ Nếu có cấu hình theo phân loại bệnh thì thêm công khám theo cấu hình tại danh mục phân loại bệnh, ngược lại lấy theo đối tượng với giabh tính như sau:
	
 	Chuyên khoa lần 2, lần 3 theo qui định:

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

