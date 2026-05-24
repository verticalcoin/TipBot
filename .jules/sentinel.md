## 2024-05-24 - Do Not Leak RPC Errors
**Vulnerability:** The application was replying to Discord users with raw RPC error messages via `message.reply(err.message)`.
**Learning:** This exposes internal error details which can leak sensitive information about the backend system or infrastructure.
**Prevention:** Always use generic error responses when catching exceptions to display to end-users. Also remember to append `.catch()` to discord API calls like `.reply()` to prevent unhandled promise rejections.
