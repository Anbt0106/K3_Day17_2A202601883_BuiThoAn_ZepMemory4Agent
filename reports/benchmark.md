# Lab 17 Benchmark Report

- Implementation: `student`
- Kind: `practice`
- Cases: **11**
- Passed: **5/11**
- Evidence hit rate: **45.5%**
- Average retrieval latency: **321.4 ms**
- Average token reduction vs full source context: **68.2%**

| Case | Layer | Pass | Latency ms | Retrieved tokens | Token reduction | Missing / Error |
| --- | --- | --- | ---: | ---: | ---: | --- |
| E01 | short_term | PASS | 0.1 | 133 | 0.0% |  |
| E06 | semantic | PASS | 282.6 | 126 | 72.5% |  |
| E09 | long_term | PASS | 1090.1 | 804 | 0.0% |  |
| E10 | short_term | PASS | 0.2 | 195 | 0.0% |  |
| E02 | long_term | FAIL | 370.2 | 0 | 100.0% | ApiError: headers: {'date': 'Mon, 17 Aug 2026 15:46:44 GMT', 'content-type': 'application/json; charset=utf-8', 'transfer-encoding': 'chunked', 'connection': 'keep-alive', 'vary': 'Origin', 'x-content-type-options': 'nosniff', 'x-ratelimit-increment': '1', 'x-ratelimit-limit': '300', 'x-ratelimit-remaining': '289', 'x-ratelimit-reset': '1786981620', 'strict-transport-security': 'max-age=2592000', 'cf-cache-status': 'DYNAMIC', 'content-encoding': 'gzip', 'server': 'cloudflare', 'cf-ray': 'a2c9d0343cbc6ceb-HKG'}, status_code: 404, body: {'message': 'user not found', 'request_id': '51b61e28-20e5-4b7d-bd85-c32a4ae362e8'} |
| E03 | long_term | FAIL | 403.3 | 0 | 100.0% | ApiError: headers: {'date': 'Mon, 17 Aug 2026 15:46:45 GMT', 'content-type': 'application/json; charset=utf-8', 'transfer-encoding': 'chunked', 'connection': 'keep-alive', 'vary': 'Origin', 'x-content-type-options': 'nosniff', 'x-ratelimit-increment': '1', 'x-ratelimit-limit': '300', 'x-ratelimit-remaining': '287', 'x-ratelimit-reset': '1786981620', 'strict-transport-security': 'max-age=2592000', 'cf-cache-status': 'DYNAMIC', 'content-encoding': 'gzip', 'server': 'cloudflare', 'cf-ray': 'a2c9d036cc0e6ceb-HKG'}, status_code: 404, body: {'message': 'user not found', 'request_id': '28a72d39-fa15-42ac-8c93-5c5b50efa7fe'} |
| E04 | episodic | FAIL | 189.6 | 0 | 100.0% | ApiError: headers: {'date': 'Mon, 17 Aug 2026 15:46:45 GMT', 'content-type': 'application/json; charset=utf-8', 'transfer-encoding': 'chunked', 'connection': 'keep-alive', 'vary': 'Origin', 'x-content-type-options': 'nosniff', 'x-ratelimit-increment': '1', 'x-ratelimit-limit': '300', 'x-ratelimit-remaining': '287', 'x-ratelimit-reset': '1786981620', 'strict-transport-security': 'max-age=2592000', 'cf-cache-status': 'DYNAMIC', 'content-encoding': 'gzip', 'server': 'cloudflare', 'cf-ray': 'a2c9d037ff996ceb-HKG'}, status_code: 404, body: {'message': 'not found', 'request_id': '5c3a0dd6-78ba-4713-9ca2-7b3ca3115214'} |
| E05 | episodic | FAIL | 235.3 | 0 | 100.0% | ApiError: headers: {'date': 'Mon, 17 Aug 2026 15:46:45 GMT', 'content-type': 'application/json; charset=utf-8', 'transfer-encoding': 'chunked', 'connection': 'keep-alive', 'vary': 'Origin', 'x-content-type-options': 'nosniff', 'x-ratelimit-increment': '1', 'x-ratelimit-limit': '300', 'x-ratelimit-remaining': '286', 'x-ratelimit-reset': '1786981620', 'strict-transport-security': 'max-age=2592000', 'cf-cache-status': 'DYNAMIC', 'content-encoding': 'gzip', 'server': 'cloudflare', 'cf-ray': 'a2c9d0392b986ceb-HKG'}, status_code: 404, body: {'message': 'not found', 'request_id': 'ca90eb5d-01d4-49e1-972b-ad5f95302690'} |
| E07 | mixed | FAIL | 365.3 | 0 | 100.0% | ApiError: headers: {'date': 'Mon, 17 Aug 2026 15:46:45 GMT', 'content-type': 'application/json; charset=utf-8', 'transfer-encoding': 'chunked', 'connection': 'keep-alive', 'vary': 'Origin', 'x-content-type-options': 'nosniff', 'x-ratelimit-increment': '1', 'x-ratelimit-limit': '300', 'x-ratelimit-remaining': '284', 'x-ratelimit-reset': '1786981620', 'strict-transport-security': 'max-age=2592000', 'cf-cache-status': 'DYNAMIC', 'content-encoding': 'gzip', 'server': 'cloudflare', 'cf-ray': 'a2c9d03bdc6b6ceb-HKG'}, status_code: 404, body: {'message': 'user not found', 'request_id': '1e2a3a45-9e90-4465-a3c6-c5c2ded6d49a'} |
| E11 | semantic | PASS | 237.6 | 125 | 77.9% |  |
| E08 | long_term | FAIL | 361.3 | 0 | 100.0% | ApiError: headers: {'date': 'Mon, 17 Aug 2026 15:46:46 GMT', 'content-type': 'application/json; charset=utf-8', 'transfer-encoding': 'chunked', 'connection': 'keep-alive', 'vary': 'Origin', 'x-content-type-options': 'nosniff', 'x-ratelimit-increment': '1', 'x-ratelimit-limit': '300', 'x-ratelimit-remaining': '281', 'x-ratelimit-reset': '1786981620', 'strict-transport-security': 'max-age=2592000', 'cf-cache-status': 'DYNAMIC', 'content-encoding': 'gzip', 'server': 'cloudflare', 'cf-ray': 'a2c9d03faff66ceb-HKG'}, status_code: 404, body: {'message': 'user not found', 'request_id': '0bb43c6f-0d5e-4e14-a009-1b78b53d6f10'} |

## Evidence excerpts

### E01 - short_term

`<RECENT_TURNS> user: Ten du an ca nhan cua toi la ORCHID-27. Toi thich Python va khong thich Java. Khi giai thich code, hay dung vi du ngan. assistant: Da hieu: demo ca nhan ORCHID-27, uu tien Python, tranh Java, vi du ngan. user: Toi dang hoc async/await va hay nham coroutine voi Task. Neu sau nay gap chu de nay, hay giai thich bang timeline. assistant: Toi se uu tien timeline khi giai thich coroutine va Task. user: TODO: hoan thanh benchmark report truoc thu Sau luc 16:00. Day la open loop LAB-REPORT-1600. </RECENT_TURNS>`

### E06 - semantic

`EPISODE: {"id":"kb-payment-retry","entity":"Payment API Retry Policy","summary":"For POST /payments, every retryable request MUST send the same Idempotency-Key. Retry only HTTP 429 or transient 5xx errors, use exponential-backoff, and stop after max-3-retries. Marker: PAYMENT-RULE-3.","so EPISODE: For POST /payments, every retryable request MUST send the same Idempotency-Key. Retry only HTTP 429 or transient 5xx errors, use exponential-backoff, and stop after max-3-retries. Marker: PAYMENT-RULE-3.`

### E09 - long_term

`<USER_SUMMARY> The user's project is LOTUS-88. They prioritize Java and Spring Boot for backend development and do not use Python for backend. </USER_SUMMARY>  <EPISODES> Episodes are source message or document excerpts shown in selection order.   - Created At: 2026-08-01 11:00:20     Source: message     Content: Lab Assistant (assistant): Da hieu: LOTUS-88, Java + Spring Boot cho backend examples.   - Created At: 2026-08-01 11:00:00     Source: message     Content: [user] {   "user_id": "lan-lab17",   "first_name": "Lan",   "last_name": "Tran",   "user_alias": "Lan Tran" }: Toi la Lan. Du an cua toi la LOTUS-88. Toi uu tien Java va Spring Boot, va khong dung Python trong vi du backend. </EP`

### E10 - short_term

`<SESSION_SUMMARY> user: Constraint: REVIEW-DEADLINE-1600 - project review is Friday at 16:00 and must not be forgotten. | assistant: Acknowledged review constraint. | user: Filler turn 1 about UI spacing. | assistant: Filler answer 1. | user: Filler turn 2 about naming. | assistant: Filler answer 2. | user: Filler turn 3 about logging. | assistant: Filler answer 3. </SESSION_SUMMARY> <DURABLE_NOTES> - user: Constraint: REVIEW-DEADLINE-1600 - project review is Friday at 16:00 and must not be forgotten. - assistant: Acknowledged review constraint. </DURABLE_NOTES> <RECENT_TURNS> user: Filler turn 4 about tests. assistant: Filler answer 4. user: Filler turn 5 about docs. assistant: Filler answe`

### E02 - long_term

``

### E03 - long_term

``

### E04 - episodic

``

### E05 - episodic

``

### E07 - mixed

``

### E11 - semantic

`EPISODE: {"id":"kb-async-http","entity":"Async HTTP Incident Playbook","summary":"When async HTTP calls time out, inspect connection pooling, downstream saturation and concurrency before increasing timeout. Reuse a long-lived client session where possible. Marker: CONN-POOL-FIRST.","sourc EPISODE: When async HTTP calls time out, inspect connection pooling, downstream saturation and concurrency before increasing timeout. Reuse a long-lived client session where possible. Marker: CONN-POOL-FIRST.`

### E08 - long_term

``
