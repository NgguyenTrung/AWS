---
title: "Event 1"
date: 2026-05-23
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---


# Bài thu hoạch: AWS Cloud AI Journey – Community Day (Conference Call)

### 1. Mục đích tham gia sự kiện
Là một người đang học tập và nghiên cứu trong lĩnh vực Công nghệ thông tin, việc tiếp cận với các xu hướng Cloud và AI thực tế là cực kỳ cần thiết. Tôi tham gia sự kiện **AWS Community Day** lần này với các mục tiêu lớn:
- Tìm hiểu cách tối ưu hóa sức mạnh của các mô hình AI (LLM) thông qua việc quản lý ngữ cảnh (Context) và xây dựng quy trình làm việc (Workflow) thực tế.
- Học hỏi kinh nghiệm thực chiến từ các bạn sinh viên/lập trình viên khác thông qua các dự án Hackathon chạy đua với thời gian (như dự án UTMorpho tại LotusHacks).
- Cập nhật các kiến thức hạ tầng Cloud hiện đại của AWS, đặc biệt là cơ chế tăng tốc, bảo mật ở lớp Edge (Amazon CloudFront) và các giải pháp AI trợ lý doanh nghiệp thế hệ mới (Amazon Q, Amazon QuickSight).

---

### 2. Những nội dung ấn tượng và trải nghiệm thực tế

#### 🔹 Context Is Everything: Câu chuyện đưa AI vào thực tế
Phiên chia sẻ này làm tôi thay đổi khá nhiều về tư duy làm Prompt. Diễn giả đã chứng minh rất rõ: AI chỉ thực sự thông minh khi được cung cấp đầy đủ "ngữ cảnh" (Context) và "bộ nhớ" (Memory). Nếu chỉ ném cho AI một câu lệnh trống không, kết quả nhận về sẽ rất chung chung. Khái niệm **“Second AI Brain”** được giới thiệu trong buổi call giúp tôi hiểu ra cách xây dựng một hệ thống trợ lý biết tự học và hiểu nhu cầu của người dùng theo thời gian.

#### 🔹 Trải nghiệm 36 giờ tại LotusHacks – Từ Ý tưởng đến sản phẩm UTMorpho
Đây là phần chia sẻ mang lại nhiều năng lượng nhất cho tôi. Nghe diễn giả kể về hành trình ăn ngủ cùng code, áp lực hoàn thiện dự án **UTMorpho** chỉ trong 36 giờ ngắn ngủi giúp tôi rút ra bài học lớn: Trong các kỳ cuộc ngắn hạn (Sprint/Hackathon), kỹ năng làm việc nhóm, việc dám buông bỏ các tính năng phụ để tập trung vào Core Value (giá trị cốt lõi) và khả năng ra quyết định nhanh mới là thứ quyết định sự sống còn của dự án.

#### 🔹 Hạ tầng cốt lõi: Tối ưu từ Edge đến Origin với Amazon CloudFront
Ở phần này, tôi được tiếp cận góc nhìn hạ tầng sâu hơn. **Amazon CloudFront** không đơn thuần chỉ là một dịch vụ CDN để cache ảnh hay video thông thường. Diễn giả đã phân tích sâu về vai trò của nó như một "tấm khiên" bảo mật ở vòng ngoài cùng, kết hợp với AWS WAF để chặn các cuộc tấn công, đồng thời giúp giảm tải đáng kể chi phí cho các server gốc (Origin) ở phía sau. 

#### 🔹 Trợ lý AI thế hệ mới: Trải nghiệm hệ sinh thái Amazon Q & QuickSight
Một trong những phần demo cuốn hút nhất là cách AWS đưa Generative AI vào hỗ trợ công việc hàng ngày qua các công cụ:
- **Amazon Q (Developer/Business):** Trợ lý đắc lực giúp code, tạo các luồng tự động hóa bằng ngôn ngữ tự nhiên (Quick Flows) và thiết kế không gian làm việc chung (Quick Spaces).
- **Amazon QuickSight:** Công cụ Business Intelligence cực mạnh, tích hợp AI cho phép người dùng chỉ cần gõ câu hỏi bằng ngôn ngữ tự nhiên là hệ thống tự động quét data thô và vẽ ra các biểu đồ (Dashboard) phân tích cực kỳ trực quan.

#### 🔹 Bản chất của AI: Tính "Không xác định" (Non-Determinism) của LLM
Đây là kiến thức kỹ thuật tôi thấy tâm đắc nhất. Trước đây tôi cứ nghĩ nếu chỉnh tham số `temperature = 0` thì AI sẽ luôn trả ra một kết quả duy nhất cho cùng một câu hỏi (Mang tính Deterministic). Tuy nhiên, các chuyên gia AWS đã "bóc trần" rằng do cấu trúc tính năng ở tầng hệ thống (Inference) và phần cứng, LLM vẫn có xác suất trả ra kết quả khác nhau. Điều này nhắc nhở các nhà phát triển phải luôn có chiến lược kiểm thử và thiết lập các Guardrails (hàng rào bảo vệ) thật chặt chẽ.

---

### 3. Bài học cốt lõi tôi rút ra được

- **Làm chủ Prompt là làm chủ ngữ cảnh:** Đừng mong đợi AI chạy tốt nếu mình không cung cấp đủ dữ liệu nền tảng và mục tiêu rõ ràng.
- **Tư duy MVP (Minimum Viable Product):** Khi làm sản phẩm công nghệ dưới áp lực thời gian, hãy tập trung giải quyết triệt để một bài toán nhức nhối trước, thay vì ôm đồm rồi không hoàn thiện được gì.
- **Kiến trúc Cloud phải toàn diện:** Một hệ thống tốt không chỉ cần chạy được, mà phải đáp ứng đồng thời 4 yếu tố: Tốc độ (Performance), Bảo mật (Security), Độ tin cậy (Reliability) và Tối ưu hóa chi phí (Cost Optimization).
- **Ứng dụng Multi-Agent trong doanh nghiệp:** Xu hướng tương lai không còn là một con Chatbot đơn độc, mà là sự phối hợp của nhiều Agent (mỗi con đảm nhận một vai trò: kế toán, kỹ thuật, chấm điểm tín dụng...) dưới sự giám sát chặt chẽ về mặt Compliance (tuân thủ).

---

### 4. Một số hình ảnh tôi ghi lại khi tham gia sự kiện


![Hình ảnh diễn giả chia sẻ slide kiến trúc](/images/4-Event/Event1.1.png)
![Giao diện demo tính năng trợ lý ảo Amazon Q](/images/4-Event/Event1.2.png)
![Slide phân tích tính Non-Determinism của LLM](/images/4-Event/Event1.3.png)
![Sơ đồ phân phối dữ liệu qua Amazon CloudFront](/images/4-Event/Event1.4.png)
![Hình ảnh toàn cảnh buổi call cùng cộng đồng AWS](/images/4-Event/Event1.5.png)

> **Tóm lại:** Buổi Community Day này không chỉ cho em kiến thức sách vở, mà nó mang lại những bài học "xương máu" từ thực tế triển khai của các chuyên gia. Những góc nhìn về bảo mật của CloudFront, sự bất ổn định của LLM hay sức mạnh của Amazon Q chắc chắn sẽ là những chất liệu cực tốt để tôi áp dụng trực tiếp vào các bài tập lớn và dự án cá nhân sắp tới của mình.