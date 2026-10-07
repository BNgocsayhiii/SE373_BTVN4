---
name: refund-policy
description: Trả lời câu hỏi về điều kiện hoàn tiền (có được hoàn không, thời hạn, phí hoàn) dựa trên các tài liệu chính sách hoàn tiền trong workspace. Dùng khi người dùng hỏi về hoàn tiền kèm ngày mua hoặc ngày yêu cầu hoàn.
---

# Quy trình

1. Kiểm tra câu hỏi có đủ 3 thông tin: ngày mua, ngày yêu cầu hoàn, trạng thái kích hoạt.
   Thiếu thông tin nào thì hỏi lại người dùng và dừng ở đó. Không tự giả định, không kết luận.
2. Dùng list_files với data/policies để tìm các tài liệu chính sách. Không dựa vào tên file để chọn chính sách.
3. Dùng read_file đọc từng tài liệu tìm được. Chú ý phạm vi hiệu lực (ngày áp dụng) ở đầu mỗi tài liệu.
4. Chọn đúng một chính sách có phạm vi hiệu lực chứa ngày mua. Chú ý "bao gồm ngày này" ở mốc bắt đầu.
5. Tính số ngày đã qua = chênh lệch ngày lịch giữa ngày yêu cầu hoàn và ngày mua.
   Ngày trong câu hỏi viết theo dạng ngày/tháng/năm. Dùng các ngày trong câu hỏi, không dùng ngày hiện tại.
   Số ngày bằng đúng giới hạn vẫn đủ điều kiện về thời gian.
6. Kiểm tra thời hạn và điều kiện kích hoạt theo chính sách đã chọn, rồi kết luận.
7. Dùng read_file đọc skills/refund-policy/references/answer-template.md và trả lời đúng theo mẫu đó.