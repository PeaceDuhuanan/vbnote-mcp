# Authentication

Vbnote protects private notes with OAuth user authorization. MCP clients discover the authorization server through the protected-resource metadata published by the remote service.

## Authorization flow

1. The MCP client connects to the remote `/mcp` endpoint.
2. An unauthenticated request receives HTTP `401` with a `WWW-Authenticate` challenge.
3. The client reads Vbnote's protected-resource metadata.
4. The client opens a browser so the user can sign in and approve access.
5. The client retries the MCP request with a Bearer access token.

## Client configuration

For clients that implement MCP OAuth discovery, configure only the remote URL:

```text
https://4a08142c38dbe374195d41c04562d9f8.nebulab.app/mcp
```

Leave OAuth Client ID, callback port, scopes, and static headers blank unless Vbnote support gives you client-specific values. In particular, do not force callback port `80`; clients normally select an available loopback port.

## Token safety

- Never commit access or refresh tokens.
- Never put tokens in an MCP URL or issue report.
- Complete authorization only on the expected Vbnote/Owll login page opened by the client.
- Disconnect the server in the MCP client if a device is lost or no longer trusted.
- Reauthorize when the client reports that authorization expired or was revoked.

## Common errors

### `invalid_redirect_uri`

The authorization server rejected the callback URI used by the client. Leave the callback-port field blank first. If the error continues, report the client name, version, and exact callback host without including tokens.

### `401 Unauthorized`

The client has no valid token, the token expired, or the selected session has not completed authorization. Use the client's **Auth**, **Sign in**, or **Reconnect** action.

### Permission denied while starting OAuth

The client could not open or bind its local callback listener. Choose a non-privileged dynamic port, check local firewall permissions, and retry without port `80`.
