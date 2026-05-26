## 2024-05-26 - Internal RPC Error Leakage
**Vulnerability:** Internal RPC error messages generated from cryptocurrency daemon requests (e.g. insufficient funds, daemon connection error) were sent directly back to the user via Discord API using `message.reply(err.message)`.
**Learning:** These error messages could contain internal configuration paths, addresses or IP addresses, and exact internal node state. The vulnerability was found across multiple dynamic bot modules.
**Prevention:** Catch all RPC errors and return generic messaging (e.g. "An internal error occurred.") to Discord users, preventing sensitive state disclosure.
