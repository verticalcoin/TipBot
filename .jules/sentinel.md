## 2024-05-24 - [Information Disclosure Prevention]
**Vulnerability:** Raw RPC daemon errors were being passed directly to Discord users via `message.reply(err.message)`.
**Learning:** These error messages could expose internal IP addresses, ports, daemon states, or stack traces, creating a security risk.
**Prevention:** Ensured all RPC error replies are caught and a generic error (`An internal error occurred. Please try again later.`) is returned instead.
