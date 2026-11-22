# Chuyên đề: Xử lý Dữ liệu với Pandas & NumPy (Data Processing for AI)

> **Mục tiêu cho AI Engineer:**  
> Trong AI Engineering, **NumPy** là nền tảng tính toán vector cho Embeddings và ma trận trọng số, trong khi **Pandas** là công cụ quản lý các tập dữ liệu đánh giá (Golden Evaluation Datasets), lưu trữ vết logs của Agent, và làm sạch dữ liệu bảng (Tabular Data).

---

## Mục lục
1. [Tại sao AI Engineer cần thành thạo NumPy & Pandas?](#1-tại-sao-ai-engineer-cần-thành-thạo-numpy--pandas)
2. [NumPy: Tính toán Vector & Ma trận tương đồng (Cosine Similarity)](#2-numpy-tính-toán-vector--ma-trận-tương-đồng-cosine-similarity)
3. [Pandas: Quản lý DataFrame & Xử lý tập dữ liệu RAG](#3-pandas-quản-lý-dataframe--xử-lý-tập-dữ-liệu-rag)
4. [Tối ưu hiệu năng: Tại sao không dùng vòng lặp `for` với dữ liệu lớn?](#4-tối-ưu-hiệu-năng-tại-sao-không-dùng-vòng-lặp-for-với-dữ-liệu-lớn)
5. [Tóm tắt & Cheat Sheet](#5-tóm-tắt--cheat-sheet)

---

## 1. Tại sao AI Engineer cần thành thạo NumPy & Pandas?

- **NumPy (Numerical Python):** Viết bằng C, cho phép tính toán trên mảng đa chiều với tốc độ tiệm cận phần cứng. Khi một mô hình Embedding (như `text-embedding-3-small` hay `all-MiniLM-L6-v2`) trả về một vector 1536 chiều, NumPy chính là công cụ dùng để tính toán khoảng cách và tìm kiếm đoạn văn bản gần nhất.
- **Pandas:** Cung cấp cấu trúc bảng dữ liệu `DataFrame`. Trong chu trình phát triển AI (LLMOps), mọi tập dữ liệu mẫu (Golden Dataset để chấm điểm RAG), bảng lưu trace bước chạy của Agent, hay bảng kết quả test A/B giữa các prompt đều được xử lý bằng Pandas.

```powershell
# Cài đặt qua uv
uv add numpy pandas pyarrow

# Hoặc pip
pip install numpy pandas pyarrow
```

---

## 2. NumPy: Tính toán Vector & Ma trận tương đồng (Cosine Similarity)

### 2.1. Khởi tạo mảng & Thuộc tính cơ bản
```python
import numpy as np
V
# Tạo vector embedding giả lập (1x4 chiều)
emb1 = np.array([0.15, 0.85, 0.32, 0.05], dtype=np.float32)
emb2 = np.array([0.12, 0.88, 0.30, 0.08], dtype=np.float32)

print("Kích thước (Shape):", emb1.shape)  # (4,)
print("Kiểu dữ liệu (Dtype):", emb1.dtype)  # float32
```

---

### 2.2. Tính toán Cosine Similarity thủ công với NumPy
Độ tương đồng Cosine là thuật toán đo khoảng cách chuẩn trong hầu hết các Vector Database:

$$\text{Cosine Similarity}(u, v) = \frac{u \cdot v}{\|u\| \|v\|}$$

```python
import numpy as np

def cosine_similarity(u: np.ndarray, v: np.ndarray) -> float:
    """Tính độ tương đồng ngữ nghĩa giữa 2 vector embedding."""
    dot_product = np.dot(u, v)
    norm_u = np.linalg.norm(u)
    norm_v = np.linalg.norm(v)
    
    if norm_u == 0 or norm_v == 0:
        return 0.0
    return float(dot_product / (norm_u * norm_v))

# Kiểm tra độ tương đồng:
score = cosine_similarity(emb1, emb2)
print(f"Độ tương đồng Cosine: {score:.4f}")  # ~0.9986 (rất gần nhau)
```

---

### 2.3. Batch Similarity (Tính toán song song cho hàng nghìn vector)
Thay vì dùng vòng lặp `for` để tính từng vector với câu hỏi (query), ta dùng **nhân ma trận (Matrix Multiplication)** để tính toàn bộ trong 1 lệnh duy nhất:

```python
# Giả sử có 3 văn bản trong database, mỗi văn bản là 1 vector 4 chiều
database_embeddings = np.array([
    [0.15, 0.85, 0.32, 0.05],  # Tài liệu 1
    [0.90, 0.10, 0.05, 0.02],  # Tài liệu 2
    [0.18, 0.82, 0.35, 0.01],  # Tài liệu 3
])

query_embedding = np.array([0.12, 0.88, 0.30, 0.08])

# 1. Chuẩn hóa độ dài (L2-normalize)
db_normalized = database_embeddings / np.linalg.norm(database_embeddings, axis=1, keepdims=True)
q_normalized = query_embedding / np.linalg.norm(query_embedding)

# 2. Nhân ma trận với toán tử @ (nhanh gấp 100 lần vòng lặp for)
scores = db_normalized @ q_normalized

print("Điểm tương đồng từng tài liệu:", scores)
best_doc_idx = int(np.argmax(scores))
print(f"Tài liệu khớp nhất là Index {best_doc_idx} với điểm {scores[best_doc_idx]:.4f}")
```

---

## 3. Pandas: Quản lý DataFrame & Xử lý tập dữ liệu RAG

### 3.1. Tạo DataFrame từ danh sách các đoạn văn bản (Chunks)
```python
import pandas as pd

chunks_data = [
    {"doc_id": "doc_01", "page": 1, "text": "Python là ngôn ngữ phổ biến.", "category": "tech"},
    {"doc_id": "doc_01", "page": 2, "text": "   FastAPI hỗ trợ async I/O.   ", "category": "tech"},
    {"doc_id": "doc_02", "page": 1, "text": "Doanh thu quý 3 đạt 10 tỷ.", "category": "finance"},
    {"doc_id": "doc_03", "page": 1, "text": "", "category": "unknown"},  # Dữ liệu lỗi
]

df = pd.DataFrame(chunks_data)
print(df.head())
```

---

### 3.2. Làm sạch dữ liệu với Vectorized String Methods
Pandas cung cấp thuộc tính `.str` để thao tác trực tiếp trên toàn bộ cột chuỗi mà không cần dùng `for`:

```python
# 1. Cắt khoảng trắng thừa và viết thường
df["cleaned_text"] = df["text"].str.strip()

# 2. Tính số ký tự trong từng chunk
df["char_count"] = df["cleaned_text"].str.len()

# 3. Lọc bỏ các chunk rỗng (char_count == 0)
df_valid = df[df["char_count"] > 0].copy()
print(df_valid[["doc_id", "cleaned_text", "char_count"]])
```

---

### 3.3. Thao tác Phân nhóm (`groupby`) – Đánh giá hiệu năng Agent
Phân tích tỷ lệ trả lời đúng của AI Agent theo từng danh mục câu hỏi:

```python
# Bảng log đánh giá Agent
eval_logs = pd.DataFrame({
    "category": ["math", "math", "legal", "legal", "tech", "tech"],
    "is_correct": [True, True, False, True, True, True],
    "latency_seconds": [1.2, 1.5, 3.4, 2.9, 0.8, 1.1]
})

# Thống kê theo từng category: Tỷ lệ đúng (accuracy) và độ trễ trung bình (mean latency)
summary = eval_logs.groupby("category").agg(
    accuracy=("is_correct", "mean"),
    avg_latency=("latency_seconds", "mean"),
    total_queries=("is_correct", "count")
).reset_index()

print(summary)
```

---

### 3.4. Lưu trữ chuẩn cho AI: Định dạng Parquet
Trong kỹ thuật dữ liệu AI hiện đại, định dạng **Parquet** (cột) thay thế hoàn toàn cho CSV vì:
- Tốc độ đọc/ghi nhanh gấp **10–20 lần**.
- Dung lượng file nén giảm **70%–90%**.
- Giữ nguyên kiểu dữ liệu (không bị biến số thành chuỗi như CSV).

```python
# Lưu ra file Parquet
df_valid.to_parquet("rag_dataset.parquet", index=False)

# Đọc lại từ Parquet
df_loaded = pd.read_parquet("rag_dataset.parquet")
```

---

## 4. Tối ưu hiệu năng: Tại sao không dùng vòng lặp `for` với dữ liệu lớn?

Khi xử lý hàng triệu dòng văn bản hoặc embeddings:

| Cách tiếp cận | Tốc độ tương đối | Khi nào nên dùng? |
| :--- | :--- | :--- |
| **Vectorization (NumPy/Pandas)** | **1x (Nhanh nhất - Cực đại)** | Phép toán toán học, cắt chuỗi `.str`, điều kiện logic |
| **List Comprehension** | **~3x – 5x chậm hơn** | Xử lý logic phức tạp nhẹ |
| **`df.apply(lambda)`** | **~10x – 20x chậm hơn** | Khi không có hàm vector hóa tương đương |
| **`df.itertuples()`** | **~20x – 50x chậm hơn** | Cần duyệt từng dòng nhưng vẫn muốn giữ tốc độ vừa phải |
| **`df.iterrows()`** | **~200x chậm hơn (Rất chậm)** | ❌ **Tuyệt đối không dùng** trên tập dữ liệu sản xuất! |

---

## 5. Tóm tắt & Cheat Sheet

```python
# --- NUMPY ---
import numpy as np
a = np.zeros(1536)                      # Vector 0 kích thước 1536
dot = np.dot(vec_a, vec_b)              # Tích vô hướng
norm = np.linalg.norm(vec_a)            # Độ dài vector
top_k_idx = np.argsort(scores)[::-1][:5]# Lấy index 5 kết quả cao nhất

# --- PANDAS ---
import pandas as pd
df = pd.read_parquet("data.parquet")    # Đọc dữ liệu nhanh
df = df.dropna(subset=["text"])         # Bỏ dòng rỗng
df["text"] = df["text"].str.strip()     # Vectorized string clean
res = df.groupby("label")["score"].mean()# Thống kê điểm trung bình
```
