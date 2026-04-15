[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=23574065&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** letuandat220@gmail.com
**Name:** Le Tuan Dat
**Student ID:** 2A202600382

---

## Mo ta

Bài Lab này thực hiện việc xây dựng một hệ thống ETL Pipeline cơ bản để xử lý dữ liệu thô từ định dạng JSON sang CSV, đồng thời áp dụng các quy tắc kiểm tra chất lượng dữ liệu (Data Validation) và biến đổi dữ liệu (Data Transformation). Ngoài ra, bài làm cũng bao gồm một thí nghiệm Stress Test để kiểm chứng tầm quan trọng của chất lượng dữ liệu đối với AI Agent.

Những gì tôi đã làm:
- Hoàn thiện tệp `solution.py` với đầy đủ các bước Extract, Validate, Transform, Load.
- Xây dựng cơ chế Logging để theo dõi số lượng bản ghi hợp lệ và bị lỗi (Data Observability).
- Thực hiện thí nghiệm so sánh hiệu năng của AI Agent khi sử dụng dữ liệu sạch và dữ liệu rác (Poisoned Data).
- Viết báo cáo phân tích chi tiết về tác động của chất lượng dữ liệu.

---

## Cach chay (How to Run)

### Prerequisites
Cài đặt các thư viện cần thiết:
```bash
pip install pandas pytest
```

### Chay ETL Pipeline
Để xử lý dữ liệu từ `raw_data.json` và tạo ra `processed_data.csv`:
```bash
python solution.py
```

### Chay Agent Simulation (Stress Test)
Để so sánh kết quả của Agent trên dữ liệu sạch và dữ liệu rác:
1. Tạo dữ liệu rác: `python generate_garbage.py`
2. Chạy mô phỏng: `python agent_simulation.py`

### Chay Testing
Để kiểm tra tính đúng đắn của toàn bộ bài làm theo yêu cầu của hệ thống autograding:
```bash
pytest tests/test_autograder.py
```

---

## Cau truc thu muc

```
├── solution.py              # Script chính thực hiện ETL Pipeline
├── processed_data.csv       # Dữ liệu đầu ra sau khi đã được làm sạch và biến đổi
├── experiment_report.md     # Báo cáo kết quả thí nghiệm Stress Test
├── raw_data.json            # Dữ liệu đầu vào thô
├── generate_garbage.py      # Script tạo dữ liệu lỗi để thử nghiệm
├── agent_simulation.py      # Script mô phỏng AI Agent
└── README.md                # File này
```

---

## Ket qua

- **Trạng thái:** Hoàn thành toàn bộ các yêu cầu.
- **Xử lý dữ liệu:** 
    - Tổng số bản ghi thô: 5
    - Số bản ghi hợp lệ: 3
    - Số bản ghi bị loại bỏ: 2 (do lỗi giá <= 0 hoặc danh mục trống)
- **Kiểm thử:** Đạt 100/100 điểm trên hệ thống autograding (tất cả 9 bài test đều pass).
- **Kết luận thí nghiệm:** AI Agent hoạt động chính xác trên dữ liệu được xử lý qua pipeline nhưng trả về kết quả sai lệch nghiêm trọng trên dữ liệu rác (outliers).
