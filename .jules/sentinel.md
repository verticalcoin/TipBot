
## 2023-10-27 - Information Exposure via RPC Errors
**Vulnerability:** The application was passing `err.message` directly back to users in Discord via `message.reply(err.message)` when cryptocurrency RPC commands failed (like transactions).
**Learning:** Internal component errors (like RPC node issues, database failures) should never be exposed directly to users, as they may leak internal infrastructure details, IP addresses, paths, or connection configurations.
**Prevention:** Catch errors, log them internally for developers (`console.error(err)`), and return a generic failure message to users.
