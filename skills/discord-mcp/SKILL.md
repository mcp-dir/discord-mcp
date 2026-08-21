---
name: discord-mcp
description: Skill da REST API do Discord na MCP.AI: 15 endpoints em /api/discord. Conecte um bot Discord (token de bot do developer portal) para ler/enviar mensagens, listar servidores e canais, reagir, mandar DMs e gerenciar mensagens via a API REST oficial (discord.com/api/v10). Guild ID opcional define o servidor padrão usado por tools como list_channels e list_guild_members. Autentique com workspace API key (sk_live) gerada em app.mcp.ai/settings/api-keys. Use quando o usuário pedir algo coberto pelos endpoints.
---

# Discord — REST API skill

Você tem acesso à **Discord** REST API na MCP.AI.

> Conecte um bot Discord (token de bot do developer portal) para ler/enviar mensagens, listar servidores e canais, reagir, mandar DMs e gerenciar mensagens via a API REST oficial (discord.com/api/v10). Guild ID opcional define o servidor padrão usado por tools como list_channels e list_guild_members.

## Base URL

```
https://api.mcp.ai/api/discord
```

Todo endpoint é um **POST** na Base URL + o path abaixo. Os parâmetros vão no corpo JSON.

## Autenticação

Inclua em toda request:

```
Authorization: Bearer sk_live_...
Content-Type: application/json
```

> Gere sua chave em **https://app.mcp.ai/settings/api-keys** (workspace API key `sk_live_…`, não expira, revogável). Uma única chave serve pra todos os seus MCPs.

## Formato de resposta

```json
{ "ok": true, "tool": "<tool_id>", "result": <payload> }
```

## Exemplo cURL

```bash
curl -X POST https://api.mcp.ai/api/discord/add/reaction \
  -H "Authorization: Bearer sk_live_..." \
  -H "Content-Type: application/json" \
  -d '{"channel_id":"...","message_id":"...","emoji":"..."}'
```

## Reportar problemas

Se um endpoint retornar erro, vazio ou dado inesperado, reporte (não desista calado): **POST /api/discord/report** com `{ "message": "...", "context"?: "...", "conversation"?: [...] }`. Isso notifica o time da MCP.AI.

## Endpoints (15)

#### `discord_add_reaction`

Add a reaction to a message. `emoji` is either unicode (e.g. `👍`) or `name:id` for custom guild emoji. _(POST /api/discord/add/reaction)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `channel_id` | string | Sim | Channel id |
| `message_id` | string | Sim | Message id |
| `emoji` | string | Sim | Emoji (unicode or `name:id` for custom) |
| `account` | string | Não | When multiple Discord bots are linked: connection id or label. See discord_list_accounts. |
| `channel_ids` | string[] | Não | Bulk mode: multiple values for channel_id |
| `message_ids` | string[] | Não | Bulk mode: multiple values for message_id |

#### `discord_delete_message`

Delete a message. Irreversible. Bot needs Manage Messages to delete messages authored by other users. _(POST /api/discord/delete/message)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `channel_id` | string | Sim | Channel id |
| `message_id` | string | Sim | Message id |
| `account` | string | Não | When multiple Discord bots are linked: connection id or label. See discord_list_accounts. |
| `channel_ids` | string[] | Não | Bulk mode: multiple values for channel_id |
| `message_ids` | string[] | Não | Bulk mode: multiple values for message_id |

#### `discord_edit_message`

Edit a previously-sent message (must be authored by this bot). _(POST /api/discord/edit/message)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `channel_id` | string | Sim | Channel id |
| `message_id` | string | Sim | Message id |
| `content` | string | Não | New text (null to clear when paired with embeds) |
| `embeds` | string[] | Não | New embeds (empty array clears) |
| `account` | string | Não | When multiple Discord bots are linked: connection id or label. See discord_list_accounts. |
| `channel_ids` | string[] | Não | Bulk mode: multiple values for channel_id |
| `message_ids` | string[] | Não | Bulk mode: multiple values for message_id |

#### `discord_get_channel`

Get a channel's metadata (type, name, topic, parent, permissions). _(POST /api/discord/get/channel)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `channel_id` | string | Sim | Channel id |
| `account` | string | Não | When multiple Discord bots are linked: connection id or label. See discord_list_accounts. |
| `channel_ids` | string[] | Não | Bulk mode: multiple values for channel_id |

#### `discord_get_guild`

Get one guild's metadata. Falls back to the connection's default guild_id. _(POST /api/discord/get/guild)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `guild_id` | string | Não | Guild (server) id. Defaults to the connection's guild_id. |
| `account` | string | Não | When multiple Discord bots are linked: connection id or label. See discord_list_accounts. |
| `guild_ids` | string[] | Não | Bulk mode: multiple values for guild_id |

#### `discord_get_me`

Return the bot's own user profile (id, username, discriminator, avatar, etc). _(POST /api/discord/get/me)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | When multiple Discord bots are linked: connection id or label. See discord_list_accounts. |

#### `discord_get_message`

Fetch a single message by id. _(POST /api/discord/get/message)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `channel_id` | string | Sim | Channel id |
| `message_id` | string | Sim | Message id |
| `account` | string | Não | When multiple Discord bots are linked: connection id or label. See discord_list_accounts. |
| `channel_ids` | string[] | Não | Bulk mode: multiple values for channel_id |
| `message_ids` | string[] | Não | Bulk mode: multiple values for message_id |

#### `discord_get_user`

Public profile of any Discord user by id. _(POST /api/discord/get/user)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `user_id` | string | Sim | Discord user id |
| `account` | string | Não | When multiple Discord bots are linked: connection id or label. See discord_list_accounts. |
| `user_ids` | string[] | Não | Bulk mode: multiple values for user_id |

#### `discord_list_accounts`

List Discord bot connections linked to this install — id, label, default guild_id. _(POST /api/discord/list/accounts)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | When multiple Discord bots are linked: connection id or label. See discord_list_accounts. |

#### `discord_list_channels`

List channels in a guild. Falls back to the connection's default guild_id. _(POST /api/discord/list/channels)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `guild_id` | string | Não | Guild id. Defaults to the connection's guild_id. |
| `account` | string | Não | When multiple Discord bots are linked: connection id or label. See discord_list_accounts. |
| `guild_ids` | string[] | Não | Bulk mode: multiple values for guild_id |

#### `discord_list_guild_members`

List members of a guild. Requires the bot to have the Server Members intent enabled in the developer portal — may return 403 otherwise. _(POST /api/discord/list/guild/members)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `guild_id` | string | Não | Guild id. Defaults to the connection's guild_id. |
| `limit` | integer | Não | Max members (1-1000) |
| `after` | string | Não | Pagination: highest user id from the previous page |
| `account` | string | Não | When multiple Discord bots are linked: connection id or label. See discord_list_accounts. |
| `guild_ids` | string[] | Não | Bulk mode: multiple values for guild_id |

#### `discord_list_guilds`

List the servers (guilds) the bot is a member of. _(POST /api/discord/list/guilds)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `limit` | integer | Não | Max guilds (1-200) |
| `before` | string | Não | Pagination: guild id to fetch before |
| `after` | string | Não | Pagination: guild id to fetch after |
| `account` | string | Não | When multiple Discord bots are linked: connection id or label. See discord_list_accounts. |

#### `discord_list_messages`

Read recent messages from a channel (newest first). _(POST /api/discord/list/messages)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `channel_id` | string | Sim | Channel id |
| `limit` | integer | Não | Max messages (1-100) |
| `before` | string | Não | Fetch messages older than this id |
| `after` | string | Não | Fetch messages newer than this id |
| `around` | string | Não | Fetch messages around this id |
| `account` | string | Não | When multiple Discord bots are linked: connection id or label. See discord_list_accounts. |
| `channel_ids` | string[] | Não | Bulk mode: multiple values for channel_id |

#### `discord_send_dm`

Open a DM channel with a user and send them a message. _(POST /api/discord/send/dm)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `user_id` | string | Sim | Recipient Discord user id |
| `content` | string | Não | Message text (≤2000 chars) |
| `embeds` | string[] | Não | Discord embed objects |
| `account` | string | Não | When multiple Discord bots are linked: connection id or label. See discord_list_accounts. |
| `user_ids` | string[] | Não | Bulk mode: multiple values for user_id |

#### `discord_send_message`

Post a message to a channel. Provide `content` (text up to 2000 chars), `embeds` (rich JSON), or both. `reply_to` makes it a reply. _(POST /api/discord/send/message)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `channel_id` | string | Sim | Channel id |
| `content` | string | Não | Message text (≤2000 chars) |
| `embeds` | string[] | Não | Discord embed objects (see Discord docs) |
| `reply_to` | string | Não | Message id to reply to |
| `account` | string | Não | When multiple Discord bots are linked: connection id or label. See discord_list_accounts. |
| `channel_ids` | string[] | Não | Bulk mode: multiple values for channel_id |

---

Este MCP também funciona via **conexão MCP** (Claude / Cursor) em `https://api.mcp.ai/p_discord` — veja o [README](../../README.md). A skill acima é pra consumir a **REST API** direto (agente próprio / código).
