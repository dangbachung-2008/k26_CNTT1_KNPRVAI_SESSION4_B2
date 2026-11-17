# [Vận dụng cơ bản 2] Khắc phục lỗi khai báo biến số trong prompt mẫu

### **Bước 1: Phân tích lỗi**

-  **Tính không nhất quán về cú pháp (Syntax Inconsistency):** Prompt gốc sử dụng hai loại dấu ngoặc khác nhau để khai báo biến là ngoặc vuông `[language]` và ngoặc nhọn `{audience}`.
    
-  **Khó khăn cho việc tự động hóa (Automation/Parsing):** Khi đưa vào các công cụ tự động hóa (như kịch bản Python, Zapier, Make hoặc hàm thay thế chuỗi `replace`), hệ thống thường chỉ quét theo một quy tắc định dạng duy nhất (ví dụ chỉ tìm các cụm nằm trong `[...]`). Việc trộn lẫn hai kiểu ngoặc khiến hệ thống bỏ sót biến hoặc thay thế sai, đồng thời làm AI dễ nhầm lẫn biến chưa gán giá trị với văn bản thông thường.
    
-   **Khả năng đọc hiểu kém:** Tên biến viết thường, tiếng Anh lẫn tiếng Việt khiến người dùng khó nhận diện nhanh đâu là phần dữ liệu cần điền động.
    

### Bước 2: Đồng bộ biến số
Đưa toàn bộ về một chuẩn duy nhất là ngoặc vuông, viết hoa, tiếng Việt:

> _Prompt mẫu sau khi đồng bộ:_ "Hãy viết một bài chia sẻ về Kỹ thuật Prompting Nâng cao (Logic & Chuỗi) bằng ngôn ngữ `[NGÔN_NGỮ]`. Dành cho đối tượng `[ĐỐI_TƯỢNG]`."

### **Bước 3: Kết quả chạy thử thực tế**

-   **Dữ liệu điền vào:**  `[NGÔN_NGỮ]` = Tiếng Việt | `[ĐỐI_TƯỢNG]` = Sinh viên CNTT năm nhất
    
-   **Prompt sau khi điền:**
    
    > "Hãy viết một bài chia sẻ về Kỹ thuật Prompting Nâng cao (Logic & Chuỗi) bằng ngôn ngữ Tiếng Việt. Dành cho đối tượng Sinh viên CNTT năm nhất."
    
-   **Đầu ra từ AI (Kết quả mẫu):**
    
    > _"Chào các tân sinh viên CNTT! Để tối ưu hóa việc làm việc với AI, hãy áp dụng hai kỹ thuật cốt lõi: **Chain-of-Thought** (ép AI suy nghĩ từng bước logic trước khi đưa ra đáp án để tránh ảo giác) và **Prompt Chaining** (chia nhỏ bài toán lớn thành nhiều bước liên tiếp). Hãy thực hành ngay từ hôm nay để biến AI thành trợ lý lập trình đắc lực của bạn!"_
