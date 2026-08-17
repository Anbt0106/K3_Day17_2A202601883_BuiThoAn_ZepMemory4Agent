# Lab 17 Golden Set Report

- Implementation: `student`
- Kind: `golden`
- Cases: **20**
- Passed: **20/20**
- Evidence hit rate: **100.0%**
- Average retrieval latency: **824.7 ms**
- Average token reduction vs full source context: **10.5%**
- Golden bonus: **10/10** (100% required)

| Case | Layer | Pass | Latency ms | Retrieved tokens | Token reduction | Missing / Error |
| --- | --- | --- | ---: | ---: | ---: | --- |
| G01 | short_term | PASS | 0.2 | 227 | 0.0% |  |
| G02 | short_term | PASS | 0.0 | 133 | 0.0% |  |
| G08 | long_term | PASS | 1534.3 | 760 | 0.0% |  |
| G09 | long_term | PASS | 1187.9 | 1528 | 0.0% |  |
| G12 | semantic | PASS | 346.7 | 242 | 47.3% |  |
| G14 | semantic | PASS | 303.3 | 240 | 38.0% |  |
| G15 | semantic | PASS | 212.5 | 240 | 47.7% |  |
| G19 | mixed | PASS | 1481.4 | 581 | 0.0% |  |
| G03 | long_term | PASS | 1173.6 | 1491 | 0.0% |  |
| G04 | long_term | PASS | 1314.6 | 1528 | 0.0% |  |
| G05 | long_term | PASS | 1148.5 | 1502 | 0.0% |  |
| G10 | episodic | PASS | 220.3 | 345 | 0.0% |  |
| G11 | episodic | PASS | 211.5 | 344 | 0.0% |  |
| G13 | semantic | PASS | 205.5 | 240 | 57.5% |  |
| G16 | mixed | PASS | 1391.1 | 581 | 0.0% |  |
| G18 | mixed | PASS | 456.2 | 500 | 11.5% |  |
| G20 | mixed | PASS | 1598.2 | 831 | 0.0% |  |
| G06 | long_term | PASS | 1226.5 | 1496 | 0.0% |  |
| G07 | long_term | PASS | 1151.8 | 1519 | 0.0% |  |
| G17 | mixed | PASS | 1330.2 | 581 | 8.1% |  |

## Evidence excerpts

### G01 - short_term

`<SESSION_SUMMARY> user: Constraint HOLD-ALPHA-0900: standup is 09:00 sharp and must not be forgotten. | assistant: Noted standup constraint. | user: Constraint HOLD-BETA-STAGING: writes go to staging DB only. | assistant: Noted staging constraint. | user: Filler A about button padding. | assistant: Filler A. | user: Filler B about color tokens. | assistant: Filler B. | user: Filler C about copy tone. | assistant: Filler C. </SESSION_SUMMARY> <DURABLE_NOTES> - user: Constraint HOLD-ALPHA-0900: standup is 09:00 sharp and must not be forgotten. - assistant: Noted standup constraint. - user: Constraint HOLD-BETA-STAGING: writes go to staging DB only. - assistant: Noted staging constraint. </DURA`

### G02 - short_term

`<RECENT_TURNS> user: Ten du an ca nhan cua toi la ORCHID-27. Toi thich Python va khong thich Java. Khi giai thich code, hay dung vi du ngan. assistant: Da hieu: demo ca nhan ORCHID-27, uu tien Python, tranh Java, vi du ngan. user: Toi dang hoc async/await va hay nham coroutine voi Task. Neu sau nay gap chu de nay, hay giai thich bang timeline. assistant: Toi se uu tien timeline khi giai thich coroutine va Task. user: TODO: hoan thanh benchmark report truoc thu Sau luc 16:00. Day la open loop LAB-REPORT-1600. </RECENT_TURNS>`

### G08 - long_term

`<USER_SUMMARY> The user's project is LOTUS-88. They prioritize Java and Spring Boot for backend development and do not use Python for backend. </USER_SUMMARY>  <EPISODES> Episodes are source message or document excerpts shown in selection order.   - Created At: 2026-08-01 11:00:00     Source: message     Content: [user] {   "user_id": "lan-lab17",   "first_name": "Lan",   "last_name": "Tran",   "user_alias": "Lan Tran" }: Toi la Lan. Du an cua toi la LOTUS-88. Toi uu tien Java va Spring Boot, va khong dung Python trong vi du backend.   - Created At: 2026-08-01 11:00:20     Source: message     Content: Lab Assistant (assistant): Da hieu: LOTUS-88, Java + Spring Boot cho backend examples. </EP`

### G09 - long_term

`<USER_SUMMARY> The user's personal project is named ORCHID-27, for which they prefer to use Python. For the company project BLUEBIRD-42, the backend must use TypeScript with NestJS, and Python should not be used for this project. The user needs to complete a benchmark report for open loop LAB-REPORT-1600 by Saturday at 16:00. The user is debugging async HTTP and has tried increasing the timeout to 60s without success. The user's effective solution involves reusing the aiohttp ClientSession and setting concurrency to 20, identifying the main issue as connection churn, not the timeout threshold. This solution addresses the ASYNC-FIX-20 incident.  Minh prefers Python and dislikes Java. The user`

### G12 - semantic

`EPISODE: For POST /payments, every retryable request MUST send the same Idempotency-Key. Retry only HTTP 429 or transient 5xx errors, use exponential-backoff, and stop after max-3-retries. Marker: PAYMENT-RULE-3. EPISODE: {"id":"kb-memory-privacy","entity":"Agent Memory Privacy Rule","summary":"Do not persist personal data without explicit opt-in. A deletion request must remove user-scoped memory and be verified across every store. Marker: DELETE-VERIFY-ALL.","source":"memory-governance-policy","u EPISODE: {"id":"kb-payment-retry","entity":"Payment API Retry Policy","summary":"For POST /payments, every retryable request MUST send the same Idempotency-Key. Retry only HTTP 429 or transient 5xx`

### G14 - semantic

`EPISODE: {"id":"kb-memory-privacy","entity":"Agent Memory Privacy Rule","summary":"Do not persist personal data without explicit opt-in. A deletion request must remove user-scoped memory and be verified across every store. Marker: DELETE-VERIFY-ALL.","source":"memory-governance-policy","u EPISODE: Do not persist personal data without explicit opt-in. A deletion request must remove user-scoped memory and be verified across every store. Marker: DELETE-VERIFY-ALL. EPISODE: {"id":"kb-context-budget","entity":"Memory Context Budget","summary":"Reserve bounded context for memory. This lab uses short-term 10 percent, long-term 4 percent, episodic 3 percent, semantic 3 percent; trim lower-priority m`

### G15 - semantic

`EPISODE: {"id":"kb-memory-privacy","entity":"Agent Memory Privacy Rule","summary":"Do not persist personal data without explicit opt-in. A deletion request must remove user-scoped memory and be verified across every store. Marker: DELETE-VERIFY-ALL.","source":"memory-governance-policy","u EPISODE: Do not persist personal data without explicit opt-in. A deletion request must remove user-scoped memory and be verified across every store. Marker: DELETE-VERIFY-ALL. EPISODE: {"id":"kb-context-budget","entity":"Memory Context Budget","summary":"Reserve bounded context for memory. This lab uses short-term 10 percent, long-term 4 percent, episodic 3 percent, semantic 3 percent; trim lower-priority m`

### G19 - mixed

`<LONG_TERM> <USER_SUMMARY> The user's project is LOTUS-88. They prioritize Java and Spring Boot for backend development and do not use Python for backend. </USER_SUMMARY>  <EPISODES> Episodes are source message or document excerpts shown in selection order.   - Created At: 2026-08-17 15:28:59     Source: message     Content: [user] {   "user_id": "lan-lab17",   "first_name": "Lan",   "last_name": "Tran",   "user_alias": "Evaluation User" }: Lan uu tien stack backend nao cho LOTUS-88?   - Created At: 2026-08-01 11:00:20     Source: message     Content: Lab Assistant (assistant): Da hieu: LOTUS-88, Java + Spring Boot cho backend examples.   - Created At: 2026-08-01 11:00:00     Source: message`

### G03 - long_term

`<USER_SUMMARY> The user's personal project is named ORCHID-27, for which they prefer to use Python. For the company project BLUEBIRD-42, the backend must use TypeScript with NestJS, and Python should not be used for this project. The user needs to complete a benchmark report for open loop LAB-REPORT-1600 by Saturday at 16:00. The user is debugging async HTTP and has tried increasing the timeout to 60s without success. The user's effective solution involves reusing the aiohttp ClientSession and setting concurrency to 20, identifying the main issue as connection churn, not the timeout threshold. This solution addresses the ASYNC-FIX-20 incident.  Minh prefers Python and dislikes Java. The user`

### G04 - long_term

`<USER_SUMMARY> The user's personal project is named ORCHID-27, for which they prefer to use Python. For the company project BLUEBIRD-42, the backend must use TypeScript with NestJS, and Python should not be used for this project. The user needs to complete a benchmark report for open loop LAB-REPORT-1600 by Saturday at 16:00. The user is debugging async HTTP and has tried increasing the timeout to 60s without success. The user's effective solution involves reusing the aiohttp ClientSession and setting concurrency to 20, identifying the main issue as connection churn, not the timeout threshold. This solution addresses the ASYNC-FIX-20 incident.  Minh prefers Python and dislikes Java. The user`

### G05 - long_term

`<USER_SUMMARY> The user's personal project is named ORCHID-27, for which they prefer to use Python. For the company project BLUEBIRD-42, the backend must use TypeScript with NestJS, and Python should not be used for this project. The user needs to complete a benchmark report for open loop LAB-REPORT-1600 by Saturday at 16:00. The user is debugging async HTTP and has tried increasing the timeout to 60s without success. The user's effective solution involves reusing the aiohttp ClientSession and setting concurrency to 20, identifying the main issue as connection churn, not the timeout threshold. This solution addresses the ASYNC-FIX-20 incident.  Minh prefers Python and dislikes Java. The user`

### G10 - episodic

`EPISODE: Ten du an ca nhan cua toi la ORCHID-27. Toi thich Python va khong thich Java. Khi giai thich code, hay dung vi du ngan. EPISODE: Toi dang hoc async/await va hay nham coroutine voi Task. Neu sau nay gap chu de nay, hay giai thich bang timeline. EPISODE: Toi se uu tien timeline khi giai thich coroutine va Task. EPISODE: TODO: hoan thanh benchmark report truoc thu Sau luc 16:00. Day la open loop LAB-REPORT-1600. EPISODE: Hom nay toi debug async HTTP. Toi da thu tang timeout len 60s nhung van fail. EPISODE: Cach hieu qua la reuse aiohttp ClientSession va dat concurrency=20. Reflection: loi chinh la connection churn, khong phai timeout threshold. Ma su co ASYNC-FIX-20. EPISODE: Da ghi nh`

### G11 - episodic

`EPISODE: Ten du an ca nhan cua toi la ORCHID-27. Toi thich Python va khong thich Java. Khi giai thich code, hay dung vi du ngan. EPISODE: Toi dang hoc async/await va hay nham coroutine voi Task. Neu sau nay gap chu de nay, hay giai thich bang timeline. EPISODE: TODO: hoan thanh benchmark report truoc thu Sau luc 16:00. Day la open loop LAB-REPORT-1600. EPISODE: Cach hieu qua la reuse aiohttp ClientSession va dat concurrency=20. Reflection: loi chinh la connection churn, khong phai timeout threshold. Ma su co ASYNC-FIX-20. EPISODE: Da ghi nhan trajectory: increase timeout khong hieu qua; ClientSession + concurrency=20 giai quyet connection churn. EPISODE: Cap nhat moi: voi du an cong ty BLUEB`

### G13 - semantic

`EPISODE: {"id":"kb-async-http","entity":"Async HTTP Incident Playbook","summary":"When async HTTP calls time out, inspect connection pooling, downstream saturation and concurrency before increasing timeout. Reuse a long-lived client session where possible. Marker: CONN-POOL-FIRST.","sourc EPISODE: Do not persist personal data without explicit opt-in. A deletion request must remove user-scoped memory and be verified across every store. Marker: DELETE-VERIFY-ALL. EPISODE: {"id":"kb-context-budget","entity":"Memory Context Budget","summary":"Reserve bounded context for memory. This lab uses short-term 10 percent, long-term 4 percent, episodic 3 percent, semantic 3 percent; trim lower-priority m`

### G16 - mixed

`<LONG_TERM> <USER_SUMMARY> The user's personal project is named ORCHID-27, for which they prefer to use Python. For the company project BLUEBIRD-42, the backend must use TypeScript with NestJS, and Python should not be used for this project. The user needs to complete a benchmark report for open loop LAB-REPORT-1600 by Saturday at 16:00. The user is debugging async HTTP and has tried increasing the timeout to 60s without success. The user's effective solution involves reusing the aiohttp ClientSession and setting concurrency to 20, identifying the main issue as connection churn, not the timeout threshold. This solution addresses the ASYNC-FIX-20 incident.  Minh prefers Python and dislikes Ja`

### G18 - mixed

`<EPISODIC> EPISODE: Ten du an ca nhan cua toi la ORCHID-27. Toi thich Python va khong thich Java. Khi giai thich code, hay dung vi du ngan. EPISODE: Toi dang hoc async/await va hay nham coroutine voi Task. Neu sau nay gap chu de nay, hay giai thich bang timeline. EPISODE: Hom nay toi debug async HTTP. Toi da thu tang timeout len 60s nhung van fail. EPISODE: Cach hieu qua la reuse aiohttp ClientSession va dat concurrency=20. Reflection: loi chinh la connection churn, khong phai timeout threshold. Ma su co ASYNC-FIX-20. EPISODE: Cap nhat moi: voi du an cong ty BLUEBIRD-42, backend bat buoc dung TypeScript voi NestJS; khong dung Python cho backend du an nay. Preference Python van dung cho demo `

### G20 - mixed

`<LONG_TERM> <USER_SUMMARY> The user's personal project is named ORCHID-27, for which they prefer to use Python. For the company project BLUEBIRD-42, the backend must use TypeScript with NestJS, and Python should not be used for this project. The user needs to complete a benchmark report for open loop LAB-REPORT-1600 by Saturday at 16:00. The user is debugging async HTTP and has tried increasing the timeout to 60s without success. The user's effective solution involves reusing the aiohttp ClientSession and setting concurrency to 20, identifying the main issue as connection churn, not the timeout threshold. This solution addresses the ASYNC-FIX-20 incident.  Minh prefers Python and dislikes Ja`

### G06 - long_term

`<USER_SUMMARY> The user's personal project is named ORCHID-27, for which they prefer to use Python. For the company project BLUEBIRD-42, the backend must use TypeScript with NestJS, and Python should not be used for this project. The user needs to complete a benchmark report for open loop LAB-REPORT-1600 by Saturday at 16:00. The user is debugging async HTTP and has tried increasing the timeout to 60s without success. The user's effective solution involves reusing the aiohttp ClientSession and setting concurrency to 20, identifying the main issue as connection churn, not the timeout threshold. This solution addresses the ASYNC-FIX-20 incident.  Minh prefers Python and dislikes Java. The user`

### G07 - long_term

`<USER_SUMMARY> The user's personal project is named ORCHID-27, for which they prefer to use Python. For the company project BLUEBIRD-42, the backend must use TypeScript with NestJS, and Python should not be used for this project. The user needs to complete a benchmark report for open loop LAB-REPORT-1600 by Saturday at 16:00. The user is debugging async HTTP and has tried increasing the timeout to 60s without success. The user's effective solution involves reusing the aiohttp ClientSession and setting concurrency to 20, identifying the main issue as connection churn, not the timeout threshold. This solution addresses the ASYNC-FIX-20 incident.  Minh prefers Python and dislikes Java. The user`

### G17 - mixed

`<LONG_TERM> <USER_SUMMARY> The user's personal project is named ORCHID-27, for which they prefer to use Python. For the company project BLUEBIRD-42, the backend must use TypeScript with NestJS, and Python should not be used for this project. The user needs to complete a benchmark report for open loop LAB-REPORT-1600 by Saturday at 16:00. The user is debugging async HTTP and has tried increasing the timeout to 60s without success. The user's effective solution involves reusing the aiohttp ClientSession and setting concurrency to 20, identifying the main issue as connection churn, not the timeout threshold. This solution addresses the ASYNC-FIX-20 incident.  Minh prefers Python and dislikes Ja`
