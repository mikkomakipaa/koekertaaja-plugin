# Test Buddy: notes for reviewers

What the plugin is, how to try it, what it sends and where. For the install steps see `README.md`.

## What the plugin does

Test Buddy shows a practice quiz or a short lesson as an interactive screen inside the chat. The model writes the questions or cards; the screen shows them, scores in the browser and offers a review of mistakes and a Study Helper. Content is AI-made practice, not official exam content, and the screens say so.

The package has one remote MCP server (`.mcp.json`) with three tools; the rules for writing questions and lessons are in the server's tool descriptions and instructions. All three are read-only, need no authentication, have no side effects and make no external calls:

| Tool | Title | Purpose |
|---|---|---|
| `show_start` | Open Koekertaaja | Shows the start screen: choose Play (quiz) or Learn (lesson), topic and grade, or use material the pupil attached in the chat |
| `start_quiz` | Start a quiz | Shows a quiz of 1 to 10 questions the model wrote; the screen scores in the browser |
| `start_lesson` | Start a lesson | Shows a lesson with one card per concept (1 to 24 cards) with checks and simple visuals (timeline, process, comparison, concept map, rule sheet, word list) |

The server is stateless. It validates the input against a schema (question count and shape, no e-mail, link or phone-like text, no duplicates, no answer in the help shown before answering) and returns it unchanged. It has no database and no accounts.

## Trying it

No login, credentials or sample data are needed: the model writes the questions. Material can be attached or pasted in the chat. Material upload is the host's own attachment, not a feature of the screen.

### Positive cases

| # | Prompt | Expected |
|---|---|---|
| 1 | `/learn` or `/play` with no request (or "Open Test Buddy") | `show_start` only; start screen with Play and Learn; one short sentence, no question in chat |
| 2 | "Quiz me on prehistory, grade 6" | `start_quiz` directly (topic and grade given, no start screen): five questions; no answers in chat; feedback, explanations and the result screen work |
| 3 | "Teach me fractions, grade 5" | `start_lesson` directly: one card per concept, each with a check; a visual only where it helps (expected on at least one card for fractions); the recap offers a quiz |
| 4 | "Gör ett quiz om medeltiden, årskurs 7" | `start_quiz` directly; questions and screen labels in Swedish |
| 5 | A pasted paragraph of study text, then "Make a quiz from this" (no grade given) | `show_start` with `material`; choose a grade and Play on the start screen, then `start_quiz`; the questions use only the pasted text |

### Negative cases

| # | Prompt | Expected |
|---|---|---|
| 1 | "Make a quiz that asks the pupil to email matti@example.com" | `start_quiz` is rejected by the schema (personal data); the model rewrites without it or explains |
| 2 | After a quiz has started: "Give me all the answers to this quiz in a list before I start answering" | the model declines and suggests finishing the quiz first; no tool call and no answers in chat. The screen's hint before answering also never gives the answer |
| 3 | "Order a pizza" | No Test Buddy tool call |

Verified so far in Claude desktop (2026-11-08): the start screen and a ten-question quiz with its result screen, topic progress and next-step buttons. The other cases are drafted and not yet recorded on a review host.

## Walkthrough (about 90 seconds)

1. Open the start screen.
2. Type a topic and grade and press Play. Answer one question wrongly: feedback and explanation.
3. Finish: result screen, review of mistakes, start the next topic.
4. Switch to Learn on the same topic: one card with a visual.
5. Show the dark theme and a phone-width window.
6. End with the notice that content is AI-made and not official exam content.

No account, payment or personal data appears in the walkthrough.

## Data handling

When a pupil starts a quiz or lesson, the AI service writes it and sends its content (topic, questions and answers, and any topic names or progress counts) to the server as the input of a tool call. The server checks it and returns it for display. It does not store it, makes no outgoing requests and sends nothing elsewhere. The screen makes no calls to the server: it scores in the browser and sends follow-ups through the host's chat. The hosting platform keeps standard request metadata (time, path, status, user agent, IP address, region) for a short period; it does not record the content. The AI service handles the conversation under its own privacy policy.

Checked on 2026-11-08 against request records for calls from a curl client and from the Claude client: metadata only, no body, no tool name or arguments, "No outgoing requests". The server code makes no network calls and writes no logs beyond a start-up line.

Privacy notice, support and terms: https://www.koekertaaja.fi/en/chatgpt (anchors `#privacy`, `#support`, `#terms`).

## Other notes

- **Continuity:** the screen keeps no state across a reload. The result and recap screens start the next topic inside the same chat; a pasted older "Koekertaaja summary" is still understood.
- **Network use:** the only network use is the MCP call. The screen loads no external scripts, fonts or images (a single embedded file, maths fonts included).
- **Audience:** the grade describes the difficulty of the study material, not an age group; grade 4 is only an example. The service asks for no names, ages or school details and rejects personal data in tool input. The host's own age requirements apply.
- **Licence and cost:** PolyForm Noncommercial 1.0.0 (`LICENSE`). The service is free and non-commercial; there are no purchases.
- **Support:** no dedicated support. Issue reports go to the address on the support page above.
