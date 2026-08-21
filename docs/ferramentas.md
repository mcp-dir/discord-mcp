# Ferramentas

Discord expõe 15 ferramentas.

### 1. `discord_list_accounts`
**Input**: `account` (opcional)

List Discord bot connections linked to this install — id, label, default guild_id.

### 2. `discord_get_me`
**Input**: `account` (opcional)

Return the bot's own user profile (id, username, discriminator, avatar, etc).

### 3. `discord_list_guilds`
**Input**: `limit` (opcional), `before` (opcional), `after` (opcional), `account` (opcional)

List the servers (guilds) the bot is a member of.

### 4. `discord_get_guild`
**Input**: `guild_id` (opcional), `account` (opcional), `guild_ids` (opcional)

Get one guild's metadata. Falls back to the connection's default guild_id. Bulk support: accepts guild_ids for batched execution.

### 5. `discord_list_channels`
**Input**: `guild_id` (opcional), `account` (opcional), `guild_ids` (opcional)

List channels in a guild. Falls back to the connection's default guild_id. Bulk support: accepts guild_ids for batched execution.

### 6. `discord_list_guild_members`
**Input**: `guild_id` (opcional), `limit` (opcional), `after` (opcional), `account` (opcional), `guild_ids` (opcional)

List members of a guild. Requires the bot to have the Server Members intent enabled in the developer portal — may return 403 otherwise. Bulk support: accepts guild_ids for batched execution.

### 7. `discord_get_channel`
**Input**: `channel_id`, `account` (opcional), `channel_ids` (opcional)

Get a channel's metadata (type, name, topic, parent, permissions).

### 8. `discord_list_messages`
**Input**: `channel_id`, `limit` (opcional), `before` (opcional), `after` (opcional), `around` (opcional), `account` (opcional), `channel_ids` (opcional)

Read recent messages from a channel (newest first).

### 9. `discord_get_message`
**Input**: `channel_id`, `message_id`, `account` (opcional), `channel_ids` (opcional), `message_ids` (opcional)

Fetch a single message by id. Bulk support: accepts channel_ids, message_ids for batched execution.

### 10. `discord_get_user`
**Input**: `user_id`, `account` (opcional), `user_ids` (opcional)

Public profile of any Discord user by id.

### 11. `discord_send_message`
**Input**: `channel_id`, `content` (opcional), `embeds` (opcional), `reply_to` (opcional), `account` (opcional), `channel_ids` (opcional)

Post a message to a channel. Provide `content` (text up to 2000 chars), `embeds` (rich JSON), or both. `reply_to` makes it a reply. Bulk support: accepts channel_ids for batched execution.

### 12. `discord_send_dm`
**Input**: `user_id`, `content` (opcional), `embeds` (opcional), `account` (opcional), `user_ids` (opcional)

Open a DM channel with a user and send them a message.

### 13. `discord_edit_message`
**Input**: `channel_id`, `message_id`, `content` (opcional), `embeds` (opcional), `account` (opcional), `channel_ids` (opcional), `message_ids` (opcional)

Edit a previously-sent message (must be authored by this bot).

### 14. `discord_add_reaction`
**Input**: `channel_id`, `message_id`, `emoji`, `account` (opcional), `channel_ids` (opcional), `message_ids` (opcional)

Add a reaction to a message. `emoji` is either unicode (e.g. `👍`) or `name:id` for custom guild emoji. Bulk support: accepts channel_ids, message_ids for batched execution.

### 15. `discord_delete_message`
**Input**: `channel_id`, `message_id`, `account` (opcional), `channel_ids` (opcional), `message_ids` (opcional)

Delete a message. Irreversible. Bot needs Manage Messages to delete messages authored by other users. Bulk support: accepts channel_ids, message_ids for batched execution.

## Prompts de exemplo

```
Mostre as últimas 20 mensagens do canal #geral
Envie no canal de avisos: 'Reunião às 15h hoje'
Liste todos os canais do servidor
```
