# Contributing

This repository documents the hosted Vbnote MCP integration. Contributions should focus on discovery metadata, client setup, compatibility notes, and security documentation.

## Before opening a pull request

1. Do not include credentials, OAuth tokens, private notes, or transcripts.
2. Keep the remote endpoint based on `4a08142c38dbe374195d41c04562d9f8.nebulab.app` unless the maintainers announce a migration.
3. Validate `server.json`:

   ```bash
   mcp-publisher validate server.json
   ```

4. Check every documented command against the current client version.
5. Explain the user-facing impact of the change in the pull request.

The hosted service implementation is maintained separately, so implementation changes cannot be accepted in this metadata repository.
