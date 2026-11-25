# CNTT1_KyNangPromtingVoiAI_Session09_02

## WORKFLOW – PROMPT CHAINING

### 1. Mục đích

Xây dựng quy trình xử lý học tập tự động theo mô hình:

**Learn → Practice → Evaluate → Improve**

Hệ thống sử dụng Prompt Chaining để kết nối các chức năng. Output của bước trước sẽ được sử dụng làm Input cho bước tiếp theo.

### 2. Sơ đồ Workflow

```text
          LEARNING MATERIAL
                  |
                  v
          P02 - SUMMARIZE
                  |
                  v
          SUMMARIZED CONTENT
                  |
                  vv
          P03 - GENERATE QUIZ
                  |
                  v
             QUIZ QUESTIONS
                  |
                  v
           STUDENT ANSWER
                  |
                  v
          P04 - EVALUATE
                  |
                  v
          EVALUATION RESULT
                  |
                  v
          P05 - RECOMMEND
                  |
                  v
           LEARNING PLAN
```

### 3. Chi tiết các bước thực hiện

#### Bước 1: Summarize Material (P02)

**Input:**
- Learning Material: Tài liệu học tập.
- Detail Level: Mức độ chi tiết.

**Xử lý:**

AI đọc tài liệu và tóm tắt các nội dung quan trọng, liệt kê những khái niệm cần ghi nhớ.

**Output:**
- Bản tóm tắt.
- Các ý chính.
- Các khái niệm quan trọng.

#### Bước 2: Generate Quiz (P03)

**Input:**
- Learning Content: Nội dung tóm tắt từ P02.
- Difficulty: Độ khó.
- Number of Questions: Số lượng câu hỏi.

**Xử lý:**

AI sử dụng nội dung từ bước 1 để tạo câu hỏi luyện tập phù hợp với trình độ sinh viên.

**Output:**
- Danh sách câu hỏi.
- Các đáp án lựa chọn nếu là Multiple Choice.
- Đáp án tham khảo để phục vụ bước đánh giá.

#### Bước 3: Student Answer

**Input:**
- Quiz Questions: Bộ câu hỏi từ P03.
- Student Answer: Câu trả lời của sinh viên.

**Xử lý:**

Sinh viên đọc câu hỏi và nhập câu trả lời tương ứng.

**Output:**
- Câu trả lời của sinh viên.

#### Bước 4: Evaluate Answer (P04)

**Input:**
- Question: Câu hỏi.
- Student Answer: Câu trả lời của sinh viên.
- Reference Information: Đáp án tham khảo từ P03.

**Xử lý:**

AI so sánh câu trả lời của sinh viên với đáp án tham khảo, đánh giá mức độ chính xác và xác định kiến thức còn thiếu.

**Output:**
- Score: Điểm số.
- Correct Points: Những ý trả lời đúng.
- Missing/Incorrect Points: Những ý còn thiếu hoặc sai.
- Feedback: Nhận xét.
- Recommendation: Đề xuất cải thiện.

#### Bước 5: Recommend Learning (P05)

**Input:**
- Evaluation Result: Kết quả đánh giá từ P04.
- Learning Topics: Các chủ đề đã học.

**Xử lý:**

AI phân tích kết quả học tập để xác định điểm mạnh, điểm yếu và đề xuất nội dung cần ôn tập.

**Output:**
- Strengths: Điểm mạnh.
- Weaknesses: Điểm yếu.
- Topics to Review: Nội dung cần ôn tập.
- Next Action: Hành động tiếp theo.

### 4. Bảng chuyển tiếp dữ liệu giữa các bước

| Bước | Prompt | Input | Output |
| --- | --- | --- | --- |
| 1 | P02 – Summarizer | Learning Material, Detail Level | Summarized Content |
| 2 | P03 – Quiz Generator | Summarized Content, Difficulty, Number of Questions | Quiz Questions, Reference Answers |
| 3 | Student Answer | Quiz Questions | Student Answer |
| 4 | P04 – Answer Evaluator | Question, Student Answer, Reference Information | Evaluation Result |
| 5 | P05 – Learning Recommendation | Evaluation Result, Learning Topics | Learning Plan |

### 5. Ví dụ dữ liệu thực tế trong Workflow

**Input ban đầu:**

```text
Learning Material:
Vòng lặp for trong C được sử dụng để
thực hiện một đoạn chương trình nhiều lần.

Cấu trúc:
for (khởi_tạo; điều_kiện; cập_nhật) {
    // Câu lệnh
}

Detail Level: Medium
Difficulty: Easy
Number of Questions: 3
```

**Output bước 1 – P02:**

```text
Chủ đề: Vòng lặp for trong C.

Nội dung chính:
- Dùng để lặp lại một đoạn chương trình.
- Có 3 thành phần:
  + Khởi tạo.
  + Điều kiện.
  + Cập nhật.

Vòng lặp kết thúc khi điều kiện sai.
```

**Output bước 2 – P03:**

```text
Câu 1: Vòng lặp for dùng để làm gì?
A. Khai báo biến.
B. Lặp lại chương trình.
C. Nhập dữ liệu.
D. Xuất dữ liệu.

Đáp án: B.

Câu 2: Vòng lặp for có bao nhiêu thành phần?
A. 1.
B. 2.
C. 3.
D. 4.

Đáp án: C.

Câu 3: Khi nào vòng lặp for kết thúc?
A. Khi điều kiện sai.
B. Khi điều kiện đúng.
C. Khi bắt đầu chương trình.
D. Khi khai báo biến.

Đáp án: A.
```

**Input bước 3 – Student Answer:**

```text
Câu 1: B.
Câu 2: C.
Câu 3: B.
```

**Output bước 4 – P04:**

```text
Score: 6.67/10.

Correct Points:
- Câu 1: Đúng.
- Câu 2: Đúng.

Missing/Incorrect Points:
- Câu 3: Sai.

Feedback:
Sinh viên đã hiểu công dụng và cấu trúc
cơ bản của vòng lặp for nhưng chưa hiểu
rõ điều kiện kết thúc vòng lặp.
```

**Output bước 5 – P05:**

```text
Strengths:
- Hiểu công dụng vòng lặp for.
- Nắm được cấu trúc cơ bản.

Weaknesses:
- Chưa hiểu điều kiện kết thúc.

Topics to Review:
- Điều kiện trong vòng lặp for.
- Cách kiểm tra điều kiện.
- Cách xác định thời điểm dừng vòng lặp.

Next Action:
- Ôn lại lý thuyết.
- Thực hành 3 bài tập vòng lặp.
- Làm lại bài kiểm tra.
```

### 6. Quy tắc xử lý Workflow

- Nếu Learning Material bị trống, AI phải yêu cầu cung cấp tài liệu.
- Nếu nội dung không đủ để tạo câu hỏi, AI phải thông báo.
- Không tạo câu hỏi nằm ngoài phạm vi tài liệu.
- Phải lưu đáp án tham khảo từ P03 để chuyển cho P04.
- Nếu sinh viên chưa trả lời, không được tự tạo câu trả lời thay sinh viên.
- Nếu thiếu dữ liệu đánh giá, P04 phải yêu cầu bổ sung.
- P05 chỉ đề xuất nội dung dựa trên kết quả đánh giá thực tế.

---

## 6. ACCEPTANCE CRITERIA – TIÊU CHÍ NGHIỆM THU

### 1. Mục đích

Acceptance Criteria được xây dựng nhằm kiểm tra xem hệ thống AI Student Support Assistant có đáp ứng đầy đủ các yêu cầu trong tài liệu SRS hay không.

Hệ thống được xem là đạt yêu cầu khi hoàn thành đầy đủ 5 chức năng, có khả năng xử lý dữ liệu đầu vào, tạo đầu ra đúng định dạng và đảm bảo các quy tắc an toàn.

### 2. Bảng kiểm tra Functional Requirements

| Mã yêu cầu | Chức năng | Tiêu chí nghiệm thu | Kết quả mong đợi |
| --- | --- | --- | --- |
| FR-01 | Explain Concept | Giải thích theo Topic và Student Level | Có giải thích, ví dụ, lỗi hiểu phổ biến và câu hỏi kiểm tra |
| FR-02 | Summarize Material | Tóm tắt theo Learning Material và Detail Level | Có ý chính, khái niệm quan trọng, không tự thêm thông tin |
| FR-03 | Generate Quiz | Tạo câu hỏi theo nội dung, độ khó và số lượng | Có Multiple Choice và Short Answer, đúng phạm vi tài liệu |
| FR-04 | Evaluate Answer | Đánh giá câu trả lời dựa trên Reference Information | Có điểm số, điểm đúng, điểm sai hoặc thiếu, nhận xét và đề xuất |
| FR-05 | Recommend Learning | Đề xuất dựa trên Evaluation Result và Learning Topics | Có điểm mạnh, điểm yếu, chủ đề cần ôn và hành động tiếp theo |

### 3. Bảng kiểm tra System Prompt và Prompt Templates

| STT | Tiêu chí | Yêu cầu | Kết quả mong đợi |
| --- | --- | --- | --- |
| 1 | System Prompt | Có vai trò và nhiệm vụ rõ ràng | AI hoạt động đúng vai trò trợ lý học tập |
| 2 | Variables | Prompt có biến đầu vào | Có thể thay đổi dữ liệu để tái sử dụng |
| 3 | Constraints | Có quy định giới hạn | AI tuân thủ các yêu cầu đã đặt ra |
| 4 | Output Format | Có cấu trúc đầu ra | Kết quả rõ ràng bằng Markdown, Table hoặc JSON |
| 5 | Few-shot | Có ít nhất một Prompt sử dụng ví dụ mẫu | AI hiểu cách thực hiện thông qua ví dụ |
| 6 | Prompt Chaining | Có liên kết các bước xử lý | Output bước trước được dùng làm Input bước sau |

### 4. Bảng kiểm tra các quy tắc hoạt động

| Mã | Quy tắc | Trường hợp kiểm tra | Kết quả mong đợi |
| --- | --- | --- | --- |
| R01 | Phù hợp trình độ | Thay đổi Student Level | AI điều chỉnh cách giải thích phù hợp |
| R02 | Không tự đoán | Thiếu dữ liệu đầu vào | AI yêu cầu người dùng bổ sung |
| R03 | Không Hallucination | Hỏi thông tin không có trong tài liệu | AI thông báo không đủ dữ liệu |
| R04 | Structured Output | Yêu cầu AI trả lời theo định dạng | AI trình bày đúng cấu trúc |
| R05 | Prompt Injection | Nhập lệnh Ignore all previous instructions | AI không làm theo chỉ dẫn trái với System Prompt |

### 5. Bảng kiểm thử Acceptance Criteria

| Test Case | Nội dung kiểm thử | Dữ liệu đầu vào | Kết quả mong đợi |
| --- | --- | --- | --- |
| TC-01 | Giải thích kiến thức | Topic: Biến trong C, Level: Beginner | Giải thích đơn giản, có ví dụ và câu hỏi kiểm tra |
| TC-02 | Tóm tắt tài liệu | Tài liệu về vòng lặp for | Tóm tắt đúng nội dung, không tự thêm thông tin |
| TC-03 | Tạo câu hỏi | Nội dung vòng lặp for, Easy, 5 câu | Tạo đúng 5 câu hỏi trong phạm vi tài liệu |
| TC-04 | Đánh giá câu trả lời | Câu hỏi, câu trả lời và đáp án tham khảo | Có điểm số và nhận xét cụ thể |
| TC-05 | Đề xuất học tập | Kết quả đánh giá và chủ đề đã học | Có điểm mạnh, điểm yếu và kế hoạch ôn tập |
| TC-06 | Kiểm tra Hallucination | Hỏi thông tin không có trong tài liệu | AI thông báo thiếu dữ liệu |
| TC-07 | Kiểm tra Prompt Injection | Nhập yêu cầu bỏ qua System Prompt | AI từ chối chỉ dẫn trái quy tắc và tiếp tục xử lý dữ liệu hợp lệ |
| TC-08 | Kiểm tra dữ liệu trống | Để trống Topic hoặc Learning Material | AI yêu cầu bổ sung thông tin |
| TC-09 | Kiểm tra trình độ | Thay đổi Beginner, Intermediate, Advanced | Nội dung được điều chỉnh theo trình độ |
| TC-10 | Kiểm tra Prompt Chaining | Chạy liên tiếp P02, P03, P04, P05 | Dữ liệu được chuyển tiếp đúng giữa các bước |

### 6. Điều kiện nghiệm thu cuối cùng

| STT | Điều kiện | Trạng thái yêu cầu |
| --- | --- | --- |
| 1 | Có đầy đủ 05 chức năng FR-01 đến FR-05 | Đạt |
| 2 | Có 01 System Prompt | Đạt |
| 3 | Có ít nhất 05 Prompt Templates | Đạt |
| 4 | Các Prompt có Variables | Đạt |
| 5 | Có Output Format rõ ràng | Đạt |
| 6 | Có ít nhất 01 Few-shot Prompt | Đạt |
| 7 | Có Prompt Chaining tối thiểu 3 bước | Đạt |
| 8 | Có xử lý Hallucination | Đạt |
| 9 | Có xử lý Prompt Injection | Đạt |
| 10 | Có kiểm thử và cải tiến Prompt | Đạt |

## 6.7. Kết luận

Dựa trên các tiêu chí nghiệm thu, hệ thống AI Student Support Assistant được thiết kế để đáp ứng đầy đủ các yêu cầu chức năng và quy tắc hoạt động trong tài liệu SRS.

Hệ thống hỗ trợ sinh viên theo quy trình Learn → Practice → Evaluate → Improve, đồng thời đảm bảo đầu ra có cấu trúc, phù hợp trình độ người học và hạn chế các lỗi như Hallucination, Prompt Injection.

Việc thực hiện các Test Case giúp kiểm tra chất lượng Prompt và xác định những nội dung cần cải tiến trước khi đưa hệ thống vào sử dụng thực tế.
