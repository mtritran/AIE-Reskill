# Hướng dẫn Quản lý Môi trường ảo với `venv` (Dành riêng cho Windows)

`venv` là thư viện tích hợp sẵn của Python giúp tạo ra môi trường ảo độc lập cho từng dự án, ngăn chặn xung đột thư viện giữa các dự án khác nhau và giữ sạch môi trường Python hệ thống.

---

## 1. Kiểm tra `venv` trên Windows

Mở PowerShell hoặc Command Prompt và kiểm tra:

```powershell
python -m venv --help
```

---

## 2. Các bước sử dụng `venv` trên Windows

### Bước 1: Điều hướng đến thư mục dự án
```powershell
cd D:\path\to\your\project
```

### Bước 2: Tạo môi trường ảo
```powershell
python -m venv venv
```
> Lệnh này sẽ tạo thư mục `venv\` chứa Python interpreter và thư mục `Lib\site-packages\` riêng biệt.

---

## 3. Kích hoạt môi trường ảo (Activate)

Tùy vào công cụ terminal bạn đang sử dụng trên Windows:

| Terminal | Lệnh kích hoạt |
| :--- | :--- |
| **PowerShell** (Khuyên dùng) | `.\venv\Scripts\Activate.ps1` *(hoặc `.\venv\Scripts\Activate`)* |
| **Command Prompt (CMD)** | `venv\Scripts\activate.bat` |

Khi kích hoạt thành công, dấu nhắc lệnh sẽ có tiền tố `(venv)`:
```text
(venv) PS D:\my-project>
```

> [!TIP]
> **Xử lý lỗi chặn script trên PowerShell:**  
> Nếu gặp thông báo lỗi màu đỏ: *"... cannot be loaded because running scripts is disabled on this system"*, hãy chạy lệnh sau một lần duy nhất để cấp quyền:
> ```powershell
> Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
> ```
> Sau đó chạy lại: `.\venv\Scripts\Activate.ps1`.

---

## 4. Cài đặt thư viện trong môi trường ảo

Mọi thư viện cài qua `pip` khi môi trường đã kích hoạt sẽ chỉ nằm trong thư mục `venv\` của dự án:

```powershell
# Cài đặt thư viện
pip install requests pydantic

# Xuất danh sách thư viện ra file
pip freeze > requirements.txt

# Cài đặt lại từ file requirements
pip install -r requirements.txt
```

---

## 5. Hủy kích hoạt (Deactivate)

Khi không làm việc trên dự án này nữa, gõ:

```powershell
deactivate
```
Dấu `(venv)` sẽ biến mất và terminal trở về trạng thái Python thông thường.
