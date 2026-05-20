## 2024-05-17 - O(N) lookup optimizations for Discord.js
**Learning:** Found two O(N) operations in bot.js and module Tipper scripts when looking up members or guild count.
**Action:** Replaced `bot.guilds.array().length` with `bot.guilds.size` (O(1)) and `message.guild.members.find('id', recipient)` with `message.guild.members.get(recipient)` (O(1)).

## 2024-05-20 - Batching Discord API Calls
**Learning:** Sending multiple separate messages sequentially using `message.author.send()` (or similar Discord methods) is a network bottleneck and can trigger Discord rate limits. However, Discord has a hard limit of 2000 characters per message.
**Action:** When batching messages to reduce API calls, always verify the concatenated payload length. Group messages so each batched request stays comfortably under the 2000-character limit to balance performance and API compliance.
