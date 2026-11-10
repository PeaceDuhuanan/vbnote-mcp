# Security Policy

## Supported versions

Security fixes are applied to the latest active Vbnote MCP version published in the official MCP Registry.

## Report a vulnerability

Do not open a public issue for suspected vulnerabilities, exposed credentials, authorization bypasses, or private-note data exposure.

Use [GitHub private vulnerability reporting](https://github.com/PeaceDuhuanan/vbnote-mcp/security/advisories/new) and include:

- A concise description of the issue and its impact.
- The affected endpoint, client, and MCP server version.
- Reproduction steps or a minimal proof of concept.
- Relevant request IDs with tokens and private note content removed.
- Any suggested mitigation.

Never include access tokens, refresh tokens, passwords, complete transcripts, or other users' private data in a report.

## Security boundaries

- The hosted MCP endpoint requires user authorization before private tools can be called.
- Tokens are expected in the `Authorization: Bearer` header and must not be placed in URLs.
- Note tools are read-only. The feedback tool is the only write operation and should run only after an explicit user request.
- Tool responses can contain private note content. The MCP client and model host may retain that content according to their own policies.
- Service audit records contain operational metadata such as request ID, user ID, tool name, status, and latency; they are designed not to record raw MCP requests or note content.

## Out of scope

Reports about the Vbnote product that are unrelated to MCP integration should use the product's normal support channel. General feature requests can be opened as public GitHub issues when they contain no sensitive information.
