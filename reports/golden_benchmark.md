# Lab 17 Golden Set Report

- Implementation: `student`
- Kind: `golden`
- Cases: **20**
- Passed: **20/20**
- Evidence hit rate: **100.0%**
- Average retrieval latency: **1360.3 ms**
- Average token reduction vs full source context: **13.8%**
- Golden bonus: **10/10** (100% required)

| Case | Layer | Pass | Latency ms | Retrieved tokens | Token reduction | Missing / Error |
| --- | --- | --- | ---: | ---: | ---: | --- |
| G01 | short_term | PASS | 0.2 | 227 | 0.0% |  |
| G02 | short_term | PASS | 0.0 | 133 | 0.0% |  |
| G08 | long_term | PASS | 2436.1 | 887 | 0.0% |  |
| G09 | long_term | PASS | 2452.4 | 2752 | 0.0% |  |
| G12 | semantic | PASS | 207.8 | 242 | 47.3% |  |
| G14 | semantic | PASS | 209.8 | 240 | 38.0% |  |
| G15 | semantic | PASS | 208.5 | 240 | 47.7% |  |
| G19 | mixed | PASS | 2248.9 | 581 | 0.0% |  |
| G03 | long_term | PASS | 2205.2 | 2688 | 0.0% |  |
| G04 | long_term | PASS | 2156.2 | 2644 | 0.0% |  |
| G05 | long_term | PASS | 2121.9 | 2649 | 0.0% |  |
| G10 | episodic | PASS | 225.9 | 158 | 28.5% |  |
| G11 | episodic | PASS | 224.8 | 167 | 24.4% |  |
| G13 | semantic | PASS | 215.4 | 240 | 57.5% |  |
| G16 | mixed | PASS | 2318.3 | 581 | 0.0% |  |
| G18 | mixed | PASS | 422.3 | 423 | 25.1% |  |
| G20 | mixed | PASS | 2771.4 | 724 | 0.0% |  |
| G06 | long_term | PASS | 2066.9 | 2428 | 0.0% |  |
| G07 | long_term | PASS | 2215.9 | 2534 | 0.0% |  |
| G17 | mixed | PASS | 2498.4 | 581 | 8.1% |  |

## Evidence excerpts

### G01 - short_term

`<SESSION_SUMMARY> user: Constraint HOLD-ALPHA-0900: standup is 09:00 sharp and must not be forgotten. | assistant: Noted standup constraint. | user: Constraint HOLD-BETA-STAGING: writes go to staging DB only. | assistant: Noted staging constraint. | user: Filler A about button padding. | assistant: Filler A. | user: Filler B about color tokens. | assistant: Filler B. | user: Filler C about copy tone. | assistant: Filler C. </SESSION_SUMMARY> <DURABLE_NOTES> - user: Constraint HOLD-ALPHA-0900: standup is 09:00 sharp and must not be forgotten. - assistant: Noted standup constraint. - user: Constraint HOLD-BETA-STAGING: writes go to staging DB only. - assistant: Noted staging constraint. </DURA`

### G02 - short_term

`<RECENT_TURNS> user: Ten du an ca nhan cua toi la ORCHID-27. Toi thich Python va khong thich Java. Khi giai thich code, hay dung vi du ngan. assistant: Da hieu: demo ca nhan ORCHID-27, uu tien Python, tranh Java, vi du ngan. user: Toi dang hoc async/await va hay nham coroutine voi Task. Neu sau nay gap chu de nay, hay giai thich bang timeline. assistant: Toi se uu tien timeline khi giai thich coroutine va Task. user: TODO: hoan thanh benchmark report truoc thu Sau luc 16:00. Day la open loop LAB-REPORT-1600. </RECENT_TURNS>`

### G08 - long_term

`<USER_SUMMARY> The user's project is LOTUS-88. They prioritize Java and Spring Boot for backend development and do not use Python for backend examples. </USER_SUMMARY>  <EPISODES> Episodes are source message or document excerpts shown in selection order.   - Created At: 2026-08-01 11:00:00     Source: message     Content: [user] {   "user_id": "lan-lab17",   "first_name": "Lan",   "last_name": "Tran",   "user_alias": "Lan Tran" }: Toi la Lan. Du an cua toi la LOTUS-88. Toi uu tien Java va Spring Boot, va khong dung Python trong vi du backend.   - Created At: 2026-08-01 11:00:20     Source: message     Content: Lab Assistant (assistant): Da hieu: LOTUS-88, Java + Spring Boot cho backend examp`

### G09 - long_term

`<USER_SUMMARY> Minh's personal project ORCHID-27 prefers Python. For the company project BLUEBIRD-42, the backend must use TypeScript with NestJS, not Python.  Minh prefers Python and dislikes Java. When explaining code, Minh prefers short examples. Minh is currently learning about async/await and often confuses coroutines with Tasks. If this topic arises in the future, explain it using a timeline.  When explaining code, use short examples. If the topic of async/await and coroutines arises, explain it using a timeline. </USER_SUMMARY>  <EPISODES> Episodes are source message or document excerpts shown in selection order.   - Created At: 2026-08-05 08:00:00     Source: message     Content: [us`

### G12 - semantic

`EPISODE: {"id":"kb-payment-retry","entity":"Payment API Retry Policy","summary":"For POST /payments, every retryable request MUST send the same Idempotency-Key. Retry only HTTP 429 or transient 5xx errors, use exponential-backoff, and stop after max-3-retries. Marker: PAYMENT-RULE-3.","so EPISODE: For POST /payments, every retryable request MUST send the same Idempotency-Key. Retry only HTTP 429 or transient 5xx errors, use exponential-backoff, and stop after max-3-retries. Marker: PAYMENT-RULE-3. EPISODE: {"id":"kb-memory-privacy","entity":"Agent Memory Privacy Rule","summary":"Do not persist personal data without explicit opt-in. A deletion request must remove user-scoped memory and be ver`

### G14 - semantic

`EPISODE: {"id":"kb-memory-privacy","entity":"Agent Memory Privacy Rule","summary":"Do not persist personal data without explicit opt-in. A deletion request must remove user-scoped memory and be verified across every store. Marker: DELETE-VERIFY-ALL.","source":"memory-governance-policy","u EPISODE: Do not persist personal data without explicit opt-in. A deletion request must remove user-scoped memory and be verified across every store. Marker: DELETE-VERIFY-ALL. EPISODE: {"id":"kb-context-budget","entity":"Memory Context Budget","summary":"Reserve bounded context for memory. This lab uses short-term 10 percent, long-term 4 percent, episodic 3 percent, semantic 3 percent; trim lower-priority m`

### G15 - semantic

`EPISODE: {"id":"kb-memory-privacy","entity":"Agent Memory Privacy Rule","summary":"Do not persist personal data without explicit opt-in. A deletion request must remove user-scoped memory and be verified across every store. Marker: DELETE-VERIFY-ALL.","source":"memory-governance-policy","u EPISODE: Do not persist personal data without explicit opt-in. A deletion request must remove user-scoped memory and be verified across every store. Marker: DELETE-VERIFY-ALL. EPISODE: {"id":"kb-context-budget","entity":"Memory Context Budget","summary":"Reserve bounded context for memory. This lab uses short-term 10 percent, long-term 4 percent, episodic 3 percent, semantic 3 percent; trim lower-priority m`

### G19 - mixed

`<LONG_TERM> <USER_SUMMARY> The user's project is LOTUS-88. They prioritize Java and Spring Boot for backend development and do not use Python for backend examples. </USER_SUMMARY>  <EPISODES> Episodes are source message or document excerpts shown in selection order.   - Created At: 2026-08-17 16:05:52     Source: message     Content: [user] {   "user_id": "lan-lab17",   "first_name": "Lan",   "last_name": "Tran",   "user_alias": "Evaluation User" }: Lan uu tien stack backend nao cho LOTUS-88?   - Created At: 2026-08-01 11:00:20     Source: message     Content: Lab Assistant (assistant): Da hieu: LOTUS-88, Java + Spring Boot cho backend examples.   - Created At: 2026-08-01 11:00:00     Source`

### G03 - long_term

`<USER_SUMMARY> Minh's personal project ORCHID-27 prefers Python. For the company project BLUEBIRD-42, the backend must use TypeScript with NestJS, not Python.  Minh prefers Python and dislikes Java. When explaining code, Minh prefers short examples. Minh is currently learning about async/await and often confuses coroutines with Tasks. If this topic arises in the future, explain it using a timeline.  When explaining code, use short examples. If the topic of async/await and coroutines arises, explain it using a timeline. </USER_SUMMARY>  <EPISODES> Episodes are source message or document excerpts shown in selection order.   - Created At: 2026-08-17 16:09:31     Source: message     Content: [us`

### G04 - long_term

`<USER_SUMMARY> Minh's personal project ORCHID-27 prefers Python. For the company project BLUEBIRD-42, the backend must use TypeScript with NestJS, not Python.  Minh prefers Python and dislikes Java. When explaining code, Minh prefers short examples. Minh is currently learning about async/await and often confuses coroutines with Tasks. If this topic arises in the future, explain it using a timeline.  When explaining code, use short examples. If the topic of async/await and coroutines arises, explain it using a timeline. </USER_SUMMARY>  <EPISODES> Episodes are source message or document excerpts shown in selection order.   - Created At: 2026-08-17 16:05:57     Source: message     Content: [us`

### G05 - long_term

`<USER_SUMMARY> Minh's personal project ORCHID-27 prefers Python. For the company project BLUEBIRD-42, the backend must use TypeScript with NestJS, not Python.  Minh prefers Python and dislikes Java. When explaining code, Minh prefers short examples. Minh is currently learning about async/await and often confuses coroutines with Tasks. If this topic arises in the future, explain it using a timeline.  When explaining code, use short examples. If the topic of async/await and coroutines arises, explain it using a timeline. </USER_SUMMARY>  <EPISODES> Episodes are source message or document excerpts shown in selection order.   - Created At: 2026-08-01 09:02:00     Source: message     Content: [us`

### G10 - episodic

`EPISODE: Minh dang ngoi mot minh viet cho xong cai ham retry cho POST payment de toi nay demo, va minh muon no vua dung dung ngon ngu ma minh thich khi lam viec ca nhan, vua bam sat du EPISODE: Toi nay minh muon viet cho tron ven cai retry payment ma vua dung so thich stack ca nhan cua minh, vua theo dung policy thanh toan chinh thuc, vua tranh dam lai dung cai su co EPISODE: Hom nay toi debug async HTTP. Toi da thu tang timeout len 60s nhung van fail. EPISODE: Cach hieu qua la reuse aiohttp ClientSession va dat concurrency=20. Reflection: loi chinh la connection churn, khong phai timeout threshold. Ma su co ASYNC-FIX-20.`

### G11 - episodic

`EPISODE: Minh dang ngoi mot minh viet cho xong cai ham retry cho POST payment de toi nay demo, va minh muon no vua dung dung ngon ngu ma minh thich khi lam viec ca nhan, vua bam sat du EPISODE: Toi dang hoc async/await va hay nham coroutine voi Task. Neu sau nay gap chu de nay, hay giai thich bang timeline. EPISODE: Toi nay minh muon viet cho tron ven cai retry payment ma vua dung so thich stack ca nhan cua minh, vua theo dung policy thanh toan chinh thuc, vua tranh dam lai dung cai su co EPISODE: Cach hieu qua la reuse aiohttp ClientSession va dat concurrency=20. Reflection: loi chinh la connection churn, khong phai timeout threshold. Ma su co ASYNC-FIX-20.`

### G13 - semantic

`EPISODE: {"id":"kb-async-http","entity":"Async HTTP Incident Playbook","summary":"When async HTTP calls time out, inspect connection pooling, downstream saturation and concurrency before increasing timeout. Reuse a long-lived client session where possible. Marker: CONN-POOL-FIRST.","sourc EPISODE: Do not persist personal data without explicit opt-in. A deletion request must remove user-scoped memory and be verified across every store. Marker: DELETE-VERIFY-ALL. EPISODE: {"id":"kb-context-budget","entity":"Memory Context Budget","summary":"Reserve bounded context for memory. This lab uses short-term 10 percent, long-term 4 percent, episodic 3 percent, semantic 3 percent; trim lower-priority m`

### G16 - mixed

`<LONG_TERM> <USER_SUMMARY> Minh's personal project ORCHID-27 prefers Python. For the company project BLUEBIRD-42, the backend must use TypeScript with NestJS, not Python.  Minh prefers Python and dislikes Java. When explaining code, Minh prefers short examples. Minh is currently learning about async/await and often confuses coroutines with Tasks. If this topic arises in the future, explain it using a timeline.  When explaining code, use short examples. If the topic of async/await and coroutines arises, explain it using a timeline. </USER_SUMMARY>  <EPISODES> Episodes are source message or document excerpts shown in selection order.   - Created At: 2026-08-17 16:09:34     Source: message     `

### G18 - mixed

`<EPISODIC> EPISODE: Toi dang hoc async/await va hay nham coroutine voi Task. Neu sau nay gap chu de nay, hay giai thich bang timeline. EPISODE: Toi nay minh muon viet cho tron ven cai retry payment ma vua dung so thich stack ca nhan cua minh, vua theo dung policy thanh toan chinh thuc, vua tranh dam lai dung cai su co EPISODE: Cach hieu qua la reuse aiohttp ClientSession va dat concurrency=20. Reflection: loi chinh la connection churn, khong phai timeout threshold. Ma su co ASYNC-FIX-20. EPISODE: Cap nhat moi: voi du an cong ty BLUEBIRD-42, backend bat buoc dung TypeScript voi NestJS; khong dung Python cho backend du an nay. Preference Python van dung cho demo ca nhan  </EPISODIC>  <SEMANTIC`

### G20 - mixed

`<LONG_TERM> <USER_SUMMARY> Minh's personal project ORCHID-27 prefers Python. For the company project BLUEBIRD-42, the backend must use TypeScript with NestJS, not Python.  Minh prefers Python and dislikes Java. When explaining code, Minh prefers short examples. Minh is currently learning about async/await and often confuses coroutines with Tasks. If this topic arises in the future, explain it using a timeline.  When explaining code, use short examples. If the topic of async/await and coroutines arises, explain it using a timeline. </USER_SUMMARY>  <EPISODES> Episodes are source message or document excerpts shown in selection order.   - Created At: 2026-08-17 16:05:59     Source: message     `

### G06 - long_term

`<USER_SUMMARY> Minh's personal project ORCHID-27 prefers Python. For the company project BLUEBIRD-42, the backend must use TypeScript with NestJS, not Python.  Minh prefers Python and dislikes Java. When explaining code, Minh prefers short examples. Minh is currently learning about async/await and often confuses coroutines with Tasks. If this topic arises in the future, explain it using a timeline.  When explaining code, use short examples. If the topic of async/await and coroutines arises, explain it using a timeline. </USER_SUMMARY>  <EPISODES> Episodes are source message or document excerpts shown in selection order.   - Created At: 2026-08-05 08:00:00     Source: message     Content: [us`

### G07 - long_term

`<USER_SUMMARY> Minh's personal project ORCHID-27 prefers Python. For the company project BLUEBIRD-42, the backend must use TypeScript with NestJS, not Python.  Minh prefers Python and dislikes Java. When explaining code, Minh prefers short examples. Minh is currently learning about async/await and often confuses coroutines with Tasks. If this topic arises in the future, explain it using a timeline.  When explaining code, use short examples. If the topic of async/await and coroutines arises, explain it using a timeline. </USER_SUMMARY>  <EPISODES> Episodes are source message or document excerpts shown in selection order.   - Created At: 2026-08-17 16:05:55     Source: message     Content: [us`

### G17 - mixed

`<LONG_TERM> <USER_SUMMARY> Minh's personal project ORCHID-27 prefers Python. For the company project BLUEBIRD-42, the backend must use TypeScript with NestJS, not Python.  Minh prefers Python and dislikes Java. When explaining code, Minh prefers short examples. Minh is currently learning about async/await and often confuses coroutines with Tasks. If this topic arises in the future, explain it using a timeline.  When explaining code, use short examples. If the topic of async/await and coroutines arises, explain it using a timeline. </USER_SUMMARY>  <EPISODES> Episodes are source message or document excerpts shown in selection order.   - Created At: 2026-08-05 08:00:00     Source: message     `
