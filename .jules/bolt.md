## 2024-05-17 - O(N) lookup optimizations for Discord.js
**Learning:** Found two O(N) operations in bot.js and module Tipper scripts when looking up members or guild count.
**Action:** Replaced `bot.guilds.array().length` with `bot.guilds.size` (O(1)) and `message.guild.members.find('id', recipient)` with `message.guild.members.get(recipient)` (O(1)).
## 2026-05-29 - Optimize string splitting
**Learning:** Found an inefficient string splitting mechanism using chained `.trim().split(' ').filter(function (n) { return n !== ''; })` throughout module commands to extract arguments.
**Action:** Replaced chained methods with a more efficient regex based `msg.content.match(/\S+/g) || []` to reduce intermediate array allocation.
