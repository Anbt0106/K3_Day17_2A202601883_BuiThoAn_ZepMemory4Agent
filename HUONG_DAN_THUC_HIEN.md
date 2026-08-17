# Hướng dẫn thực hiện Lab 17: Multi-Memory Agent với Zep

Tài liệu này tổng hợp lộ trình từ `README.md`, `LAB.md`, `VALIDATION.md`, `control_plane/`, `data/README.md` và các report.

## 1. Mục tiêu

Hoàn thiện agent có bốn lớp memory:

1. **Short-term**: các lượt hội thoại gần nhất và compaction.
2. **Long-term**: facts, preferences, decisions và open loops theo user.
3. **Episodic**: trajectory, cách xử lý, kết quả và provenance.
4. **Semantic**: tri thức domain dùng chung trong standalone graph.

Evaluator chấm **retrieved evidence**, không chấm câu trả lời đoán đúng. Case PASS khi mọi chuỗi trong `must_contain_all` xuất hiện và mọi chuỗi trong `must_not_contain` không xuất hiện. Mục tiêu practice: ít nhất **9/11 case PASS (80%)**. Điểm nền tối đa 80; golden 20/20 cộng 10; UI cộng 10.

## 2. Quy tắc quan trọng

- Chỉ viết code trong bốn marker `LAB TODO` của `src/memory_student.py`.
- Không sửa/đổi tên `src/memory_reference.py`, evaluator, scorer, dataset hoặc test khóa hành vi.
- Không commit `.env`, `ZEP_API_KEY` hoặc `data/golden_eval.json`.
- Golden chỉ được giảng viên phát ở 60 phút cuối.
- Privacy drill chạy sau khi lưu benchmark practice nhưng trước golden.
- Sau privacy drill, nếu cần chạy golden thì seed lại một lần.
- Không nhận vơ memory hit khi retrieval không trả evidence.

## 3. Chuẩn bị môi trường

Yêu cầu: Docker Desktop/Engine + Compose v2, khoảng 4 GB RAM, Internet và một `ZEP_API_KEY`. OpenAI API key không bắt buộc.

Mở PowerShell:

```powershell
cd D:\AI_In_Action\Codelabs\K3_Day17_2A202601883_BuiThoAn_ZepMemory4Agent
Copy-Item .env.example .env
notepad .env
```

Điền `ZEP_API_KEY` vào `.env`; không đưa key vào source, Markdown, log hoặc Git.

```powershell
docker compose build
docker compose up -d redis qdrant
docker compose run --rm app python -m src.smoke
```

Smoke test cần báo Redis, Qdrant, dataset và key đều `[OK]`. Nếu fail, xử lý môi trường trước khi sửa code.

Seed dữ liệu một lần:

```powershell
docker compose run --rm app python -m src.seed
```

Các benchmark sau dùng `--reuse-seeded`.

## 4. Đọc dữ liệu và control plane

Trước khi code, đọc:

- `data/sessions.json`: session, query, expected layer và ground truth.
- `data/consent.json`: consent của synthetic users.
- `data/knowledge.jsonl`: semantic knowledge dùng chung.
- `control_plane/AGENTS.md`: scope và quyền ghi memory.
- `control_plane/CONTEXT_LAYERS.md`: bảy lớp context.
- `control_plane/MEMORY.md`, `MEMORY_SCHEMA.md`: schema, provenance, timestamp, confidence, TTL, validity.
- `control_plane/SOUL.md`: phải nói rõ layer cung cấp evidence.
- `control_plane/TASKS.md`: open loops phải còn rõ.

Luồng tổng quát:

```text
session JSON -> router -> retrieve 4 layers -> priority/token budget -> merged context -> evaluator
```

## 5. Pha A: short-term và compaction

Chạy:

```powershell
docker compose run --rm app python -m src.demo_short_term
```

Đọc `src/short_term.py`, chú ý `detect_pressure`, `compact`, `extract_durable_notes`, `render`.

1. Chạy demo với `max_recent_messages=6`.
2. Đổi tạm trong `src/demo_short_term.py` xuống `max_recent_messages=4`.
3. Chạy lại.
4. Xác nhận `REVIEW-DEADLINE-1600` vẫn nằm trong durable notes.
5. Sau này ghi 2–3 câu giải thích vào `README_submission.md`.

Compaction phải giữ state, decision, TODO và constraint; không chỉ tóm tắt văn bản. Không sửa `src/evaluate.py`; E01/E10 dùng short-term local.

## 6. Pha B: long-term cross-session

Hoàn thiện `retrieve_long_term` trong `src/memory_student.py`. Luồng cốt lõi:

```python
prime_eval_thread(self.client, user_id, thread_id, query)
user_context = self.client.thread.get_user_context(thread_id=thread_id)
return user_context.context
```

Giữ scaffolding/fact bổ sung hiện có. Với `graph.search`, luôn dùng `cap_query(query)` vì Zep giới hạn query 400 ký tự.

```powershell
docker compose run --rm app python -m src.evaluate --impl student --reuse-seeded --only-layer long_term
```

Kiểm tra E02 (Python), E03 (benchmark report và 16:00), E08 (recency: BLUEBIRD-42 phải là TypeScript + NestJS), E09 (Lan không thấy ORCHID-27).

## 7. Pha C: episodic memory

Hoàn thiện `retrieve_episodic` bằng user graph:

```python
results = self.client.graph.search(
    user_id=user_id,
    query=cap_query(query),
    scope="episodes",
    limit=15,
)
return render_graph_search(results, episode_char_cap=180)
```

Chạy:

```powershell
docker compose run --rm app python -m src.evaluate --impl student --reuse-seeded --only-layer episodic
```

E04 cần `ClientSession`, `concurrency=20`, `ASYNC-FIX-20`. E05 cần `connection churn`, `timeout threshold`. Không dùng semantic `graph_id` cho episodic.

## 8. Pha D: semantic memory

Hoàn thiện `retrieve_semantic` bằng standalone graph:

```python
results = self.client.graph.search(
    graph_id=graph_id,
    query=cap_query(query),
    scope="episodes",
    limit=8,
)
```

Nếu cần, fallback sang `scope="nodes"`. Tránh `scope="auto"` vì có thể làm mất marker như `PAYMENT-RULE-3` và `CONN-POOL-FIRST`.

```powershell
docker compose run --rm app python -m src.evaluate --impl student --reuse-seeded --only-layer semantic
```

Semantic dùng `graph_id`, không dùng `user_id`. Kiểm tra E06 và E11.

## 9. Pha E: assemble và benchmark

Hoàn thiện `assemble_context`:

```python
return self.budget.assemble(layers)
```

Budget bắt buộc: short-term 10%, long-term 4%, episodic 3%, semantic 3%; thứ tự STM -> LT -> EP -> SEM.

```powershell
docker compose run --rm app pytest -q
docker compose run --rm app python -m src.evaluate --impl no_memory
docker compose run --rm app python -m src.evaluate --impl student --reuse-seeded
docker compose run --rm app python -m src.compare_reports
```

Kiểm tra `reports/benchmark.json/.md`, `reports/benchmark_no_memory.json/.md` và `reports/comparison.md`. Nếu fail, đọc cột `Missing / Error` và evidence excerpt, rồi sửa đúng layer.

## 10. Mini-drill

```powershell
docker compose run --rm app python -m src.episodic_maintenance
docker compose run --rm app python -m src.heartbeat --dry-run
docker compose run --rm app python -m src.compiled_kb --reset
```

Quan sát scope, provenance, consent, isolation và việc heartbeat không tự cấp quyền.

## 11. Privacy drill

Chỉ chạy sau khi đã lưu benchmark practice:

```powershell
docker compose run --rm app python -m src.forget --user-id minh-lab17
docker compose run --rm app python -m src.forget --user-id minh-lab17 --verify-only
```

Verify phải chứng minh memory user-scoped của Minh không còn được retrieve. Chụp hai lệnh thành `privacy.png`. Nếu còn chạy golden, seed lại một lần:

```powershell
docker compose run --rm app python -m src.seed
```

## 12. Golden và UI bonus

Khi giảng viên phát `data/golden_eval.json`, đặt đúng path và không sửa file:

```powershell
docker compose run --rm app python -m src.evaluate --impl student --reuse-seeded --golden
```

Golden +10 chỉ khi `passed == 20` và `summary.perfect == true`. UI phải load case, chat tiếp, gọi retrieval thật và hiển thị evidence/layer; UI stub không đủ.

## 13. README_submission.md

Tạo file tối đa 400 từ, gồm:

1. Kiến trúc bốn memory layer và router.
2. Giải thích compaction E10.
3. Giải thích conflict/recency E08.
4. So sánh memory-enabled/no-memory bằng số liệu `comparison.md`.
5. Nêu một case fail và nguyên nhân nếu có.
6. Mô tả privacy, isolation và minh chứng.

## 14. Checklist nộp bài

- [ ] Bốn TODO trong `src/memory_student.py` hoàn thiện.
- [ ] `pytest -q` PASS.
- [ ] Practice đạt ít nhất 9/11 PASS.
- [ ] Có benchmark student, no-memory và comparison.
- [ ] Có privacy delete + verify-only và ảnh minh chứng.
- [ ] Có `README_submission.md` <= 400 từ.
- [ ] Có ảnh long-term, episodic, semantic, privacy.
- [ ] Không có `.env`, key, `.venv`, `.pytest_cache`, golden input trong commit.

Kiểm tra Git:

```powershell
git status --short
git diff --check
git diff --cached --name-status
```

## 15. Lỗi thường gặp

| Hiện tượng | Cách xử lý |
| --- | --- |
| Smoke fail | Kiểm tra Docker, `.env`, key rồi chạy lại. |
| Semantic trả preference user | Dùng standalone `graph_id`, không dùng `user_id`. |
| Mất marker literal | Dùng `scope="episodes"`, fallback `nodes`; tránh `auto`. |
| Query bị từ chối | Dùng `cap_query(query)`. |
| E09 leak dữ liệu | Kiểm tra đúng `user_id` và namespace. |
| Golden chưa chạy | Chờ giảng viên phát file đúng thời điểm. |
| Golden fail sau forget | Seed lại một lần trước golden. |
| Token reduction cao nhưng hit rate thấp | Ưu tiên evidence hit rate, không tối ưu token mù quáng. |

