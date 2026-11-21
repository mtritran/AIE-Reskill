# Cẩm nang Tinh gọn về Python UV (Windows Edition)

**UV** (phát triển bởi Astral, viết bằng **Rust**) là công cụ quản lý package và dự án Python hiện đại nhất hiện nay. UV thay thế toàn diện cả 4 công cụ truyền thống: `pip`, `venv`, `pyenv` và `poetry` với tốc độ nhanh gấp **10 – 100 lần**.

---

## 1. Tại sao AI Engineer nên dùng UV thay vì pip + venv?

1. **Tốc độ vượt trội**: Cài đặt gói, resolve dependency phức tạp trong vài giây thay vì vài phút.
2. **Quản lý tất cả trong 1**: Không cần nhớ nhiều lệnh rời rạc (`venv`, `pip`, `poetry`, `pyenv`).
3. **Không cần kích hoạt venv thủ công**: Dùng `uv run` sẽ tự động chạy trong môi trường của dự án.
4. **Tự động tải và đổi phiên bản Python**: Không cần lên trang python.org tải installer cài thủ công.
5. **Lockfile chuẩn (`uv.lock`)**: Đảm bảo 100% chạy trên máy nào cũng cùng chính xác một phiên bản dependency.

---

## 2. Cài đặt UV trên Windows

Mở **PowerShell** và chọn 1 trong 2 cách:

### Cách 1: Qua winget (Khuyên dùng)
```powershell
winget install astral-sh.uv
```

### Cách 2: Qua script chính thức của Astral
```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

Sau khi cài đặt, tắt và mở lại terminal rồi kiểm tra:
```powershell
uv --version
```

---

## 3. Workflow thực chiến hàng ngày với UV

### 3.1. Khởi tạo dự án mới: `uv init`
```powershell
uv init my-project
cd my-project
```
UV sẽ tự động sinh:
- `pyproject.toml`: File cấu hình dự án & danh sách thư viện (chuẩn PEP 621).
- `.python-version`: Phiên bản Python dự án sử dụng.
- `.gitignore`: Đã bỏ qua sẵn `.venv`, cache...

### 3.2. Thêm thư viện: `uv add`
```powershell
# Cài đặt thư viện (tự động tạo .venv nếu chưa có và ghi vào pyproject.toml + uv.lock)
uv add fastapi pydantic httpx

# Cài đặt thư viện dev (chỉ dùng khi test/lint)
uv add --dev pytest ruff
```

### 3.3. Chạy code không cần activate venv: `uv run`
> [!IMPORTANT]
> Đây là tính năng tiện lợi nhất của UV. Bạn **không cần** chạy `.\venv\Scripts\Activate.ps1`. Chỉ cần dùng `uv run`:

```powershell
uv run main.py
uv run pytest
```

### 3.4. Gỡ bỏ thư viện: `uv remove`
```powershell
uv remove requests
```

### 3.5. Đồng bộ môi trường khi clone từ Git: `uv sync`
Khi bạn clone một dự án có file `pyproject.toml` và `uv.lock` về máy:
```powershell
uv sync
```
UV sẽ tự động tạo `.venv` và cài đặt chính xác mọi thư viện theo `uv.lock`.

---

## 4. Quản lý phiên bản Python tự động với UV

UV có thể tự tải và chuyển đổi giữa các phiên bản Python mà không làm ảnh hưởng máy tính:

```powershell
# Liệt kê các bản Python đang có trên máy
uv python list

# Tải và cài đặt một phiên bản Python mới (ví dụ 3.12)
uv python install 3.12

# Khóa phiên bản Python cho dự án hiện tại
uv python pin 3.12
```

---

## 5. Chạy tool CLI tạm thời với `uvx`

Để chạy một công cụ (như linter `ruff`, format `black`) mà không muốn cài vào dự án:
```powershell
uvx ruff check .
```
UV sẽ tải về cache tạm, chạy xong và không làm bẩn môi trường dự án.

---

## 6. Bảng chuyển đổi lệnh nhanh (Từ pip/venv sang UV)

| Thao tác | Cú pháp cũ (`pip` / `venv`) | Cú pháp mới với `uv` (Khuyên dùng) |
| :--- | :--- | :--- |
| **Tạo môi trường ảo** | `python -m venv venv` | `uv init` hoặc `uv venv` |
| **Kích hoạt môi trường** | `.\venv\Scripts\Activate.ps1` | **Không cần** (dùng `uv run`) |
| **Cài thư viện** | `pip install pydantic` | `uv add pydantic` |
| **Cài thư viện dev** | Thêm thủ công vào `requirements-dev.txt` | `uv add --dev pytest` |
| **Gỡ thư viện** | `pip uninstall pydantic` | `uv remove pydantic` |
| **Chạy script** | `python main.py` | `uv run main.py` |
| **Đồng bộ toàn bộ** | `pip install -r requirements.txt` | `uv sync` |
| **Export requirements** | `pip freeze > requirements.txt` | `uv export -o requirements.txt` |
