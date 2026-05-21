## 2024-05-17 - O(N) lookup optimizations for Discord.js
**Learning:** Found two O(N) operations in bot.js and module Tipper scripts when looking up members or guild count.
**Action:** Replaced `bot.guilds.array().length` with `bot.guilds.size` (O(1)) and `message.guild.members.find('id', recipient)` with `message.guild.members.get(recipient)` (O(1)).

## 2024-05-23 - Batching Discord API Calls with Message Length Constraints
**Learning:** Discord has strict rate limits for sending messages, and a hard maximum length of 2000 characters per message. If multiple separate small messages are sent sequentially, it introduces significant network latency and risks hitting rate limits (e.g. `tiphelp` sending 7 separate messages).
**Action:** When sending multiple pieces of static text or data sequentially, batch them into the fewest possible messages by concatenating them, while strictly ensuring the resulting strings stay under the 2000 character limit to avoid API rejection.
