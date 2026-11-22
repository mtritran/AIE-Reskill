# Day 02: Document Parsing, Testing với Pytest & Data Processing (Pandas/Numpy)

> **Unit 1: Python Programming Advance**  
> **Target Outcome (LO1):** Thành thạo kỹ năng bóc tách tài liệu đa định dạng (Markdown, TXT, PDF, HTML), viết bộ kiểm thử tự động với `pytest`, và xử lý mảng/bảng dữ liệu với Pandas & Numpy để chuẩn bị dữ liệu đầu vào cho hệ thống RAG và LLM Pipeline.

---

## Mục lục bài học
1. [Bóc tách tài liệu (Document Parsing): TXT, Markdown, PDF, HTML](#1-bóc-tách-tài-liệu-document-parsing)
2. [Kiểm thử tự động với `pytest`](#2-kiểm-thử-tự-động-với-pytest)
3. [Xử lý dữ liệu với Pandas & Numpy](#3-xử-lý-dữ-liệu-với-pandas--numpy)
4. [Danh mục bài thực hành & Deliverables](#4-danh-mục-bài-thực-hành--deliverables)

---

## 1. Bóc tách tài liệu (Document Parsing)
Trong các hệ thống RAG (Retrieval-Augmented Generation), bước đầu tiên luôn là chuyển đổi các tài liệu thô từ nhiều định dạng khác nhau thành văn bản sạch (clean text) trước khi tiến hành chia nhỏ (chunking) và đánh chỉ mục vector.
- 📖 **Tài liệu hướng dẫn chi tiết:** [06-document-parsing.md](file:///D:/Study%20&%20Learning/AIE-Reskill/day-02/06-document-parsing.md) (Lược sử, trích xuất text/metadata, merge, split, rotate, watermark và mã hóa với `pypdf`)

---

## 2. Kiểm thử tự động với `pytest`
Đảm bảo độ tin cậy của code bằng cách viết test tự động cho các hàm xử lý dữ liệu, kiểm tra schema và logic của tool.
- 📖 **Tài liệu hướng dẫn chi tiết:** [07-testing-with-pytest.md](file:///D:/Study%20&%20Learning/AIE-Reskill/day-02/07-testing-with-pytest.md) (Assert, pytest.raises, parametrize, fixtures, conftest.py và Mock LLM API)

---

## 3. Xử lý dữ liệu với Pandas & Numpy
Nắm vững các thao tác xử lý DataFrame, vector hóa mảng số liệu để làm việc với embedding và tập dữ liệu đánh giá (evaluation datasets).
- 📖 **Tài liệu hướng dẫn chi tiết:** [08-pandas-numpy.md](file:///D:/Study%20&%20Learning/AIE-Reskill/day-02/08-pandas-numpy.md) (NumPy vector & Cosine Similarity, Pandas DataFrame, Parquet format và tối ưu hiệu năng)
