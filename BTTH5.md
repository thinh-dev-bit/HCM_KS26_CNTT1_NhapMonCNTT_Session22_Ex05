# BÁO CÁO THIẾT KẾ QUY TRÌNH TROUBLESHOOTING & BUG REPORT (SESSION 22)

Để giải quyết triệt để tình trạng "spam" tin nhắn báo lỗi lẻ tẻ làm trôi thông tin quan trọng trên nhóm chat của Startup, dưới đây là bộ quy chuẩn vận hành bắt buộc dành cho toàn bộ thành viên khối Kỹ thuật.

---

## Phần 1: Quy trình 3 Bước Tra cứu Bắt buộc (Self-Solve Workflow)

Mục tiêu của quy trình này là ép buộc các thành viên phải tự rà soát và xử lý **80% các lỗi vặt (Docker, Port conflict...)** một cách độc lập trước khi đẩy sự cố lên nhóm chung. Quy tắc: Chỉ được phép nhờ hỗ trợ nếu đã thực hiện đủ 3 bước dưới đây trong vòng 15-20 phút mà vẫn bế tắc.

### 🔄 Bước 1: Tối ưu hóa Tìm kiếm (Googling)
*   **Hành động:** Ngay khi Terminal/phần mềm văng lỗi, cấm tuyệt đối việc gõ câu hỏi văn nói (VD: *"Tại sao Docker của em không chạy?"*).
*   **Thực thi:** Bóc tách thông báo lỗi thành 3 thành phần (Công cụ + Mã lỗi nguyên văn + Hệ điều hành) và áp dụng "Combo toán tử" Google.
    *   *Ví dụ:* `site:stackoverflow.com "port 8080 is already in use" docker windows 11`

### 🔄 Bước 2: Thẩm định Cộng đồng (Community Search)
*   **Hành động:** Truy cập vào kết quả từ StackOverflow hoặc GitHub Issues. Không ngồi dịch toàn bộ câu hỏi.
*   **Thực thi:** Áp dụng "Quy tắc đọc lướt 30s".
    *   Cuộn thẳng xuống phần **Answers**.
    *   Ưu tiên lấy lệnh từ các bình luận có **Tích xanh (Accepted Answer)** hoặc **Lượt Upvote cao**.
    *   Trên GitHub, tìm các đoạn code Workaround có nhiều thả tim (❤️, 👍) và có bình luận *"This works!"* gần đây.

### 🔄 Bước 3: Giải mã bằng AI (AI Translation & Decoding)
*   **Hành động:** Nếu đọc StackOverflow vẫn không hiểu cách sửa, sử dụng Trợ lý AI (ChatGPT/Gemini) để dịch lỗi sang tiếng Việt.
*   **Thực thi:** Gửi câu lệnh theo đúng **Công thức Prompt 3 Thành phần**:
    1.  **[Context]:** *"Tôi đang chạy Docker trên Windows 11..."*
    2.  **[Raw Error]:** *"Terminal báo lỗi nguyên văn: bind: address already in use..."*
    3.  **[Instruction]:** *"Hãy giải thích nguyên nhân bằng tiếng Việt và cho tôi 3 bước khắc phục tại chỗ."*
    *   *(⚠️ **Lưu ý bảo mật:** Bắt buộc phải bôi đen hoặc thay thế các thông tin như `API_KEY`, mật khẩu Database thành dấu `***` trước khi dán lên AI).*

---

## Phần 2: Mẫu Bug Report Template Chuẩn (Khung 4 Mảnh Ghép)

Nếu đã hoàn tất 3 bước tự tra cứu trên nhưng sự cố vẫn chưa được giải quyết, thành viên mới được phép gửi yêu cầu hỗ trợ lên nhóm Zalo/Slack/Telegram. 

Tuy nhiên, **nghiêm cấm nhắn tin cụt ngủn**. Mọi tin nhắn báo lỗi bắt buộc phải điền theo đúng **Form 4 mảnh ghép** dưới đây để Senior Dev nắm bắt bối cảnh ngay lập tức trong vòng 1 phút.

### 📋 Biểu mẫu Copy & Paste (Dành cho thành viên):

```text
🚨 [YÊU CẦU HỖ TRỢ KỸ THUẬT] 🚨

1. [CONTEXT - Bối cảnh]
- Hệ điều hành & Thiết bị: (VD: Windows 11 / macOS Sonoma)
- Phần mềm/Môi trường đang chạy: (VD: Docker Desktop 4.25, Node.js 18)
- Tôi đang thao tác chức năng gì: (VD: Khởi động container Database)

2. [EXPECTED - Kỳ vọng]
- (VD: Tôi mong muốn lệnh `docker-compose up` chạy thành công và mở cổng 3306).

3. [ACTUAL - Thực tế phát sinh]
- (VD: Terminal báo lỗi xung đột cổng mạng, container bị thoát ngay lập tức với Exit Code 1. Tôi đã thử tìm trên StackOverflow và dùng lệnh `netstat` để tìm tiến trình nhưng vẫn không tắt được).

4. [LOG & SCREENSHOT - Bằng chứng]
- Lỗi nguyên văn: "..."
- Ảnh chụp màn hình: (Đính kèm ảnh chụp bằng tổ hợp phím Win + Shift + S, đã khoanh đỏ chỗ bị lỗi và che thông tin bảo mật).