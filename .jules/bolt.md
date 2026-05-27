## 2024-05-17 - O(N) lookup optimizations for Discord.js
**Learning:** Found two O(N) operations in bot.js and module Tipper scripts when looking up members or guild count.
**Action:** Replaced `bot.guilds.array().length` with `bot.guilds.size` (O(1)) and `message.guild.members.find('id', recipient)` with `message.guild.members.get(recipient)` (O(1)).

## 2024-05-27 - Optimize message parsing allocations
**Learning:** Found multiple instances where strings were parsed using `.trim().split(' ').filter(function (n) { return n !== ''; })`. This is inefficient as it allocates arrays of intermediate space tokens.
**Action:** Replaced `.trim().split(' ').filter(...)` and similar uses of `.split(' ')` with `.match(/\S+/g) || []`. This extracts non-whitespace sequences directly without allocating intermediate space token strings.
