# bounty-toolkit

Bug bounty / CTF toolkit workspace for Claude Code.

## Hack The Box MCP (CTF)

`.mcp.json` registers the HTB CTF MCP server (`htb-mcp-ctf`) at project scope.
The API token is **not** stored in the repo — it's read from `HTB_MCP_TOKEN`.

1. Create an API token in your HTB profile settings (App Tokens).
2. Export it before launching Claude Code:
   ```sh
   export HTB_MCP_TOKEN="<your token>"
   claude
   ```
3. Approve the project server when prompted, then check with `/mcp`.

Equivalent one-off CLI command (user-local, not committed):

```sh
claude mcp add --transport http htb-mcp-ctf https://mcp.hackthebox.ai/v1/ctf/mcp/ \
  --header "Authorization: Bearer $HTB_MCP_TOKEN"
```

For Claude Code on the web, add `HTB_MCP_TOKEN` as an environment variable/secret
in the cloud environment settings.

### VS Code

`.vscode/mcp.json` registers the same server using VS Code's `servers` format.
The token is a `promptString` input with `password: true`: VS Code asks for it
the first time the server starts and stores it securely. Don't replace
`${input:htb-api-token}` with the raw token, because this file is committed.
