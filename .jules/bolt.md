## 2024-05-17 - O(N) lookup optimizations for Discord.js
**Learning:** Found two O(N) operations in bot.js and module Tipper scripts when looking up members or guild count.
**Action:** Replaced `bot.guilds.array().length` with `bot.guilds.size` (O(1)) and `message.guild.members.find('id', recipient)` with `message.guild.members.get(recipient)` (O(1)).

## 2024-05-24 - Message Parsing Optimization
**Learning:** The command parser in module tippers was using `msg.content.trim().split(' ').filter(n => n !== '')` which involves creating multiple intermediate arrays and function calls.
**Action:** Replace string splitting + filtering with `msg.content.trim().split(/\s+/)` to parse commands faster and reduce memory allocations/garbage collection overhead.
