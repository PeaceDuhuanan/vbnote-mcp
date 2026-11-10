# Data Access and Privacy

Vbnote MCP gives an AI client access to private notes only after the user authorizes the connection.

## Data the tools can return

Depending on the user's request and authorization, tool responses can contain:

- Note titles, timestamps, source types, folders, and other metadata.
- Search excerpts and existing note summaries.
- Original transcript text.
- Download links for exported transcript text files.

This data is private. Users should connect only MCP clients and model providers they trust.

## Write operations

Note browsing, search, count, metadata, summary, and transcript tools are read-only. `submit_owll_feedback` sends feedback to the Owll team and is the only write operation exposed by this MCP server. It should be called only after an explicit user request.

## Operational logging

The hosted service records operational audit fields such as request ID, user ID, tool name, status, and latency. It is designed not to log raw MCP request bodies or note content.

The connected MCP client or model provider may independently store prompts, tool arguments, and tool results. Review that provider's retention and privacy controls before using private notes.

## Safe usage

- Request only the notes needed for the current task.
- Prefer summaries or metadata when full transcripts are unnecessary.
- Avoid sharing exported transcript links outside the intended audience.
- Remove the MCP connection from clients you no longer use.
- Do not include private note content in public bug reports.
