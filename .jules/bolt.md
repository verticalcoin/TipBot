## 2023-10-27 - Batching Discord API Calls
**Learning:** Sending multiple individual messages via Discord.js is a significant performance bottleneck due to network latency and rate limits. However, Discord enforces a strict 2000-character limit per message.
**Action:** Always batch multiple message sends into single payloads to reduce API requests, but calculate string lengths carefully to split payloads that exceed 2000 characters.
