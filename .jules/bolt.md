## 2024-05-17 - O(N) lookup optimizations for Discord.js
**Learning:** Found two O(N) operations in bot.js and module Tipper scripts when looking up members or guild count.
**Action:** Replaced `bot.guilds.array().length` with `bot.guilds.size` (O(1)) and `message.guild.members.find('id', recipient)` with `message.guild.members.get(recipient)` (O(1)).
## 2023-10-27 - [Optimized Message Parsing in Tipper Modules]
**Learning:** Using `.split(' ').filter(n => n !== '')` to parse words from strings is about 6x slower than using a regex split `.split(/\s+/)`. The former creates an array with empty strings for multiple spaces and then iterates again to filter them out, while the regex directly tokenizes correctly and more efficiently in a single pass.
**Action:** Replace `msg.content.trim().split(' ').filter(function (n) { return n !== ''; })` with `msg.content.trim().split(/\s+/)` in all Tipper modules to speed up command parsing without sacrificing readability.
