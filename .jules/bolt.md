## 2024-05-17 - O(N) lookup optimizations for Discord.js
**Learning:** Found two O(N) operations in bot.js and module Tipper scripts when looking up members or guild count.
**Action:** Replaced `bot.guilds.array().length` with `bot.guilds.size` (O(1)) and `message.guild.members.find('id', recipient)` with `message.guild.members.get(recipient)` (O(1)).
## 2026-05-28 - Token extraction optimization using match
**Learning:** Chaining `.trim().split(' ').filter(...)` for parsing command arguments creates intermediate arrays and is slower.
**Action:** Replaced `.trim().split(' ').filter(...)` with `.match(/\S+/g) || []` to extract tokens more efficiently and robustly (handling various whitespace characters) across `*Tipper.js` modules. This significantly reduces memory allocations and execution time.
