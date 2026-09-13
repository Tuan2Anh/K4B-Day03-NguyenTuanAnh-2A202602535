# 📊 BÁO CÁO THU HOẠCH NGHIỆM THU BÀI LAB 3 (BƯỚC 3 — SUBMISSION ARTIFACT)

> **Họ và Tên Học viên:** Nguyễn Tuấn Anh  
> **Mã Sinh Viên / Mã Học viên:** 2A202602535  
> **Chủ đề Lựa chọn:** Gợi ý 1.1: Trợ lý Học vụ & Tra cứu Lịch thi VinUni (VinUni Academic Assistant)  

---

## 1. BẢNG CHẤM ĐIỂM AGENTIC FIT SCORING MATRIX (ĐÁNH GIÁ CHỦ ĐỀ)

| Tiêu chí Đánh giá | Mức độ (1 - 5) | Giải trình chi tiết lý do chọn điểm |
| :--- | :---: | :--- |
| **1. Multi-step Reasoning** | 4 / 5 | Phân tách rõ ràng giữa câu hỏi quy chế học vụ chung (trả lời trực tiếp từ LLM) và yêu cầu tra cứu/đặt lịch hẹn cố vấn học tập (kích hoạt chuỗi ReAct). |
| **2. Tool Interaction** | 5 / 5 | Bắt buộc phải kết nối CSDL học vụ thời gian thực qua giao thức MCP Server để thực thi các tool `academic_query` và `schedule_appointment`. |
| **3. Dynamic Decision** | 4 / 5 | Bước tiếp theo phụ thuộc vào kết quả Observation: nếu sinh viên tồn tại thì tổng hợp thông tin, nếu NOT_FOUND thì xử lý cảnh báo lịch sự, chống ảo giác. |
| **4. Long Horizon Goal** | 4 / 5 | Duy trì mục tiêu xuyên suốt qua nhiều bước ReAct (Thought -> Action -> Observation -> Final Answer) để giải quyết trọn vẹn yêu cầu học vụ của sinh viên. |
| **TỔNG ĐIỂM AGENTIC FIT** | **17 / 20** | *Nếu tổng điểm > 12/20: Bài toán rất phù hợp triển khai Agentic System.* |

---

## 2. TRÍCH XUẤT KẾT QUẢ WATERFALL TRACE LOG (SAU KHI CHẠY TEST SUITE TRÊN API THẬT)

> ⚠️ **YÊU CẦU NGHIỆM THU:** Mở tệp `.env` điền `GEMINI_API_KEY` (hoặc `OPENAI_API_KEY`) để kết nối LLM thật trước khi thực thi `python src/app.py --all`. Bài nộp chỉ dùng Mock Offline Provider sẽ không đạt điểm nghiệm thực tế.

Dán 1 đoạn trích xuất log tiêu biểu từ file `docs/trace_waterfall.json` sinh ra từ phản hồi LLM API thật:

```json
[
  {
    "step": 1,
    "query": "Hãy đặt lịch hẹn tư vấn học vụ cho sinh viên SV2026001 vào lúc 14:00 ngày 15/09/2026 với PGS.TS Nguyễn Văn A.",
    "action_type": "TOOL_EXECUTION",
    "tool_name": "schedule_appointment",
    "arguments": {
      "advisor_name": "PGS.TS Nguyễn Văn A",
      "datetime_str": "2026-09-15T14:00",
      "student_id": "SV2026001"
    },
    "observation": {
      "status": "SUCCESS",
      "booking_id": "BK-SV2026001-99",
      "student_id": "SV2026001",
      "datetime": "2026-09-15T14:00",
      "advisor": "PGS.TS Nguyễn Văn A",
      "message": "Đặt lịch thành công cho sinh viên SV2026001 với PGS.TS Nguyễn Văn A vào lúc 2026-09-15T14:00."
    },
    "latency_ms": 1365.49
  },
  {
    "step": 2,
    "query": "Hãy đặt lịch hẹn tư vấn học vụ cho sinh viên SV2026001 vào lúc 14:00 ngày 15/09/2026 với PGS.TS Nguyễn Văn A.",
    "action_type": "FINAL_ANSWER",
    "thought": "Tổng hợp kết quả từ MCP Server thành công.",
    "output": "Đặt lịch thành công cho sinh viên SV2026001 với PGS.TS Nguyễn Văn A vào lúc 2026-09-15T14:00.",
    "latency_ms": 10.0
  }
]
```

---

## 3. TỔNG KẾT KẾT QUẢ NGHIỆM THU & NỘP BÀI

- [x] Đã điền API Key thật trong `.env` và xác nhận Agent chạy mượt mà trên LLM API thật (OpenAI SDK / `openai/gpt-oss-20b`).
- **Tổng số Test Cases đã chạy thành công:** 5 / 5 test cases.
- **Số lượt gọi Tool qua MCP Server chính xác:** 4 lượt (TC02, TC03, TC04, TC05).
- **Kết quả đẩy Repo nộp bài:** [x] Đã Commit và Push mã nguồn thành công lên GitHub cá nhân.

---

> ✅ **HOÀN TẤT NỘP BÀI:** Sao chép đường link GitHub Repository cá nhân của bạn và dán vào ô nộp bài trên hệ thống LMS VLearn để hoàn tất Bài Lab 3!

