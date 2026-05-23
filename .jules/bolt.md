## 2024-05-23 - Batching Discord API Calls
**Learning:** The Discord API rate limits and constraints (2000 characters per message) significantly impact bot performance when sending multiple individual messages.
**Action:** Always batch outbound Discord messages together into chunks under 2000 characters to minimize the number of API requests, particularly in commands that output large amounts of static or dynamic text (like help commands).
