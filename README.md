# Test Buddy

Practise for school exams and learn a topic step by step, as an interactive screen inside the chat. Made for Finnish school subjects. The grade you choose (for example grade 4) describes the difficulty of the study material. Part of Koekertaaja (koekertaaja.fi).

- **Play:** name a topic and a grade (for example grade 4), or attach your material in the chat, and say "quiz me". Up to ten questions per round with feedback, a score, a review of mistakes and optional extra practice that never changes the score.
- **Learn:** say "teach me". Short cards, one per concept, with a quick check each, simple timelines, processes and comparisons, and a recap that can start a quiz on the same topic.
- **Start screen:** open Test Buddy without a request and choose Play or Learn, topic and grade. Attach your own material in the chat first if you have it.
- **Study Helper:** simpler explanation, the reason why, a hint (before answering), another way to explain it (after a wrong answer) and an extra example on Learn cards. Before you answer, nothing gives the answer away.

## Add the MCP server only (no plugin)

Test Buddy works without the plugin: the MCP server carries the rules for the questions and lessons itself. The plugin's two skills only add consistency (for example sending "test me" to Play and "explain" to Learn), so install it too if you want that. Everything below uses the same server and sends the same data as described under "What the plugin sends and where".

| | |
|---|---|
| Server URL | `https://mcp.koekertaaja.fi/mcp` |
| Transport | Streamable HTTP (remote server) |
| Sign-in | None. There are no accounts and no API key. |

Connector menus change between releases, and which plan can add a custom connector is set by Claude and ChatGPT, not by this project. If a menu below does not match what you see, search your app's help for "custom connector" or "MCP".

### Claude (claude.ai and Claude desktop)

1. Open **Settings** and choose **Connectors**.
2. Choose **Add custom connector**.
3. Name: `Koekertaaja`. Remote MCP server URL: `https://mcp.koekertaaja.fi/mcp`. Leave any advanced or sign-in fields empty.
4. Choose **Add**. On a Team or Enterprise plan an owner may have to add the connector for the organisation first.
5. Open a new conversation, use the **+** menu, then **Connectors**, and switch Koekertaaja on for the conversation.
6. Say "Open Koekertaaja", or "quiz me on fractions, grade 5". The start screen or the quiz appears as an interactive screen in the chat.

Claude Code (terminal) has no screens, so use the plugin there instead; to add the server alone run:

```
claude mcp add --transport http koekertaaja https://mcp.koekertaaja.fi/mcp
```

### ChatGPT

1. Open **Settings**, then **Apps** (called **Connectors** in some versions) and **Advanced settings**, and turn on **Developer mode**. Custom MCP apps need it, and it is available on selected plans only.
2. In the same place choose **Create** (or **Add custom connector**).
3. Name: `Koekertaaja`. MCP server URL: `https://mcp.koekertaaja.fi/mcp`. Authentication: **No authentication**.
4. Tick the box that says you trust the server, then choose **Create**.
5. In a new chat, open the **+** menu, then **More** (or **Developer mode**), and select Koekertaaja for the chat.
6. Say "Open Koekertaaja", or attach your material and say "quiz me". The start screen or the quiz appears as an interactive screen in the chat.

### If it does not work

- **Nothing appears, only text:** the app or plan you use may not show interactive screens from custom connectors. Try the desktop or web app.
- **Old behaviour after an update:** remove the connector and add it again, then start a new conversation. Apps keep the tool list from when the connector was added.
- **A pupil using it:** do not share names or other personal details in the chat. Questions and lessons are made by AI and are not official exam content; check them against the textbook.

## Install the plugin

**Claude Code**:

```
/plugin install test-buddy --marketplace mikkomakipaa/koekertaaja-plugin
```

In Claude desktop, add the plugin from the directory or upload the plugin ZIP.

**ChatGPT desktop app and Codex:** 

Add the marketplace, then install the plugin from the app:

```
codex plugin marketplace add mikkomakipaa/koekertaaja-plugin
```

Then open the Plugins Directory in the ChatGPT desktop app (or Codex), choose the "koekertaaja-plugin" marketplace and install Test Buddy. 

In ChatGPT, upload the plugin ZIP to plugins.

## What the plugin sends and where

This plugin contains two skills (Play and Learn) and connects to one remote MCP server (`.mcp.json`), which shows the quiz or lesson screen. 

To show a quiz or lesson, the AI service writes it and sends its content (topic, questions and answers, and any topic names or progress counts) to that server as the input of a tool call. The server checks it and returns it for display in your chat. It does not store it, has no database or account system, makes no outgoing requests and sends nothing elsewhere. 

The hosting platform keeps standard request metadata (time, path, status, user agent, IP address, region) for a short period; it does not record the content. 

The AI service you use handles your conversation under its own privacy policy. Scores are calculated in your browser. Do not share names or other personal details.

Privacy notice: https://www.koekertaaja.fi/en/chatgpt#privacy
Support: https://www.koekertaaja.fi/en/chatgpt#support
Terms: https://www.koekertaaja.fi/en/chatgpt#terms

Questions and lessons are made by AI and are not official exam content: check them against your textbook. 

Free, non-commercial service by Mikko Mäkipää. 

Licence: PolyForm Noncommercial 1.0.0.
