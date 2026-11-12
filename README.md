<p align="center">
  <img src="images/blotato-logo.png" alt="Blotato" width="160">
</p>

<h1 align="center">Blotato MCP Server</h1>

<p align="center">
  <b>
  The official Model Context Protocol (MCP) server for Blotato. Create, schedule, and publish social posts from your AI assistant. Review analytics, reply to Instagram and Facebook comments and DMs, and run DM automations.
  </b>
</p>

<!-- Line 1 · Project -->
<p align="center">
  <a href="https://github.com/blotato/blotato-mcp"><img src="https://img.shields.io/badge/Official-Blotato-6D28D9" alt="Official Blotato Server"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-blue" alt="License: MIT"></a>
</p>

<!-- Line 2 · Protocol & access -->
<p align="center">
  <a href="https://modelcontextprotocol.io"><img src="https://img.shields.io/badge/Model_Context_Protocol-compatible-000000?logo=modelcontextprotocol&logoColor=white" alt="Model Context Protocol compatible"></a>
  <a href="server.json"><img src="https://img.shields.io/badge/MCP_Registry-com.blotato-000000?logo=modelcontextprotocol&logoColor=white" alt="MCP Registry: com.blotato"></a>
  <a href="https://help.blotato.com/api-and-mcp-concepts/authentication"><img src="https://img.shields.io/badge/Auth-OAuth_2.1%20%7C%20API%20key-2EBC4F" alt="Auth: OAuth 2.1 or API key"></a>
</p>

<!-- Line 3 · Native connectors -->
<p align="center">
  <a href="https://claude.ai/directory/blotato"><img src="https://img.shields.io/badge/Claude-Connector_directory-D97757?logo=claude&logoColor=white" alt="Listed in the Claude connector directory"></a>
  <a href="https://chatgpt.com/plugins/plugin_asdk_app_6ad1c468acb88191b46d69457b4f4f86"><img src="https://img.shields.io/badge/ChatGPT-Plugins_directory-10A37F" alt="Listed in the ChatGPT Plugins directory"></a>
</p>

<p align="center">
  <a href="https://help.blotato.com/start-with-an-ai-agent/mcp/setup"><b>Getting started</b></a> ·
  <a href="https://help.blotato.com/start-with-an-ai-agent/mcp/tools"><b>Tools reference</b></a> ·
  <a href="https://help.blotato.com/start-with-an-ai-agent/mcp/examples"><b>Example prompts</b></a> ·
  <a href="https://help.blotato.com"><b>Help center</b></a>
</p>

---

Blotato helps creators, marketers, and businesses manage their social media. With the Blotato MCP Server, you can:

* **Publish and schedule** posts to any connected account, right away, at a set time, or in your next open slot.
* **Manage your content calendar** by listing, moving, and deleting scheduled posts.
* **Answer comments and DMs** on Instagram and Facebook.
* **Run DM automations** that reply when someone comments on a post or sends a message.
* **Review analytics** and compare your top-performing posts.
* **Turn sources into posts** by extracting content from YouTube videos, articles, PDFs, and audio.
* **Create visuals** such as images, carousels, and videos from Blotato templates.

The server is hosted by Blotato at `https://mcp.blotato.com/mcp` and signs in with **OAuth 2.1** or a **Blotato API key**, so every action runs against your own Blotato account and the social accounts you've connected to it.

---

## Before you start

Check that you meet the following requirements before you set up the server:

* An active Blotato subscription. API and MCP access aren't included in the free trial. See [pricing](https://www.blotato.com/pricing).
* At least one social account connected in [Accounts](https://my.blotato.com/accounts). You can connect the server first, but publishing needs a connected account.
* Access to **the AI client of your choice**, and a browser to complete the OAuth 2.1 sign-in.
* For clients that use an API key instead of OAuth, a key from [Settings → API](https://my.blotato.com/settings/api). Generating a key during a trial ends the trial and starts billing.

---

## Quick start

Blotato is listed in the Claude and ChatGPT directories. Pick your client below to add it without editing any config.

<table align="center">
  <tr>
    <td align="center" width="220">
      <a href="https://claude.ai/directory/blotato">
        <img src="https://img.shields.io/badge/Claude-D97757?style=for-the-badge&logo=claude&logoColor=white" alt="Add to Claude"><br>
        <b>Add to Claude</b>
      </a>
      <br><sub>Schedule social posts and manage DMs from Claude.</sub>
    </td>
    <td align="center" width="220">
      <a href="https://chatgpt.com/plugins/plugin_asdk_app_6ad1c468acb88191b46d69457b4f4f86">
        <img src="https://img.shields.io/badge/ChatGPT-10A37F?style=for-the-badge" alt="Add to ChatGPT"><br>
        <b>Add to ChatGPT</b>
      </a>
      <br><sub>Schedule social posts and manage DMs from ChatGPT.</sub>
    </td>
  </tr>
</table>

### Let your agent do the setup

Ask your coding agent to configure the server and guide you through sign-in.

```
Set up Blotato MCP for this agent using the official setup guide at
https://help.blotato.com/start-with-an-ai-agent/mcp/setup
and the MCP server URL https://mcp.blotato.com/mcp. Then start the Blotato
authentication flow so I can sign in, and verify the connection by calling
blotato_list_accounts.
```

Or add the server manually with your client's own command:

| Client | Command or configuration |
| --- | --- |
| Claude Code | `claude mcp add --transport http blotato https://mcp.blotato.com/mcp`, then run `/mcp` in a session to authenticate |
| Claude.ai, Desktop, and Cowork | **Customize → Connectors → Browse connectors**, then search for **Blotato** |
| ChatGPT.com, Desktop, and Codex | **Plugins**, then search for **Blotato** and choose **Install plugin** |
| Codex CLI | `codex mcp add blotato --url https://mcp.blotato.com/mcp`, then `codex mcp login blotato` |
| Cursor | Add the server to `~/.cursor/mcp.json` with a `blotato-api-key` header ([guide](https://help.blotato.com/start-with-an-ai-agent/mcp/setup#cursor)) |
| VS Code | Add the server to `.vscode/mcp.json` with a `blotato-api-key` header ([guide](https://help.blotato.com/start-with-an-ai-agent/mcp/setup#vs-code)) |
| Any other MCP client | Use the server URL `https://mcp.blotato.com/mcp` |

After setup, ask your client to list your connected Blotato accounts. A list of accounts, or an empty list, means the connection works.

> [!TIP]
> For step-by-step setup for each client, see [Connect your AI client](https://help.blotato.com/start-with-an-ai-agent/mcp/setup). You can also open [Settings → API](https://my.blotato.com/settings/api) in Blotato for a client selector.

---

## Example workflows

Once connected, you can run tasks like these from your client.

### Publishing and scheduling

* "Post 'Live Q&A tonight. Drop your questions in the comments' to my LinkedIn tomorrow at 10am."
* "Schedule this LinkedIn post for Tuesday at 9am Eastern and put the other two in my next open slots."

### Content calendar

* "What goes out next week? Move Thursday's post to Friday."
* "Move all my posts scheduled for Friday to Monday at the same times."

### Comments and DMs

* "Reply to the new comments on yesterday's Instagram post."
* "When someone comments GUIDE on any of my Instagram posts, DM them asking for their email, then DM them my guide."

### Content and visuals

* "Summarize this YouTube video in 2–3 sentences and give me three takeaways."
* "Create a LinkedIn and Facebook post about my product launch, with a newspaper infographic."

> [!NOTE]
> A publish call returns a receipt, not proof that the post went live. Ask your client to check the post with `blotato_get_post_status`. Scheduled posts report `scheduled` until their time comes.

For more, see [Example prompts](https://help.blotato.com/start-with-an-ai-agent/mcp/examples).

---

## Supported platforms

| Platform | Posts | Analytics | Comments | DMs | Automations |
| --- | --- | --- | --- | --- | --- |
| X | ✅ | ✅ | - | - | - |
| Instagram | ✅ | ✅ | ✅ | ✅ | ✅ |
| Facebook | ✅ | ✅ | ✅ | ✅ | ✅ |
| LinkedIn | ✅ | - | - | - | - |
| TikTok | ✅ | ✅ | - | - | - |
| YouTube | ✅ | ✅ | - | - | - |
| Threads | ✅ | ✅ | - | - | - |
| Pinterest | ✅ | ✅ | - | - | - |
| Bluesky | ✅ | ✅ | - | - | - |
| Slack | ✅ | - | - | - | - |

## Tools

### Accounts

| Tool | Description |
| --- | --- |
| `blotato_get_user` | Get account info and verify connection |
| `blotato_list_accounts` | List connected social accounts and subaccounts |
| `blotato_list_pinterest_boards` | List a Pinterest account's boards for publishing pins |

### Credits

| Tool | Description |
| --- | --- |
| `blotato_get_credits` | Get remaining credits and current credit pricing |

### Publishing

| Tool | Description |
| --- | --- |
| `blotato_create_post` | Publish or schedule a post to a connected account |
| `blotato_get_post_status` | Check the status of a submitted post |
| `blotato_list_posts` | List scheduled, published, and failed posts |

### Content calendar

| Tool | Description |
| --- | --- |
| `blotato_list_schedules` | List upcoming scheduled posts |
| `blotato_get_schedule` | Get one scheduled post's details |
| `blotato_update_schedule` | Change a scheduled post's content or time |
| `blotato_delete_schedule` | Delete a scheduled post and cancel publishing |

### Analytics

| Tool | Description |
| --- | --- |
| `blotato_list_top_posts` | List top-ranked published posts |
| `blotato_get_post_analytics` | Get latest metrics and history for one post |

### Comments

| Tool | Description |
| --- | --- |
| `blotato_list_comments` | List comments on published posts |
| `blotato_get_comment` | Get a single comment by ID |
| `blotato_post_comment` | Comment on or reply to Instagram and Facebook posts |

### Messages

| Tool | Description |
| --- | --- |
| `blotato_list_conversations` | List DM conversations |
| `blotato_get_conversation` | Get a single conversation by ID |
| `blotato_list_messages` | List direct messages |
| `blotato_get_message` | Get a single message and its delivery status |
| `blotato_send_message` | Send a DM or private reply to a comment |

### DM automations

| Tool | Description |
| --- | --- |
| `blotato_create_automation` | Create a DM automation, saved as a draft |
| `blotato_list_automations` | List DM automations with selected metrics |
| `blotato_update_automation` | Update an automation's message, triggers, gates, or webhook |
| `blotato_update_automation_trigger` | Turn a single automation trigger on/off |
| `blotato_delete_automation` | Archive a DM automation and stop new runs |
| `blotato_list_automation_runs` | List an automation's runs |
| `blotato_list_automation_logs` | List automation run logs |
| `blotato_get_automation_analytics` | Get automation analytics/stats |

### Content extraction

| Tool | Description |
| --- | --- |
| `blotato_create_source` | Extract content from a URL or text |
| `blotato_get_source_status` | Check the status of a source extraction |

### Images and videos

| Tool | Description |
| --- | --- |
| `blotato_list_design_templates` | List templates for images, carousels, slideshows, and videos |
| `blotato_create_design` | Create an image, carousel, or video from a template |
| `blotato_get_design_status` | Check the status of a design |

### Media

| Tool | Description |
| --- | --- |
| `blotato_create_presigned_upload_url` | Get a URL for uploading a local file |

> [!NOTE]
> For every tool's parameters and behavior, see the [Tools reference](https://help.blotato.com/start-with-an-ai-agent/mcp/tools).

---

## How it works

### OAuth

1. Your client connects to the hosted server over Streamable HTTP:

   ```
   https://mcp.blotato.com/mcp
   ```

2. Clients that support OAuth open a browser sign-in. Sign in to the Blotato account you want the client to post from, then approve access.
3. Once connected, the client calls Blotato tools on your behalf, against the social accounts connected to that Blotato account.

### API key authentication

For clients that don't support OAuth, send your Blotato API key in a header. Use the full key, including any trailing `=` characters.

| Header | Value |
| --- | --- |
| `blotato-api-key` | `YOUR_API_KEY` |

Keep API keys in your personal client configuration, not in shared project files. See [Authentication](https://help.blotato.com/api-and-mcp-concepts/authentication).

---

## Repository contents

The server itself runs as a hosted service at `mcp.blotato.com` and isn't part of this repo. This repo holds its public-facing pieces:

| File | Purpose |
| --- | --- |
| [`server.json`](server.json) | Entry for the [MCP Registry](https://registry.modelcontextprotocol.io/?q=blotato) (`com.blotato/mcp`) |
| [`mcp.json`](mcp.json) | Portable MCP server config |
| [`.mcp.json`](.mcp.json) | Native MCP config for clients such as Claude Code |
| [`images/`](images/) | Blotato brand assets |

---

## Support and feedback

If you hit a bug or limitation, or have a suggestion:

* Check the [MCP FAQs](https://help.blotato.com/start-with-an-ai-agent/mcp/faqs) and the [Blotato help center](https://help.blotato.com).
* Email [support@blotato.com](mailto:support@blotato.com) for account, billing, or connection issues.

---

## Disclaimer

MCP clients can perform actions on your connected social accounts with your existing permissions. Review posts, replies, and automations before confirming them, and check what was published.
