# Chuyên đề: Python Functions, Context Managers & Decorators

> **Dành cho AI Engineers & Backend Reskilling**  
> Tài liệu này tổng hợp và tinh gọn toàn bộ kiến thức cốt lõi từ căn bản đến nâng cao về hàm, phạm vi biến, closure và decorator trong Python. Đặc biệt gắn liền với các bài toán thực tế khi xây dựng hệ thống **AI Agent** và **FastAPI**.

---

## Mục lục
1. [Phần 1: Function Best Practices & Cạm bẫy kinh điển (Gotchas)](#phần-1-function-best-practices--cạm-bẫy-kinh-điển-gotchas)
2. [Phần 2: Context Managers (`with` statement)](#phần-2-context-managers-with-statement)
3. [Phần 3: Bản chất của Decorator (Under the Hood)](#phần-3-bản-chất-của-decorator-under-the-hood)
4. [Phần 4: Kỹ thuật Decorator nâng cao & Ứng dụng trong AI Agent](#phần-4-kỹ-thuật-decorator-nâng-cao--ứng-dụng-trong-ai-agent)
5. [Tổng kết & Bài tập tự luyện](#phần-5-tổng-kết--bài-tập-tự-luyện)

---

## Phần 1: Function Best Practices & Cạm bẫy kinh điển (Gotchas)

### 1.1. Docstring – Tại sao tối quan trọng trong AI Engineering?

Trong lập trình truyền thống, docstring chỉ dùng để đồng nghiệp dễ đọc code. Nhưng trong **AI Engineering**, docstring trở thành **"câu lệnh điều khiển" (Prompt)** quyết định hệ thống AI có chạy đúng hay không.

#### A. Là "bộ não" giúp AI Agent chọn và gọi đúng Tool (Function Calling)
Khi xây dựng AI Agent (bằng LangChain, LangGraph, LlamaIndex, OpenAI SDK...), bạn cung cấp cho LLM một danh sách các hàm Python (Tools) như `tim_kiem_don_hang()`, `huy_ve()`, `tinh_tien()`.

**LLM không hề đọc code bên trong hàm của bạn.** Thứ duy nhất nó đọc để hiểu hàm đó làm gì, khi nào nên gọi, và truyền tham số gì vào chính là **tên hàm, type hints và Docstring**.

- **Nếu docstring sơ sài:** AI sẽ gọi nhầm hàm, truyền sai định dạng dữ liệu, hoặc bỏ qua tool dù đang rất cần.
- **Nếu docstring chi tiết:** AI tự động hiểu ngữ cảnh và trích xuất đúng thông tin từ câu hỏi của người dùng để điền vào tham số.

```python
# ❌ Docstring tệ -> AI rất dễ đoán sai hoặc truyền sai định dạng ngày
def get_weather(city: str, date: str):
    """Lấy thời tiết."""
    ...

# ✅ Docstring chuẩn AI Engineering -> AI hiểu chính xác phải làm gì
def get_weather(city: str, date: str) -> dict:
    """Tra cứu dự báo thời tiết cho một thành phố vào một ngày cụ thể.
    Chỉ sử dụng công cụ này khi người dùng hỏi về thời tiết trong tương lai gần (tối đa 7 ngày).

    Args:
        city: Tên thành phố bằng tiếng Anh (ví dụ: "Hanoi", "Ho Chi Minh City").
        date: Ngày cần xem theo định dạng chuẩn ISO YYYY-MM-DD (ví dụ: "2026-11-21").
    """
    ...
```

> [!NOTE]
> Ở ví dụ trên, nhờ docstring quy định rõ `YYYY-MM-DD` và tên tiếng Anh, nếu user hỏi *"Mai ở Sài Gòn mưa không?"*, AI sẽ tự dịch thành `city="Ho Chi Minh City"` và tự tính ngày mai ra `date="2026-11-22"`.

#### B. Định hình cấu trúc dữ liệu đầu ra (Structured Outputs / Pydantic)
Trong các bài toán trích xuất dữ liệu (Data Extraction) từ văn bản thô sang JSON bằng Pydantic hoặc Instructor, mô tả trong docstring và field description chính là prompt hướng dẫn LLM bóc tách từng trường thông tin.

```python
from pydantic import BaseModel, Field

class HoSoUngVien(BaseModel):
    """Trích xuất thông tin tóm tắt từ CV của ứng viên."""
    
    so_nam_kinh_nghiem: int = Field(
        description="Tổng số năm kinh nghiệm làm việc thực tế, không tính thời gian thực tập."
    )
    ky_nang_chinh: list[str] = Field(
        description="Danh sách tối đa 5 kỹ năng lập trình nổi bật nhất."
    )
```

#### C. Giúp AI Coding Assistants (Cursor, Copilot) sinh code chuẩn xác
Các AI Engineer hiện đại dùng Cursor, GitHub Copilot hay Claude Code liên tục để viết pipeline xử lý dữ liệu hoặc huấn luyện model:
- Khi dự án có hàng trăm file xử lý tensor, dataframe phức tạp, AI Assistant dựa vào docstring để biết **shape của tensor** (ví dụ: `(batch_size, seq_len, hidden_dim)`), kiểu dữ liệu đầu vào/ra mà không cần phải đọc toàn bộ codebase.
- Viết docstring trước (Docstring-driven development) giúp bạn ra lệnh cho Cursor/Copilot tự động sinh ra đoạn code bên dưới chính xác tới 90%.

#### D. Tối ưu hóa ngữ cảnh trong hệ thống RAG (Code Retrieval)
Nếu bạn xây dựng một hệ thống RAG để hỏi đáp trên kho mã nguồn (Codebase QA) của công ty:
- Các hệ thống indexing code thường tách nhỏ (chunking) theo từng hàm/class và dùng mô hình Embedding để biến docstring thành vector.
- Khi lập trình viên tìm kiếm bằng ngôn ngữ tự nhiên (ví dụ: *"Hàm nào xử lý làm sạch dữ liệu bị thiếu?"*), công cụ tìm kiếm sẽ khớp câu hỏi đó với **docstring** chứ không phải với các dòng code `df.fillna()` khô khan.

> [!IMPORTANT]
> **Tóm lại:** Trong AI Engineering, **Docstring chính là một dạng Prompt Engineering được nhúng trực tiếp vào code**. Viết docstring rõ ràng, chặt chẽ không còn là "thói quen tốt cho đẹp code" nữa, mà là kỹ năng bắt buộc để hệ thống AI hoạt động ổn định và không bị ảo giác (hallucination).

---

### 1.2. Cơ chế truyền tham số: Pass by Assignment
Python không hoàn toàn là *Pass by Value* cũng không hẳn là *Pass by Reference*, mà là **Pass by Object Reference (Pass by Assignment)**:
- **Immutable types** (`int`, `float`, `str`, `tuple`): Khi sửa trong hàm, Python tạo object mới $\rightarrow$ Biến bên ngoài không bị đổi.
- **Mutable types** (`list`, `dict`, `set`): Truyền vào địa chỉ tham chiếu $\rightarrow$ Thao tác sửa đổi (in-place mutation) sẽ làm thay đổi biến gốc bên ngoài!

---

### 1.3. Cạm bẫy kinh điển: Default Argument là Mutable Object ⚠️

#### ❌ Sai lầm phổ biến:
```python
def log_agent_step(step_name: str, history: list = []):  # NGUY HIỂM!
    history.append(step_name)
    return history

print(log_agent_step("Step 1"))  # Output: ['Step 1']
print(log_agent_step("Step 2"))  # Output: ['Step 1', 'Step 2'] <-- Bị dính dữ liệu cũ!
```
*Lý do:* Giá trị mặc định của hàm được khởi tạo **chỉ 1 lần duy nhất** tại thời điểm Python định nghĩa hàm (function definition time), chứ không phải mỗi lần gọi hàm.

####  Cách viết chuẩn (Best Practice):
```python
def log_agent_step(step_name: str, history: list | None = None) -> list:
    if history is None:
        history = []
    history.append(step_name)
    return history

print(log_agent_step("Step 1"))  # ['Step 1']
print(log_agent_step("Step 2"))  # ['Step 2'] - Độc lập, an toàn!
```

---

## Phần 2: Context Managers (`with` statement)

Context Manager đảm bảo tài nguyên được giải phóng an toàn (đóng file, ngắt kết nối database, giải phóng khóa lock) ngay cả khi code phát sinh Exception.

### 2.1. Cú pháp `with` truyền thống
```python
with open("config.txt", "w", encoding="utf-8") as f:
    f.write("api_key=xyz")
# Ra khỏi khối with, file tự động được đóng dù có lỗi xảy ra
```

### 2.2. Tự tạo Context Manager bằng `@contextmanager`
Thay vì phải viết cả class với 2 phương thức `__enter__` và `__exit__`, ta dùng decorator `@contextmanager` từ thư viện `contextlib`:

```python
import time
from contextlib import contextmanager

@contextmanager
def execution_timer(task_name: str):
    start = time.perf_counter()
    print(f"Bắt đầu: {task_name}")
    try:
        yield  # Nơi code bên trong khối `with` sẽ được thực thi
    finally:
        elapsed = time.perf_counter() - start
        print(f"Hoàn thành {task_name} trong {elapsed:.4f} giây")

# Sử dụng:
with execution_timer("Gọi mô hình LLM"):
    time.sleep(0.5)  # Giả lập độ trễ API
```

---

## Phần 3: Bản chất của Decorator (Under the Hood)

Để hiểu cặn kẽ Decorator, bạn cần nắm vững 3 khái niệm nền tảng:

### 3.1. Functions are Objects (Hàm là đối tượng hạng nhất)
Hàm có thể:
1. Gán cho một biến khác: `say = print; say("Hello")`
2. Truyền vào hàm khác như tham số.
3. Được định nghĩa lồng nhau và trả về từ một hàm khác.

```python
def get_llm_formatter(format_type: str):
    def json_format(data): return f"{{\"result\": \"{data}\"}}"
    def text_format(data): return f"Plain text: {data}"
    
    return json_format if format_type == "json" else text_format

formatter = get_llm_formatter("json")
print(formatter("Thành công"))  # Output: {"result": "Thành công"}
```

---

### 3.2. Scope (Phạm vi) & Biến `nonlocal`
- **LEGB Rule:** Python tìm biến theo thứ tự: **L**ocal $\rightarrow$ **E**nclosing $\rightarrow$ **G**lobal $\rightarrow$ **B**uilt-in.
- Muốn sửa biến của hàm bao bọc (Enclosing scope) từ hàm con bên trong, bắt buộc dùng từ khóa **`nonlocal`**:

```python
def make_counter():
    count = 0  # Thuộc Enclosing Scope
    def increment():
        nonlocal count  # Báo cho Python biết muốn sửa biến 'count' ở scope cha
        count += 1
        return count
    return increment

c = make_counter()
print(c())  # 1
print(c())  # 2
```

---

### 3.3. Closures (Bao đóng)
**Closure** là một hàm ghi nhớ các giá trị ở phạm vi cha (Enclosing scope) ngay cả khi hàm cha **đã chạy xong và bị xóa khỏi stack bộ nhớ**.

```python
def make_multiplier(factor: int):
    # 'factor' sẽ được lưu trong closure của hàm multiply
    def multiply(x: int) -> int:
        return x * factor
    return multiply

double = make_multiplier(2)
print(double(5))  # 10
# Kiểm tra closure trong nội tại Python:
print(double.__closure__[0].cell_contents)  # Output: 2
```

---

### 3.4. Định nghĩa Decorator đầu tiên
Decorator bản chất là một **Higher-Order Function nhận vào một hàm và trả về một hàm bọc mới**.

```python
def my_decorator(func):
    def wrapper():
        print("[Trước khi gọi hàm]")
        func()
        print("[Sau khi gọi hàm]")
    return wrapper

# Cách dùng cú pháp @:
@my_decorator
def greet():
    print("Xin chào Agent!")

greet()
```
> **Bản chất của `@my_decorator` chính là phép gán:**  
> `greet = my_decorator(greet)`

---

## Phần 4: Kỹ thuật Decorator nâng cao & Ứng dụng trong AI Agent

### 4.1. Vấn đề mất Metadata và giải pháp `@functools.wraps` ⚠️

Khi bọc hàm bằng wrapper, tên hàm (`__name__`) và tài liệu (`__doc__`) sẽ bị biến thành của `wrapper`. Điều này sẽ làm **hỏng các framework AI** vốn đọc `__name__` và `__doc__` để đăng ký tool.

```python
import functools

def good_decorator(func):
    @functools.wraps(func)  # BẮT BUỘC: Giữ nguyên docstring, name, annotations gốc!
    def wrapper(*args, **kwargs):
        return func(*args, **kwargs)
    return wrapper

@good_decorator
def get_weather(city: str) -> str:
    """Lấy dự báo thời tiết của thành phố chỉ định."""
    return f"Nắng tại {city}"

print(get_weather.__name__)  # Output: 'get_weather' (không bị đổi thành 'wrapper')
print(get_weather.__doc__)   # Vẫn giữ nguyên docstring của tool!
```

---

### 4.2. Decorator nhận tham số (Decorators that take arguments)
Mô hình cấu trúc 3 tầng:
1. Tầng 1: Nhận tham số cấu hình của decorator.
2. Tầng 2: Nhận hàm mục tiêu cần bọc.
3. Tầng 3 (`wrapper`): Nhận tham số khi hàm mục tiêu được gọi.

```python
def repeat(num_times: int):
    """Decorator chạy lại hàm n lần."""
    def decorator_repeat(func):
        @functools.wraps(func)
        def wrapper(*args, **kwargs):
            result = None
            for i in range(num_times):
                print(f"Lần chạy {i + 1}/{num_times}...")
                result = func(*args, **kwargs)
            return result
        return wrapper
    return decorator_repeat

@repeat(num_times=3)
def send_heartbeat():
    print("Ping máy chủ...")

send_heartbeat()
```

---

### 4.3. Ứng dụng thực chiến 1: `@retry` với Exponential Backoff khi gọi LLM API

Trong hệ thống AI, các lệnh gọi API sang OpenAI/Anthropic rất dễ gặp lỗi mạng hoặc chạm giới hạn Rate Limit (HTTP 429). Decorator sau giúp tự động thử lại:

```python
import functools
import time

def retry_api_call(max_retries: int = 3, initial_delay: float = 1.0, backoff_factor: float = 2.0):
    def decorator(func):
        @functools.wraps(func)
        def wrapper(*args, **kwargs):
            retries = 0
            delay = initial_delay
            while True:
                try:
                    return func(*args, **kwargs)
                except Exception as e:
                    retries += 1
                    if retries > max_retries:
                        print(f"❌ [Retry] Đã thử {max_retries} lần nhưng thất bại. Báo lỗi ra ngoài!")
                        raise e
                    print(f"⚠️ [Retry] Gặp lỗi '{e}'. Đang thử lại lần {retries}/{max_retries} sau {delay:.1f}s...")
                    time.sleep(delay)
                    delay *= backoff_factor
        return wrapper
    return decorator

# Thử nghiệm với hàm giả lập lỗi mạng
call_count = 0

@retry_api_call(max_retries=3, initial_delay=0.5)
def call_gemini_api(prompt: str) -> str:
    global call_count
    call_count += 1
    if call_count < 3:
        raise ConnectionError("Mạng chập chờn (503 Service Unavailable)")
    return f"Phản hồi từ Gemini: Đã xử lý prompt '{prompt}'"

print(call_gemini_api("Xin chào AI"))
```

---

### 4.4. Ứng dụng thực chiến 2: Mô phỏng `@tool` Registry cho AI Agent

Đây là cơ chế chính xác mà **LangChain**, **LangGraph** hay **Agno** sử dụng để tự động gom các hàm Python thành danh sách Tool cho Agent:

```python
import functools
from typing import Callable, Any

# Bộ nhớ lưu danh sách tool của Agent
TOOL_REGISTRY: dict[str, dict[str, Any]] = {}

def tool(name: str | None = None, description: str | None = None):
    """Decorator biến một hàm Python thành Tool cho AI Agent."""
    def decorator(func: Callable):
        tool_name = name or func.__name__
        tool_desc = description or (func.__doc__ or "").strip()
        
        # Đăng ký tool vào hệ thống
        TOOL_REGISTRY[tool_name] = {
            "name": tool_name,
            "description": tool_desc,
            "fn": func
        }
        
        @functools.wraps(func)
        def wrapper(*args, **kwargs):
            return func(*args, **kwargs)
        return wrapper
    return decorator

# --- Định nghĩa các công cụ ---
@tool(description="Tính toán biểu thức toán học")
def calculate(expression: str) -> str:
    return str(eval(expression))

@tool(description="Tra cứu số dư tài khoản ngân hàng")
def check_balance(account_id: str) -> str:
    return f"Số dư của {account_id} là 50,000,000 VND"

# --- Giả lập Agent tìm và gọi tool ---
print(" Danh sách Tool Agent đã nhận diện:")
for t_name, t_info in TOOL_REGISTRY.items():
    print(f"- Tool: '{t_name}' | Mô tả: {t_info['description']}")

# Agent quyết định gọi tool:
action = "calculate"
result = TOOL_REGISTRY[action]["fn"]("15 * 8")
print(f"\nKết quả thực thi tool '{action}': {result}")
```

---

## Phần 5: Tổng kết & Bài tập tự luyện

### Tóm tắt nhanh:
1. **Docstring**: Là "prompt" để LLM hiểu tool $\rightarrow$ Luôn viết rõ ràng.
2. **Default Arguments**: Tuyệt đối không dùng `list` hay `dict` làm giá trị mặc định $\rightarrow$ Dùng `None`.
3. **Closure**: Ghi nhớ biến của scope cha nhờ `nonlocal` và scope bao bọc.
4. **Decorator**: Là `func = decorator(func)`.
5. **Luôn dùng `@functools.wraps`**: Để bảo vệ metadata (`__name__`, `__doc__`).

###  Bài tập tự luyện (Lab Day 1):
1. **Bài 1:** Viết decorator `@log_latency(threshold_seconds=1.0)`: Nếu hàm chạy lâu hơn `threshold_seconds`, in ra cảnh báo màu vàng `[SLOW WARNING]`.
2. **Bài 2:** Viết decorator `@enforce_types`: Kiểm tra kiểu dữ liệu truyền vào có đúng với Type Hints của hàm không, nếu sai raise `TypeError`.
