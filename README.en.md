# Discord

### Discord for Claude, ChatGPT and AI agents

Connect a Discord bot (bot token from the developer portal) to read/send messages, list guilds and channels, react, send DMs and manage messages via the official REST API (discord.com/api/v10). Optional Guild ID sets the default server used by tools like list_channels and list_guild_members.

- 📊 **15 tools**
- ✏️ **Read and write**
- 💬 **Works with any MCP client**: Claude Desktop, Cursor, VS Code, Cline, Continue
- 🔑 **Magic-link login (no password)**

[Portuguese version](README.md) · [Full docs (PT-BR)](docs/)

---

## One-click install

### Claude (Web and Desktop)

[➕ Open in Claude and connect](https://claude.ai/new?modal=add-custom-connector#settings/customize-connectors)

Manual: [claude.ai/customize/connectors](https://claude.ai/customize/connectors?surface=cowork) → **+** → **Add custom connector** → name `Discord`, URL `https://api.mcp.ai/p_discord`.

### Cursor

[➕ Install in Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=discord&config=eyJ1cmwiOiJodHRwczovL2FwaS5tY3AuYWkvcF9kaXNjb3JkIn0=)

### VS Code (Copilot Chat)

[➕ Install in VS Code](vscode:mcp/install?name=discord&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.mcp.ai%2Fp_discord%22%7D)

### Any other MCP-over-HTTP client

```
https://api.mcp.ai/p_discord
```

---

## 15 tools

| Tool | Description |
|---|---|
| `discord_list_accounts` | List Discord bot connections linked to this install — id, label, default guild_id. |
| `discord_get_me` | Return the bot's own user profile (id, username, discriminator, avatar, etc). |
| `discord_list_guilds` | List the servers (guilds) the bot is a member of. |
| `discord_get_guild` | Get one guild's metadata. Falls back to the connection's default guild_id. Bulk support: accepts guild_ids for batched execution. |
| `discord_list_channels` | List channels in a guild. Falls back to the connection's default guild_id. Bulk support: accepts guild_ids for batched execution. |
| `discord_list_guild_members` | List members of a guild. Requires the bot to have the Server Members intent enabled in the developer portal — may return 403 otherwise. Bulk support: accepts guild_ids for batched execution. |
| `discord_get_channel` | Get a channel's metadata (type, name, topic, parent, permissions). |
| `discord_list_messages` | Read recent messages from a channel (newest first). |
| `discord_get_message` | Fetch a single message by id. Bulk support: accepts channel_ids, message_ids for batched execution. |
| `discord_get_user` | Public profile of any Discord user by id. |
| `discord_send_message` | Post a message to a channel. Provide `content` (text up to 2000 chars), `embeds` (rich JSON), or both. `reply_to` makes it a reply. Bulk support: accepts channel_ids for batched execution. |
| `discord_send_dm` | Open a DM channel with a user and send them a message. |
| `discord_edit_message` | Edit a previously-sent message (must be authored by this bot). |
| `discord_add_reaction` | Add a reaction to a message. `emoji` is either unicode (e.g. `👍`) or `name:id` for custom guild emoji. Bulk support: accepts channel_ids, message_ids for batched execution. |
| `discord_delete_message` | Delete a message. Irreversible. Bot needs Manage Messages to delete messages authored by other users. Bulk support: accepts channel_ids, message_ids for batched execution. |

---

## Pricing

Free.

---

## License

MIT — see [LICENSE](LICENSE). The MCP server at `api.mcp.ai/p_discord` is proprietary (hosted); this repo (manifests, docs, skills) is MIT.
