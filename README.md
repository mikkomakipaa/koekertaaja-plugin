# Test Buddy

Practise for school exams and learn a topic step by step, as an interactive screen inside the chat. Made for Finnish school subjects. The grade you choose (for example grade 4) describes the difficulty of the study material. Part of Koekertaaja (koekertaaja.fi).

- **Play:** name a topic and a grade (for example grade 4), or attach your material in the chat, and say "quiz me". Up to ten questions per round with feedback, a score, a review of mistakes and optional extra practice that never changes the score.
- **Learn:** say "teach me". Short cards, one per concept, with a quick check each, simple timelines, processes and comparisons, and a recap that can start a quiz on the same topic.
- **Start screen:** open Test Buddy without a request and choose Play or Learn, topic and grade. Attach your own material in the chat first if you have it.
- **Study Helper:** simpler explanation, the reason why, a hint (before answering), another way to explain it (after a wrong answer) and an extra example on Learn cards. Before you answer, nothing gives the answer away.

## Install

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
