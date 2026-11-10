# Client Setup and Troubleshooting

## Connection values

| Field | Value |
| --- | --- |
| Name | `Vbnote` |
| Type | `HTTP` or `Streamable HTTP` |
| URL | `https://4a08142c38dbe374195d41c04562d9f8.nebulab.app/mcp` |
| Headers | Leave blank |
| OAuth Client ID | Leave blank |
| OAuth callback port | Leave blank |
| OAuth scopes | Leave blank |
| Timeout | `180` seconds |

## Verify the service

The health endpoint is public and does not expose private data:

```bash
curl -fsS https://4a08142c38dbe374195d41c04562d9f8.nebulab.app/health
```

Expected response:

```json
{"ok":true,"service":"owll-mcp-server"}
```

## Verify tool discovery

After authorization, use the client's MCP server or tool list and confirm that Vbnote tools are present. Then start with a low-risk read request:

```text
Use Vbnote to count my notes.
```

## Troubleshooting checklist

1. Confirm the endpoint uses HTTPS and ends with `/mcp`.
2. Confirm the server is enabled for the current Copilot session or agent harness.
3. Complete the browser authorization flow.
4. Restart or reconnect the MCP server after authorization.
5. Check organization policies if the server is hidden or blocked.
6. Capture the client name, version, visible error message, and request ID before reporting a problem.

Do not attach tokens, private note text, or transcript download URLs to public issues.
