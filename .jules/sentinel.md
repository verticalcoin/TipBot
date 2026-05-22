## 2024-05-24 - Unhandled Promise Rejections in Discord API calls
**Vulnerability:** Discord API calls like `message.delete()` and `message.reply()` often lack `.catch()` handlers.
**Learning:** If the bot tries to delete a message it doesn't have permission to, or if the message has already been deleted, it causes an unhandled promise rejection which can crash the entire Node.js process (depending on Node.js version and configuration).
**Prevention:** Always append a `.catch(console.error)` (or similar silent catch) to Discord API promises that are not otherwise handled, especially for cleanup actions like `delete()`.
