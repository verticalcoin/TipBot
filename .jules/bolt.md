## 2024-05-17 - O(N) lookup optimizations for Discord.js
**Learning:** Found two O(N) operations in bot.js and module Tipper scripts when looking up members or guild count.
**Action:** Replaced `bot.guilds.array().length` with `bot.guilds.size` (O(1)) and `message.guild.members.find('id', recipient)` with `message.guild.members.get(recipient)` (O(1)).
## 2024-05-24 - Optimized split() over filter() and batched Discord API calls
**Learning:** Found two common patterns: 1) `msg.content.trim().split(' ').filter(n => n !== '')` which processes strings twice, and 2) consecutive API calls to `message.author.send` which increases latency and approaches rate limits.
**Action:** Replaced array splitting and filtering with regex `split(/\s+/)` to combine it in one step, saving operations. Combined multiple short Discord messages into fewer, larger messages while adhering to the 2000 character limit.
