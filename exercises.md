# Ngày 1 — Bài Tập & Phản Ánh
## Nền Tảng LLM API | Phiếu Thực Hành

**Thời lượng:** 1:30 giờ  
**Cấu trúc:** Lập trình cốt lõi (60 phút) → Bài tập mở rộng (30 phút)

---

## Phần 1 — Lập Trình Cốt Lõi (0:00–1:00)

Chạy các ví dụ trong Google Colab tại: https://colab.research.google.com/drive/172zCiXpLr1FEXMRCAbmZoqTrKiSkUERm?usp=sharing

Triển khai tất cả TODO trong `template.py`. Chạy `pytest tests/` để kiểm tra tiến độ.

**Điểm kiểm tra:** Sau khi hoàn thành 4 nhiệm vụ, chạy:
```bash
python template.py
```
Bạn sẽ thấy output so sánh phản hồi của GPT-4o và GPT-4o-mini.

---

## Phần 2 — Bài Tập Mở Rộng (1:00–1:30)

### Bài tập 2.1 — Độ Nhạy Của Temperature
Gọi `call_openai` với các giá trị temperature 0.0, 0.5, 1.0 và 1.5 sử dụng prompt **"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**

**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2–3 câu)
> Khi temperature = 0.0, phản hồi rất nhất quán, chính xác và ít sáng tạo; temperature = 0.5 cho câu trả lời cân bằng giữa chính xác và sáng tạo; temperature = 1.0 làm tăng tính đa dạng và sáng tạo; temperature = 1.5 thường tạo ra các câu trả lời bất ngờ hơn nhưng có thể kém chính xác hơn.

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Tôi sẽ đặt temperature thấp (ví dụ 0.0–0.2) cho chatbot hỗ trợ khách hàng để đảm bảo tính nhất quán, độ chính xác và tránh tạo ra thông tin gây nhầm lẫn.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> Tính toán sơ bộ: tổng tokens/ngày = 10.000 * 3 * 350 = 10.500.000 tokens/ngày (≈10.500 nhóm 1k token). Nếu giả sử (ví dụ) giá GPT-4o là $0.030/1k token và GPT-4o-mini là $0.006/1k token thì GPT-4o sẽ đắt gấp ~5 lần. Với workload này, chi phí hàng ngày lần lượt sẽ xấp xỉ $315 (GPT-4o) so với $63 (GPT-4o-mini). Lưu ý: con số phụ thuộc vào giá thực tế — phương pháp trên cho bạn cách ước tính.

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> GPT-4o xứng đáng khi cần đầu ra cực kỳ chính xác, phức tạp hoặc chuyên sâu (ví dụ: soạn thảo pháp lý, phân tích y tế) nơi sai sót có chi phí cao. GPT-4o-mini phù hợp cho các tác vụ quy mô lớn mà yêu cầu tính năng thông tin cơ bản hoặc tương tác nhanh với chi phí thấp (ví dụ chatbot hỗ trợ cơ bản, phân loại nội dung, tóm tắt ngắn).

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> Streaming quan trọng khi người dùng mong đợi phản hồi tức thì hoặc khi phản hồi dài (ví dụ: trợ lý hội thoại theo thời gian thực, viết nội dung dài, công cụ hỗ trợ code) vì nó giảm độ trễ cảm nhận và cho phép hiển thị dần. Non-streaming phù hợp khi cần phản hồi toàn bộ, nguyên vẹn và có thể xử lý batch dễ dàng (ví dụ: tạo báo cáo hoàn chỉnh, xử lý đơn lẻ không cần hiển thị tức thì), hoặc khi việc triển khai streaming quá phức tạp so với lợi ích.


## Danh Sách Kiểm Tra Nộp Bài
- [ ] Tất cả tests pass: `pytest tests/ -v`
- [ ] `call_openai` đã triển khai và kiểm thử
- [ ] `call_openai_mini` đã triển khai và kiểm thử
- [ ] `compare_models` đã triển khai và kiểm thử
- [ ] `streaming_chatbot` đã triển khai và kiểm thử
- [ ] `retry_with_backoff` đã triển khai và kiểm thử
- [ ] `batch_compare` đã triển khai và kiểm thử
- [ ] `format_comparison_table` đã triển khai và kiểm thử
- [x] `exercises.md` đã điền đầy đủ
- [ ] Sao chép bài làm vào folder `solution` và đặt tên theo quy định 
