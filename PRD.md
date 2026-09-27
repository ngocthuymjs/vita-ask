# PRD - Vita Ask (ChatGPT for Company)

## 1. Ý tưởng (1 câu)
Web chat giống ChatGPT cho team công ty: hỏi đáp thường thức + hỏi đáp thông tin nội bộ (chính sách, lương thưởng phúc lợi, số lượng nhân viên).

## 2. Ai dùng
- Team công ty (nhiều user, có login)
- Mỗi user lưu lịch sử chat + project riêng

## 3. Tính năng chính (v1)
1. Chat hỏi đáp thường thức (giống ChatGPT)
2. Chat hỏi đáp công ty (lấy từ knowledge base cloud)
3. Change model (v1 giả lập: GPT-4o, Claude, Vita-Internal...)
4. Projects: tạo project riêng, chat trong project
5. Đính kèm file (PDF, Word, ảnh) để hỏi + soạn thảo văn bản
6. Soạn thảo / chỉnh văn bản (AI rewrite)
7. Admin upload tài liệu lên cloud knowledge base
8. Login / quản lý user cơ bản

## 4. Knowledge base
- User upload lên cloud, chatbot lấy từ đó trả lời
- v1: giả lập cloud (mock), v2 gắn thật

## 5. Model
- v1 giả lập trước (mock response), UI đổi model đầy đủ
- v2 gắn API thật

## 6. Không làm trong v1
- Thanh toán, phân quyền phức tạp, app mobile
