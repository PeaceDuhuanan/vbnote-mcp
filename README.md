# Vbnote MCP Server

Connect GitHub Copilot and other MCP-compatible agents to your private Vbnote notes, summaries, folders, and transcripts.

- Website: [Vbnote MCP Server](https://4a08142c38dbe374195d41c04562d9f8.nebulab.app/)
- Remote endpoint: `https://4a08142c38dbe374195d41c04562d9f8.nebulab.app/mcp`
- Transport: Streamable HTTP
- Authentication: OAuth user authorization
- MCP Registry name: `io.github.PeaceDuhuanan/vbnote`

## What you can do

- Search notes by keyword, date range, source, content type, or folder.
- Browse recent notes without inventing a search query.
- Count matching notes without loading their contents.
- Read note metadata, existing summaries, and original transcripts.
- Export long transcripts as downloadable text files.
- Send feedback to the Owll team only when the user explicitly requests it.

All note-reading tools are read-only. `submit_owll_feedback` is the only tool that writes data, and clients can require confirmation before it runs.

## Add Vbnote to GitHub Copilot

### GitHub Copilot app

1. Open **Customize**.
2. Select **Add extension** → **MCP Server…**.
3. Set **Server name** to `Vbnote`.
4. Select **HTTP**.
5. Enter the endpoint:

   ```text
   https://4a08142c38dbe374195d41c04562d9f8.nebulab.app/mcp
   ```

6. Leave OAuth Client ID, callback port, scopes, and headers blank.
7. Select **Add server**, then complete the browser authorization flow when prompted.

### GitHub Copilot CLI

```bash
copilot mcp add --transport http vbnote https://4a08142c38dbe374195d41c04562d9f8.nebulab.app/mcp
```

Start a Copilot session and ask:

```text
Use Vbnote to list my recently updated notes.
```

## Add Vbnote to VS Code

Run **MCP: Add Server** from the Command Palette, choose **HTTP**, and enter the remote endpoint. You can also add this user or workspace configuration:

```json
{
  "servers": {
    "vbnote": {
      "type": "http",
      "url": "https://4a08142c38dbe374195d41c04562d9f8.nebulab.app/mcp"
    }
  }
}
```

Start the server from the editor and select **Auth** when VS Code asks you to sign in.

## Example requests

```text
List my recent notes.
Search my notes for Flutter performance.
How many meeting notes did I create last week?
Summarize the note about MCP authentication.
Show me the original transcript for that note.
Export these three transcripts as text files.
```

## Authentication and privacy

Vbnote uses OAuth to authorize access to a user's private library. The MCP endpoint returns an authorization challenge when no valid token is present. Do not paste access tokens into configuration files, issues, or support messages.

See:

- [Authentication](docs/authentication.md)
- [Data access and privacy](docs/privacy.md)
- [Client setup and troubleshooting](docs/clients.md)
- [Security policy](SECURITY.md)

## Service endpoints

| Purpose | URL |
| --- | --- |
| MCP | `https://4a08142c38dbe374195d41c04562d9f8.nebulab.app/mcp` |
| Health | `https://4a08142c38dbe374195d41c04562d9f8.nebulab.app/health` |
| OAuth protected-resource metadata | `https://4a08142c38dbe374195d41c04562d9f8.nebulab.app/.well-known/oauth-protected-resource/mcp` |
| Icon | `https://4a08142c38dbe374195d41c04562d9f8.nebulab.app/favicon.png` |

## Repository scope

This public repository contains discovery metadata, client setup instructions, and security documentation for the hosted Vbnote MCP service. The hosted service implementation and Vbnote backend are maintained in private repositories.

## Contributing

Documentation fixes and client compatibility reports are welcome. Read [CONTRIBUTING.md](CONTRIBUTING.md) before opening a pull request.

## License

The metadata and documentation in this repository are licensed under the [MIT License](LICENSE).
