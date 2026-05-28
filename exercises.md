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
> Khi tăng giá trị temperature, câu trả lời của mô hình trở nên đa dạng, sáng tạo và khó đoán hơn. Với temperature = 0.0, phản hồi thường rất ổn định, ngắn gọn và mang tính chính xác cao; còn ở 1.0 và 1.5, mô hình có xu hướng dùng cách diễn đạt phong phú hơn, thêm chi tiết thú vị hoặc đôi khi lan man hơn.
**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Đối với chatbot hỗ trợ khách hàng, tôi sẽ chọn temperature khoảng 0.2 – 0.5. Mức này giúp câu trả lời ổn định, nhất quán và chính xác, tránh việc mô hình trả lời quá sáng tạo hoặc bịa thông tin. Đồng thời, nó vẫn giữ được sự tự nhiên trong hội thoại để phản hồi không quá cứng nhắc.*

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> GPT-4o đắt hơn GPT-4o-mini khoảng 16–17 lần cho workload này

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> GPT-4o đáng giá hơn khi cần chất lượng suy luận và độ chính xác cao, ví dụ: chatbot tư vấn pháp lý, phân tích tài liệu y tế, trợ lý lập trình phức tạp hoặc hệ thống AI xử lý nhiều bước suy luận. Trong các trường hợp này, việc giảm lỗi và tăng chất lượng phản hồi quan trọng hơn chi phí vận hành.
GPT-4o-mini phù hợp hơn cho các tác vụ số lượng lớn nhưng không yêu cầu suy luận quá sâu, như chatbot FAQ tuyển sinh, hỗ trợ khách hàng cơ bản, phân loại văn bản, tóm tắt ngắn hoặc auto-reply. Chi phí thấp giúp hệ thống dễ mở rộng cho hàng chục nghìn người dùng mỗi ngày.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> Streaming quan trọng nhất trong các ứng dụng cần phản hồi theo thời gian thực để cải thiện trải nghiệm người dùng, như chatbot hỗ trợ khách hàng, trợ lý AI, AI coding assistant hoặc ứng dụng voice AI, vì người dùng có thể thấy câu trả lời xuất hiện ngay thay vì phải chờ toàn bộ phản hồi hoàn thành. Điều này đặc biệt hữu ích khi câu trả lời dài hoặc mô hình xử lý chậm. Ngược lại, non-streaming phù hợp hơn khi hệ thống cần nhận toàn bộ kết quả một lần để xử lý tiếp, chẳng hạn như tạo JSON chuẩn, phân tích dữ liệu, gọi API backend, batch processing hoặc các workflow yêu cầu phản hồi hoàn chỉnh và ổn định trước khi hiển thị.



## Danh Sách Kiểm Tra Nộp Bài
- [ ] Tất cả tests pass: `pytest tests/ -v`
- [ ] `call_openai` đã triển khai và kiểm thử
- [ ] `call_openai_mini` đã triển khai và kiểm thử
- [ ] `compare_models` đã triển khai và kiểm thử
- [ ] `streaming_chatbot` đã triển khai và kiểm thử
- [ ] `retry_with_backoff` đã triển khai và kiểm thử
- [ ] `batch_compare` đã triển khai và kiểm thử
- [ ] `format_comparison_table` đã triển khai và kiểm thử
- [ ] `exercises.md` đã điền đầy
- [ ] Sao chép bài làm vào folder `solution` và đặt tên theo quy định 