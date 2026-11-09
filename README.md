# Test Buddy

Practise for school exams and learn a topic step by step, as an interactive screen inside the chat. Made for Finnish school subjects. The grade you choose (for example grade 4) describes the difficulty of the study material. Part of Koekertaaja (koekertaaja.fi).

- **Play:** name a topic and a grade (for example grade 4), or attach your material in the chat, and say "quiz me". Up to ten questions per round with feedback, a score, a review of mistakes and optional extra practice that never changes the score.
- **Learn:** say "teach me". Short cards, one per concept, simple timelines, processes and comparisons, and a recap that can start a quiz on the same topic.
- **Start screen:** open Test Buddy without a request and choose Play or Learn, topic and grade. Attach your own material in the chat first if you have it.
- **Study Helper (in Play):** simpler explanation, a hint (before answering), another way to explain it (after a wrong answer) and an extra example (after answering). Before you answer, nothing gives the answer away.

<img width="738" height="871" alt="Pasted 09-11-2026 at 14 56 23" src="https://github.com/user-attachments/assets/7a908750-033b-47bb-b8c9-17324e4cf61f" />
<img width="737" height="810" alt="Pasted 09-11-2026 at 15 03 45" src="https://github.com/user-attachments/assets/e3fb45b4-d064-4faf-aab6-5b2b5a2988e6" />
<img width="768" height="576" alt="Pasted 09-11-2026 at 14 55 56" src="https://github.com/user-attachments/assets/de203dbc-057f-4dfd-9145-c0a087d1131e" />

## Install

Test Buddy is a remote MCP server. You add it to Claude or ChatGPT as a custom connector; there is no plugin to install, no account and no API key. What it sends is described under "What is sent and where".

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

Claude Code runs in a terminal and cannot show the interactive screens, so use Claude or ChatGPT for those. To add the server to Claude Code anyway:

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

## How to use

Test Buddy opens as an interactive screen inside the chat. You do not type answers into the chat: you work on the screen, and the chat only says one short sentence.

### 1. Start

Say what you want, in Finnish, Swedish or English. The screen and the questions follow your language.

| You say | What happens |
|---|---|
| "Open Koekertaaja" or "Avaa Koekertaaja" | The start screen opens. Choose where to practise from (material from the chat, or a topic you type), the topic, the grade and Play or Learn. |
| "Quiz me on fractions, grade 5" or "Kokeile minua murtoluvuista, 5. luokka" | A quiz starts straight away. |
| "Teach me the Middle Ages, grade 6" or "Opeta minulle keskiaika, 6. luokka" | A lesson starts straight away. |
| "Test me" with no topic | The start screen opens so you can choose. |

If something is missing (topic, grade, or Play or Learn), the start screen opens and asks, instead of guessing. The grade is the difficulty of the study material (1 to 12), not the pupil's age.

### 2. Use your own material

Attach a photo, a PDF or pasted text of your textbook page or exam announcement in the chat, then say "quiz me" or "teach me". The questions and cards use only that material. If part of it cannot be read, you are told which part, and you can paste the text instead. The start screen lists the topics it found and you choose one or all of them. Do not attach names, contact details or other personal information.

### 3. Play (quiz)

- Five questions by default; on the start screen you can choose up to 30 (long practices run in rounds of ten).
- Many question types, not only multiple choice: true or false, choose all that apply, fill in the blank, short answer, match pairs, sort into groups, put in order, find the odd one out, and fill the gaps from a word bank. Some questions have a small diagram.
- Press **Check** to see right or wrong and why. Study Helper offers **a simpler explanation** and **a hint** before you answer, and **another way to explain it** and **an example** after.
- At the end: your score, the state of each topic, **Review mistakes** (replays the missed questions with hints but no score), optional extra practice that never changes the score, and a new round.

### 4. Learn (lessons)

- Short cards, one idea each: a heading, the main explanation, an example and a "remember" line, sometimes with a timeline, process, comparison, concept map, rule sheet or word list.
- Go through the cards with **Next**. A lesson has 1 to 24 cards, depending on how much material there is.
- The recap lists the cards and offers a quiz on the same topic, and the next topic when your material has one you have not covered yet.

### 5. After a round

The result screen shows how each topic went and a main button "Next: <topic>". "Practise: <topic>" suggests the weakest one. **Learn the topic**, **Play this topic** and **New round** keep the same topic, grade, language and material, so you are not asked again. **Start over** (top right of the screen) returns to the start.

### Good to know

- Everything is made by AI and is not official exam content. Check it against your textbook.
- The screen keeps no history: if you reload or open a new chat, start again and attach the material again.
- Scores are counted in your browser and are not stored anywhere.
- Made for Finnish school subjects. Other curricula are not supported.
- If the screen shows "Tehtävää ei voitu näyttää" ("The task could not be shown"), say "try again".

## What is sent and where

Test Buddy connects to one remote MCP server, which shows the quiz or lesson screen. 

To show a quiz or lesson, the AI service writes it and sends its content (topic, questions and answers, and any topic names or progress counts) to that server as the input of a tool call. The server checks it and returns it for display in your chat. It does not store it, has no database or account system, makes no outgoing requests and sends nothing elsewhere. 

The hosting platform keeps standard request metadata (time, path, status, user agent, IP address, region) for a short period; it does not record the content. 

The AI service you use handles your conversation under its own privacy policy. Scores are calculated in your browser. Do not share names or other personal details.

Privacy notice: https://www.koekertaaja.fi/en/chatgpt#privacy
Support: https://www.koekertaaja.fi/en/chatgpt#support
Terms: https://www.koekertaaja.fi/en/chatgpt#terms

Questions and lessons are made by AI and are not official exam content: check them against your textbook. 

Free, non-commercial service by Mikko Mäkipää. 

Licence: PolyForm Noncommercial 1.0.0.
