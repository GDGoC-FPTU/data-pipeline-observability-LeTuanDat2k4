# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** 2A202600382
**Name:** Le Tuan Dat
**Date:** 2026-04-15

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Agent: Based on my data, the best choice is Laptop at $1200. | 10/10 | Kết quả chính xác, sản phẩm phù hợp và giá đúng. |
| Garbage Data (`garbage_data.csv`) | Agent: Based on my data, the best choice is Nuclear Reactor at $999999. | 1/10 | Kết quả sai lệch hoàn toàn do dữ liệu bị nhiễu bởi Outlier. |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Trong tình huống "Garbage Data", AI Agent đã thất bại hoàn toàn trong việc đưa ra một câu trả lời hợp lý cho người dùng. Thay vì đề xuất một sản phẩm điện tử tiêu chuẩn như Laptop, hệ thống lại đề xuất một "Nuclear Reactor" với mức giá cực lớn là $999999. Điều này xảy ra do dữ liệu đầu vào đã bị "đầu độc" bởi các giá trị ngoại lai (Extreme Outliers) mà hệ thống mô phỏng của Agent (vốn được thiết kế đơn giản để tìm giá cao nhất) đã xác định nhầm là "lựa chọn tốt nhất". 

Ngoài vấn đề về Outliers, bộ dữ liệu rác còn chứa nhiều lỗi nghiêm trọng khác:
1. **Sai kiểu dữ liệu (Wrong Data Types):** Giá trị "ten dollars" thay vì số sẽ khiến các hàm tính toán toán học bị lỗi hoặc trả về kết quả không dự đoán được.
2. **Trùng lặp ID (Duplicate IDs):** Gây nhiễu khi cần truy xuất thông tin chính xác theo định danh.
3. **Giá trị rỗng (Null values):** Bản ghi "Ghost Item" không có danh mục và giá bằng 0 có thể khiến Agent đưa ra thông tin vô nghĩa hoặc gây lỗi hệ thống nếu không được xử lý null-check.

Nếu không có một quy trình ETL (Extract, Transform, Load) chuyên nghiệp để kiểm tra, lọc và làm sạch dữ liệu trước khi nạp vào AI, trí thông minh của AI Agent sẽ trở nên vô dụng. Nó sẽ hoạt động theo nguyên tắc "Garbage In, Garbage Out" (Đầu vào là rác, đầu ra cũng là rác). Do đó, khả năng quan sát dữ liệu (Data Observability) và kiểm soát chất lượng là điều kiện tiên quyết để xây dựng các hệ thống AI tin cậy và an toàn trong thực tế.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** (Dong y hay khong? Giai thich ngan gon.)

Đồng ý hoàn toàn. Một câu lệnh (prompt) được thiết kế tốt đến đâu cũng không thể cứu vãn được kết quả nếu dữ liệu nền tảng mà AI truy cập bị sai lệch, thiếu sót hoặc bị đầu độc. Chất lượng dữ liệu chính là "nguồn thức ăn" cho trí tuệ nhân tạo; thức ăn bẩn sẽ tạo ra kết quả tồi tệ bất kể phương pháp chế biến (prompting) có tinh vi đến mức nào.

---
