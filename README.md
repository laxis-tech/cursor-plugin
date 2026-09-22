# Laxis

Cursor plugin that connects agents to [Laxis](https://www.laxis.com) through Laxis's official remote [Model Context Protocol](https://modelcontextprotocol.io/) server.

Laxis is an AI meeting note taker that records, transcribes, and summarizes your meetings on Zoom, Google Meet, Microsoft Teams, Webex, phone calls, and in person. This plugin lets agents browse your meetings, search across transcripts, and read full speaker-labeled transcripts from your own Laxis workspace.

## Install

1. Open **Cursor Settings → Plugins**.
2. Search for **Laxis**.
3. Click **Install**, then complete the Laxis sign-in prompt.

Or run `/add-plugin laxis` in chat.

## MCP

```json
{
  "mcpServers": {
    "laxis": {
      "type": "http",
      "url": "https://app.laxis.tech/mcp"
    }
  }
}
```

Auth is OAuth 2.1 against your Laxis account with Dynamic Client Registration and PKCE. Cursor registers itself and prompts for Laxis sign-in when the plugin connects. There is no API key or client ID to configure.

## What agents can do

| Category | Capabilities |
| --- | --- |
| Meetings | List your meetings with title, date, participants, keywords, and summary |
| Search | Semantic search across your transcripts, with the meeting and timestamp cited |
| Transcripts | Read complete, speaker-labeled transcripts page by page |

The hosted runtime is the source of truth for tool names and schemas. Call `list_meetings` as a read-only smoke test after connecting.

Typical workflows: turn a batch of customer calls into a status report, draft a follow-up email grounded in what was actually said, consolidate action items across meetings, or prep for a call by reviewing every past conversation with the same customer.

## Notes

- Tool calls run as the Laxis user who authorizes the connection and cannot exceed that user's permissions.
- All tools are read-only. The server never creates, modifies, or deletes anything in Laxis.
- Everything returned comes from recordings in your own Laxis workspace. The server does not fetch news, web pages, or third-party content.
- Requires a Laxis account on a Premium plan or higher (including Business team plans and AppSumo lifetime tiers with the MCP add-on).

## Docs

- Laxis help center: https://help.laxis.com
- Privacy policy: https://www.laxis.com/privacy
- Server URL: https://app.laxis.tech/mcp
- Support: support@laxis.tech

Logo is Laxis's official mark.

## License

MIT
