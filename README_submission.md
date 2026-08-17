# Báo cáo thực hiện Lab 17: Multi-Memory Agent với Zep

## 1. Kiến trúc 4 Memory Layer & Router
Hệ thống kết hợp 4 tầng bộ nhớ chuyên biệt:
- **Short-term**: Lưu trữ sliding window lượt hội thoại gần nhất và nén ngữ cảnh.
- **Long-term**: Quản lý fact ổn định, preference, open loops qua Zep User Context Block & Graph Edges.
- **Episodic**: Truy hồi trajectory sự cố, giải pháp và reflection (Zep Graph episodes theo `user_id`).
- **Semantic**: Tri thức domain/playbook dùng chung (Zep Standalone Graph theo `graph_id`).
Router định tuyến layer phù hợp; Context Budget Manager phân bổ token ngân sách (10/4/3/3) và lắp ghép prompt.

## 2. Giải thích Compaction (E10)
Chiến lược sliding window kết hợp tóm tắt (summary) và trích xuất ghi chú bền vững (`<DURABLE_NOTES>`). Khi context quá tải, các filler turns bị loại bỏ/nén lại nhưng thông tin then chốt (ràng buộc `REVIEW-DEADLINE-1600`) luôn được lưu giữ nguyên vẹn trong durable notes.

## 3. Giải thích Conflict & Recency (E08)
Khi có sự thay đổi stack (Minh thích Python cho `ORCHID-27` nhưng bắt buộc dùng TypeScript + NestJS cho `BLUEBIRD-42`), Zep Graph ghi nhận các khoảng hiệu lực `valid_at` / `invalid_at` và phân tách theo namespace project. Nhờ vậy, truy vấn cho `BLUEBIRD-42` trả về đúng stack mới nhất mà không bị lẫn fact cũ.

## 4. So sánh Memory-enabled vs No-memory
Theo số liệu từ `reports/comparison.md`:
- **Evidence hit rate**: Tăng từ **18.2%** (No-memory) lên **100.0%** (Memory-enabled) (+81.8%).
- **Passed cases**: Đạt **11/11** so với **2/11** (+9 cases).
- **Latency**: Trung bình 705.6 ms cho multi-layer graph retrieval.
- **Token reduction**: No-memory giảm 81.8% chỉ vì không lấy dữ liệu; Memory-enabled đạt 15.3% reduction nhưng đảm bảo chính xác 100% evidence.

## 5. Đánh giá Case & Xử lý biên
Trong baseline No-memory, toàn bộ cross-session, episodic và semantic cases (E02-E09, E11) đều FAIL do thiếu context. Với Student Memory, toàn bộ 11/11 practice cases và 20/20 Golden cases đều PASS hoàn hảo (10/10 bonus) nhờ tinh chỉnh `episode_char_cap` và `limit` vừa vặn ngân sách token.

## 6. Privacy, Isolation & Minh chứng
- **Isolation**: Phân lập nghiêm ngặt theo `user_id`. Truy vấn của Lan (E09) không làm lộ dữ liệu của Minh.
- **Right-to-be-forgotten**: Lệnh `python -m src.forget --user-id minh-lab17` xóa sạch toàn bộ user memory. Kiểm tra `--verify-only` chứng minh `Zep user absent: True`, `Redis user keys remaining: 0`, trong khi Knowledge Base dùng chung vẫn an toàn.
