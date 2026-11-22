# Chuyên đề: Kiểm thử Tự động với `pytest` (Testing for AI & Backend)

> **Mục tiêu cho AI Engineer:**  
> Trong các hệ thống AI Agent và LLM Pipeline, việc viết Unit Test và Integration Test giúp kiểm tra tính đúng đắn của logic tiền xử lý dữ liệu, schema validation, và quan trọng nhất: **Mock các lệnh gọi LLM API** để kiểm thử tự động với chi phí \$0 và tốc độ mili-giây.

---

## Mục lục
1. [Tại sao cần kiểm thử tự động với `pytest`?](#1-tại-sao-cần-kiểm-thử-tự-động-với-pytest)
2. [Cài đặt & Cấu trúc thư mục Test chuẩn](#2-cài-đặt--cấu-trúc-thư-mục-test-chuẩn)
3. [Cú pháp Assert & Bắt lỗi ngoại lệ (`pytest.raises`)](#3-cú-pháp-assert--bắt-lỗi-ngoại-lệ-pytestraises)
4. [Kiểm thử nhiều kịch bản với `@pytest.mark.parametrize`](#4-kiểm-thử-nhiều-kịch-bản-với-pytestmarkparametrize)
5. [Tái sử dụng dữ liệu với Fixtures (`@pytest.fixture`, `conftest.py`)](#5-tái-sử-dụng-dữ-liệu-với-fixtures-pytestfixture-conftestpy)
6. [Kỹ thuật Mocking trong AI: Giả lập LLM API với `unittest.mock`](#6-kỹ-thuật-mocking-trong-ai-giả-lập-llm-api-với-unittestmock)
7. [Tóm tắt & Cheat Sheet lệnh `pytest`](#7-tóm-tắt--cheat-sheet-lệnh-pytest)

---

## 1. Tại sao cần kiểm thử tự động với `pytest`?

Khác với thư viện `unittest` tích hợp sẵn của Python (vốn rườm rà, bắt buộc phải kế thừa class `TestCase`), `pytest` được cả cộng đồng ưa chuộng vì:
- **Cú pháp cực kỳ đơn giản**: Chỉ cần dùng từ khóa `assert` thông thường của Python.
- **Báo lỗi chi tiết (Rich Failure Reports)**: Tự động phân tích giá trị biến khi test thất bại.
- **Hệ thống Fixture mạnh mẽ**: Quản lý setup / teardown dữ liệu một cách trực quan.
- **Tương thích hoàn hảo với `asyncio`**: Hỗ trợ kiểm thử các hàm bất đồng bộ thông qua plugin `pytest-asyncio`.

---

## 2. Cài đặt & Cấu trúc thư mục Test chuẩn

### 2.1. Cài đặt
```powershell
# Cài đặt qua uv vào nhóm dev
uv add --dev pytest pytest-asyncio

# Hoặc pip
pip install pytest pytest-asyncio
```

### 2.2. Quy ước đặt tên & Cấu trúc dự án
`pytest` tự động dò tìm (test discovery) các file và hàm thỏa mãn:
- Tên file bắt đầu bằng `test_*.py` hoặc kết thúc bằng `*_test.py`.
- Tên hàm kiểm thử bắt đầu bằng `test_*()`.

```text
my_agent_project/
├── src/
│   ├── parser.py          # Code xử lý dữ liệu
│   └── agent_tool.py      # Code tool của Agent
├── tests/
│   ├── conftest.py        # Chứa các fixture dùng chung cho toàn bộ test
│   ├── test_parser.py     # Test chức năng parser
│   └── test_tools.py      # Test các agent tool
└── pyproject.toml
```

### 2.3. Chạy kiểm thử
```powershell
# Chạy tất cả test
uv run pytest

# Chạy hiển thị chi tiết từng test case
uv run pytest -v

# Dừng lại ngay khi gặp test case đầu tiên bị fail
uv run pytest -x
```

---

## 3. Cú pháp Assert & Bắt lỗi ngoại lệ (`pytest.raises`)

### 3.1. Dùng `assert` chuẩn Python
```python
# src/calculator.py
def calculate_discount(price: float, discount_percent: float) -> float:
    if discount_percent < 0 or discount_percent > 100:
        raise ValueError("Phần trăm giảm giá phải từ 0 đến 100")
    return price * (1 - discount_percent / 100)

# tests/test_calculator.py
from src.calculator import calculate_discount

def test_calculate_discount_valid():
    result = calculate_discount(100.0, 20.0)
    assert result == 80.0
    assert isinstance(result, float)
```

### 3.2. Bắt lỗi ngoại lệ với `pytest.raises`
Để kiểm tra xem hàm có ném ra lỗi mong đợi khi nhận đầu vào không hợp lệ hay không:

```python
import pytest
from src.calculator import calculate_discount

def test_calculate_discount_invalid_percent():
    # Kỳ vọng hàm ném ra ValueError với thông báo tương ứng
    with pytest.raises(ValueError, match="Phần trăm giảm giá phải từ 0 đến 100"):
        calculate_discount(100.0, 150.0)
```

---

## 4. Kiểm thử nhiều kịch bản với `@pytest.mark.parametrize`

Thay vì phải copy-paste nhiều hàm test cho từng trường hợp, `@pytest.mark.parametrize` cho phép chạy cùng 1 bài test với hàng loạt bộ dữ liệu đầu vào và đầu ra khác nhau:

```python
import pytest

def clean_query_text(query: str) -> str:
    """Làm sạch câu hỏi trước khi đưa vào RAG vector search."""
    if not query:
        return ""
    return query.strip().lower()

@pytest.mark.parametrize(
    "raw_input, expected_output",
    [
        ("  Hello World  ", "hello world"),
        ("AI AGENT", "ai agent"),
        ("", ""),
        ("   ", ""),
        ("Python 3.13!", "python 3.13!"),
    ]
)
def test_clean_query_text(raw_input, expected_output):
    assert clean_query_text(raw_input) == expected_output
```

---

## 5. Tái sử dụng dữ liệu với Fixtures (`@pytest.fixture`, `conftest.py`)

### 5.1. Fixture cơ bản (Setup & Teardown)
Fixture chuẩn bị tài nguyên (tạo file tạm, kết nối DB giả lập) trước khi test và tự động dọn dẹp sau khi test xong:

```python
import pytest
import os

@pytest.fixture
def sample_text_file(tmp_path):
    """Fixture tạo một file văn bản mẫu trong thư mục tạm của OS."""
    file_path = tmp_path / "sample_doc.txt"
    file_path.write_text("Dữ liệu thử nghiệm cho RAG chunking", encoding="utf-8")
    
    # yield cung cấp giá trị cho hàm test, sau yield là code dọn dẹp
    yield str(file_path)
    
    # Teardown: xóa file nếu cần (tmp_path tự động dọn sau phiên test)
    if os.path.exists(file_path):
        os.remove(file_path)

def test_read_sample_file(sample_text_file):
    with open(sample_text_file, "r", encoding="utf-8") as f:
        content = f.read()
    assert "RAG chunking" in content
```

### 5.2. File dùng chung: `conftest.py`
Mọi fixture đặt trong file `conftest.py` sẽ **tự động có hiệu lực trên toàn bộ thư mục `tests/`** mà không cần phải `import` thủ công.

---

## 6. Kỹ thuật Mocking trong AI: Giả lập LLM API với `unittest.mock`

> [!IMPORTANT]
> **Tại sao không nên gọi LLM API thật trong Unit Test?**
> 1. **Tốn chi phí token**: Chạy test CI/CD hàng trăm lần mỗi ngày sẽ phát sinh chi phí lớn.
> 2. **Chậm**: Mỗi lần test phải đợi mạng 2–5 giây.
> 3. **Không ổn định (Flaky Tests)**: Mạng chập chờn hoặc mô hình sinh ra từ ngữ khác nhau sẽ làm test fail ngẫu nhiên.

Sử dụng `unittest.mock.patch` để giả lập phản hồi của mô hình AI:

```python
# src/agent_service.py
import httpx

def get_sentiment(text: str) -> str:
    """Hàm gửi request tới LLM API để phân tích cảm xúc."""
    response = httpx.post("https://api.openai.com/v1/chat/completions", json={"prompt": text})
    data = response.json()
    return data["choices"][0]["message"]["content"]
```

```python
# tests/test_agent_service.py
from unittest.mock import patch, MagicMock
from src.agent_service import get_sentiment

@patch("src.agent_service.httpx.post")
def test_get_sentiment_mocked(mock_post):
    # 1. Tạo phản hồi giả lập (Mock Response)
    mock_response = MagicMock()
    mock_response.json.return_value = {
        "choices": [{"message": {"content": "POSITIVE"}}]
    }
    mock_post.return_value = mock_response

    # 2. Gọi hàm thực tế
    result = get_sentiment("Khóa học AI Engineer này rất tuyệt vời!")

    # 3. Kiểm tra kết quả mà KHÔNG tốn 1 xu chi phí API!
    assert result == "POSITIVE"
    mock_post.assert_called_once()  # Xác nhận API đã được gọi đúng 1 lần
```

---

## 7. Tóm tắt & Cheat Sheet lệnh `pytest`

| Lệnh | Ý nghĩa |
| :--- | :--- |
| `uv run pytest` | Chạy toàn bộ các test case trong thư mục `tests/` |
| `uv run pytest -v` | Hiển thị chi tiết tên từng hàm test (verbose) |
| `uv run pytest -k "parser"` | Chỉ chạy các bài test có tên chứa chữ "parser" |
| `uv run pytest tests/test_tools.py` | Chỉ chạy file test cụ thể |
| `uv run pytest -x` | Dừng ngay lập tức khi phát hiện bài test đầu tiên bị lỗi |
| `uv run pytest --lf` | Chỉ chạy lại những bài test bị rớt (Last Failed) ở lần trước |
