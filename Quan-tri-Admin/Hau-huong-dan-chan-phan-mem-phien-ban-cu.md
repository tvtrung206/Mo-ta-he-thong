<div align="center">

`Công ty TNHH Giải Pháp Kỹ Thuật Số DH - Mẫu: DH-02: Mô tả thay đổi hệ thống DHG.Hospital 3.1`

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/dh-hos/dhg.hospitalprinter/main/Deploy_Tools/Logo.ico" alt="Simple Icons" width=70>
  <h1>HƯỚNG DẪN SỬ DỤNG</h1>  
</div>
<div align="center">

#### CHỦ ĐỀ: HƯỚNG DẪN CẤU HÌNH POSTGRESQL NGĂN CHẶN DHG.HOSPITAL THEO PHIÊN BẢN

</div>

###### :eight_spoked_asterisk: Người lập: [**ÔNG TRIỆU HẬU**](https://github.com/ongtrieuhau)

###### :eight_spoked_asterisk: Ngày lập: **07/06/2024**

###### :eight_spoked_asterisk: Khách hàng nào có yêu cầu triển khai

#### TẠO TRIGGER ĐỂ HẠN CHẾ PHIÊN BẢN THEO MODULE

Dưới đây hướng dẫn dành cho module và phiên bản cần hạn chế  (những phiên bản cũ hơn, không sử dụng được).

- v_module: Giá trị module trong bảng current.cauhinhmay (3.24.0606.0)

- v_version : Giá trị phienban trong bảng current.cauhinhmay (Printer)

- Thay đổi 2 giá trị cụ thể trong nội dung sau, rồi thực thi lệnh SQL này. 

``` Declare the variable and use it in the DELETE statement
DO $$
DECLARE
    v_version VARCHAR := '3.24.0606.0';
    v_module VARCHAR := 'Printer';
-- Declare the variable and use it in the DELETE statement

BEGIN
    DELETE FROM current.psnhatky_module
    WHERE UPPER(module) = UPPER(v_module)
    AND REPLACE(phienban, '.', '')::BIGINT < REPLACE(v_version, '.', '')::BIGINT;

    -- Create or replace the function
    CREATE OR REPLACE FUNCTION current.psnhatky_module_printer_phienban (
    )
    RETURNS trigger LANGUAGE 'plpgsql'
    VOLATILE
    CALLED ON NULL INPUT
    SECURITY INVOKER
    PARALLEL UNSAFE
    COST 100
    AS
    $body$
    DECLARE
        v_version VARCHAR := '3.24.0606.0';
        v_module VARCHAR := 'Printer';
    BEGIN
        IF UPPER(COALESCE(NEW.module,''))=UPPER(v_module) AND REPLACE(NEW.phienban, '.', '')::BIGINT < REPLACE(v_version, '.', '')::BIGINT THEN
            DELETE FROM current.cauhinhmay WHERE UPPER(module) = UPPER(v_module) AND tenmay=NEW.tenmay ;
        END IF;
        RETURN NEW;
    END;
    $body$;

    -- Drop the existing trigger if it exists
    IF EXISTS (
        SELECT 1
        FROM pg_trigger
        WHERE tgname = 'psnhatky_module_printer_phienban_trigger'
    ) THEN
        EXECUTE 'DROP TRIGGER psnhatky_module_printer_phienban_trigger ON current.psnhatky_module';
    END IF;

    -- Create the new trigger
    EXECUTE 'CREATE TRIGGER psnhatky_module_printer_phienban_trigger
    BEFORE INSERT ON current.psnhatky_module
    FOR EACH ROW EXECUTE PROCEDURE current.psnhatky_module_printer_phienban()';

    CREATE OR REPLACE FUNCTION current.cauhinhmay_module_printer_phienban (
	)
	RETURNS trigger LANGUAGE 'plpgsql'
	VOLATILE
	CALLED ON NULL INPUT
	SECURITY INVOKER
	PARALLEL UNSAFE
	COST 100
	AS
	$body$
    DECLARE
        v_version VARCHAR := '3.24.0606.0';
        v_module VARCHAR := 'Printer';
	BEGIN
		IF UPPER(COALESCE(NEW.module,''))=UPPER(v_module) AND REPLACE(NEW.phienban, '.', '')::BIGINT < REPLACE(v_version, '.', '')::BIGINT THEN
        	RAISE EXCEPTION 'Lỗi phát sinh trong quá trình đăng ký máy tính. Vui lòng liên hệ Quản trị hệ thống!';
        	RETURN NULL;
    	END IF;
    	RETURN NEW;
	END;
	$body$;
	-- Drop the existing trigger if it exists
    IF EXISTS (
        SELECT 1
        FROM pg_trigger
        WHERE tgname = 'cauhinhmay_module_printer_phienban_trigger'
    ) THEN
        EXECUTE 'DROP TRIGGER cauhinhmay_module_printer_phienban_trigger ON current.cauhinhmay';
    END IF;
	CREATE TRIGGER cauhinhmay_module_printer_phienban_trigger  BEFORE INSERT ON current.cauhinhmay
	FOR EACH ROW EXECUTE PROCEDURE current.cauhinhmay_module_printer_phienban();

END $$;
```
#### KẾT QUẢ KHI TẠO SQL TRÊN

![image](https://i.imgur.com/gWH1uVv.png)
![image](https://i.imgur.com/aMrLG3r.png)

#### KẾT QUẢ KHI THỰC THI MODULE

![alt text](Hau-huong-dan-chan-phan-mem-phien-ban-cu.gif)

#### KẾT THÚC CHÚC THÀNH CÔNG
