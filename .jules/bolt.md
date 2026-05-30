## 2024-05-17 - O(N) lookup optimizations for Discord.js
**Learning:** Found two O(N) operations in bot.js and module Tipper scripts when looking up members or guild count.
**Action:** Replaced `bot.guilds.array().length` with `bot.guilds.size` (O(1)) and `message.guild.members.find('id', recipient)` with `message.guild.members.get(recipient)` (O(1)).

## 2024-05-17 - Avoid Intermediate Array Allocations in Message Parsing
**Learning:** Found an inefficient pattern for tokenizing messages (`msg.content.trim().split(' ').filter(...)`) which creates multiple intermediate array allocations.
**Action:** Replaced with `msg.content.match(/\S+/g) || []` to efficiently extract tokens while avoiding unnecessary allocations, improving performance particularly on busy servers.
