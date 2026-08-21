# Discord

### Discord para Claude, ChatGPT e agentes de IA

Conecte um bot Discord (token de bot do developer portal) para ler/enviar mensagens, listar servidores e canais, reagir, mandar DMs e gerenciar mensagens via a API REST oficial (discord.com/api/v10). Guild ID opcional define o servidor padrão usado por tools como list_channels e list_guild_members.

- 📊 **15 ferramentas**
- ✏️ **Leitura e escrita**
- 💬 **Funciona com qualquer cliente MCP**: Claude Desktop, Cursor, VS Code, Cline, Continue
- 🔑 **Login via magic-link (sem senha)**

[English version](README.en.md) · [Documentação completa](docs/) · [Skill pra agentes](skills/)

---

## Instalar em 1 clique

### Claude (Web e Desktop)

A Anthropic unificou a instalação de MCPs em `claude.ai/customize/connectors`. **O mesmo link serve pra Claude Web e Claude Desktop** (basta estar logado):

[➕ Abrir no Claude e conectar](https://claude.ai/new?modal=add-custom-connector#settings/customize-connectors)

**Manual** (se o deeplink não abrir): [claude.ai/customize/connectors](https://claude.ai/customize/connectors?surface=cowork) → **+** → **Adicionar conector personalizado** → cole **Nome** `Discord` e **URL** `https://api.mcp.ai/p_discord`.

### Cursor

[➕ Instalar Discord no Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=discord&config=eyJ1cmwiOiJodHRwczovL2FwaS5tY3AuYWkvcF9kaXNjb3JkIn0=)

### VS Code (Copilot Chat)

[➕ Instalar Discord no VS Code](vscode:mcp/install?name=discord&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.mcp.ai%2Fp_discord%22%7D)

### ChatGPT, Manus, OpenClaw e mais 40+ clientes

Funciona em qualquer cliente MCP que suporte **MCP over HTTP**. A URL do servidor é sempre:

```
https://api.mcp.ai/p_discord
```

Detalhes por cliente: [INSTALL.md](INSTALL.md).

---

## Exemplos de uso

```
Mostre as últimas 20 mensagens do canal #geral
Envie no canal de avisos: 'Reunião às 15h hoje'
Liste todos os canais do servidor
```

---

## 15 ferramentas disponíveis

| Tool | Descrição |
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

Detalhe de cada tool: [docs/ferramentas.md](docs/ferramentas.md)

---

## Preços

Grátis.

---

## Privacidade & LGPD

- **Sub-processadores**: o LLM host que você escolher (Claude, ChatGPT, Cursor, agente próprio). Lista completa em [docs/privacidade-lgpd.md](docs/privacidade-lgpd.md).
- Os dados retornados pelas tools são enviados ao **LLM host que você escolher**, sub-processador fora do nosso controle. Recomendamos planos com opt-out de treinamento.

---

## Perguntas frequentes

**O servidor é open source?**
O servidor é proprietário (hosted). Este repositório é o wrapper público com manifestos, docs e skills — tudo MIT.

**Posso usar com agente próprio (não Claude/Cursor)?**
Sim — qualquer cliente que suporte MCP over HTTP. URL: `https://api.mcp.ai/p_discord`.


---

## Suporte

- 📧 [discord@mcp.ai](mailto:discord@mcp.ai)
- 🐛 [GitHub Issues](https://github.com/mcp-dir/discord-mcp/issues)
- 📄 [docs/](docs/)

---

## Licença

MIT — veja [LICENSE](LICENSE). O servidor MCP em `api.mcp.ai/p_discord` é proprietário (hosted); este repositório (manifestos, docs, skills) é MIT.
