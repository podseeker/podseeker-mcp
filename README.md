# Podseeker MCP server

Podseeker is the podcast database for getting clients booked. This remote MCP server brings it into Claude, ChatGPT, Cursor and any other MCP client, so you can research podcast guest spots in a conversation.

- **Search** active podcasts with the same filters as the Podseeker app: topic, guest-friendly shows, booking difficulty, listener estimates, audience location and recent episodes.
- **Open a show's profile:** hosts, recent guests, how hard it is to book, and known contacts (host and producer emails, contact forms).
- **Find contacts** for a show that has none on file.
- **Match podcasts to a client:** add the person you're booking and get recommendations, each with a Client Fit rating and the reason.
- **Save shortlists** as media lists. Clients and media lists are the same ones your team sees in the Podseeker app.

The server doesn't send email. Pitching stays in the Podseeker app.

## Server URL

```
https://app.podseeker.co/mcp
```

Remote server over Streamable HTTP. Sign in with OAuth (Claude, ChatGPT) or an API key (`Authorization: Bearer ps_...`). It runs on your organization's Podseeker API plan: [plans](https://www.podseeker.co/podcast-api). New accounts start with free API credits.

## Connect

- **Claude (claude.ai and Claude Desktop):** Settings → Customize → Connectors → Add → Custom connector. Name it Podseeker, paste the server URL, then click Connect and approve in the Podseeker window that opens.
- **ChatGPT:** open chatgpt.com/plugins, click Add → Add custom MCP server, name it Podseeker, paste the server URL, choose OAuth and confirm. Click Connect and approve in the Podseeker window. In a new chat, type `@` and pick Podseeker.
- **Claude Code:**
  ```
  claude mcp add --transport http podseeker https://app.podseeker.co/mcp --header "Authorization: Bearer ps_your_key"
  ```
- **Cursor and other MCP clients:** add the server URL as a remote (Streamable HTTP) server with the header `Authorization: Bearer ps_your_key`. Example config: [`.mcp.json`](.mcp.json).

Create an API key at [app.podseeker.co/api](https://app.podseeker.co/api).

## Tools

| Tool | What it does |
|---|---|
| `search_podcasts` | Search podcasts by topic and filters |
| `get_podcast` | A show's full profile and known contacts |
| `lookup_podcast` | Find a show by its Apple Podcasts ID |
| `similar_podcasts` | Shows similar to a given podcast |
| `enrich_podcast_contacts` | Search for contacts when a show has none on file |
| `get_enrichment` | Check a contact search |
| `list_clients`, `get_client`, `create_client`, `update_client` | The people you're booking |
| `recommend_podcasts`, `get_recommendations` | Podcast recommendations for a client, with Client Fit |
| `list_media_lists`, `get_media_list`, `create_media_list`, `update_media_list` | Shortlists your team shares |
| `add_to_media_list`, `remove_from_media_list` | Add or remove shows on a list |
| `get_usage` | Your API credit balance |

Each tool uses the same credits as its API endpoint; clients, media lists and usage are free. Keep a person in the loop before anything is sent.

## Links

- [API and MCP documentation](https://app.podseeker.co/api/docs#ai-assistants)
- [Podseeker API plans](https://www.podseeker.co/podcast-api)
- [Privacy policy](https://www.podseeker.co/privacy)
- Official MCP Registry: `co.podseeker/podseeker`
- Support: support@podseeker.co

This repository holds the server's public description only. The server is hosted by Podseeker; there is nothing to install.
