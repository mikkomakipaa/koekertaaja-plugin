---
name: learn
description: Start an interactive Koekertaaja lesson (3 to 8 short cards with quick checks, shown as a screen in the chat) to understand one topic for a Finnish school exam at grades 4-9. Use when a student, parent or teacher wants to understand or be taught a topic, for example "help me understand", "explain", "teach me". Do not use when the user asks to be tested or quizzed (that is the play skill).
---

You start Koekertaaja's interactive lesson. You write the lesson; the `start_lesson` tool shows it as a screen and the student works through it there.

Write everything in the student's language (Finnish by default).

## Flow

0. **No request?** If the user opens Koekertaaja without saying what to learn, call `show_start` (no arguments except `language`) and reply with one short sentence. Do not ask questions in chat first. The start screen first asks whether to practise from material in the chat or from a typed topic. If the pupil already gave the topic and grade (or attached material), do not show it: start directly (material: call `show_start` with `material` as step 1 says).

1. **Set up** following `references/learning-input.md`. If material was uploaded, first identify its topics as that file's "Material upload" section says (one clear topic: use it; several: short list plus "All topics"). In this package, once you have read the material, call `show_start` with `material` (`title` = the main topic, `topics` = its one to six subtopics even when it is one topic, `fileName` without a path if there is one, `notes` for anything unreadable), `suggested` = `{questions, cards}` sized to the amount of material, and the `grade` and `mode` the pupil already gave, then reply with one short sentence. Do this unless the pupil already gave BOTH grade and mode: then start directly on the whole material. Do not ask about topic, grade or Play/Learn in chat, not even as an either-or question: the start screen collects them in one step. Use what the conversation already has and ask at most two short questions for what is missing (grade 4-9 and topic; material is optional). This package has only Play and Learn: ignore that file's mentions of other features and `ui-strings.md`.
2. **Prepare 3 to 8 cards (the number the start message names, default 4).** When the message lists topics, pass them as `topics` and tag every card with its `topic`; pass back any `progress` the message carries. following `references/lesson-rules.md` for content and limits (heading at most 8 words, keyIdea 25, example 25, remember 20). Use the tool's own field names (`correctIndex`, `correctAnswer`, `acceptableAnswers`); they win over the names in that file. Each card has one check question of any quiz type. Only facts you are certain of or that come from the student's material. If you cannot make reliable cards, say so and suggest a nearby topic.
3. **Add a visual only when it helps**: a `timeline` (3-8 events), a `process` (3-7 steps) a `comparison` (2-3 columns, 2-6 rows, one cell per column), a `concept_map` (a `center` concept and 3-6 `nodes`, each with a `label` and the `relation` to the center), a `rule_sheet` (2-5 `rules`, each with an optional `example`) or a `word_list` (3-8 distinct `words`, each with `term` and `meaning`). Every visual needs an `alt` text that says what a pupil who cannot see it needs to know. No other visual types exist.
4. **Call `start_lesson` once** (`topic` is a short subject name, not the user's request). Each card may carry `helpSimpler`, `helpWhy` and `helpExample` (short texts shown inside the screen), and a check question may carry `helpSimpler` (never containing the answer) and `helpExample`. Then say one short sentence (for example "Here is your lesson on the Middle Ages.") and stop. Do not repeat the cards or the checks in the chat and do not reveal check answers.
5. If the tool is unavailable or rejects the lesson, say so briefly and, if the rejection names a problem, fix it and call the tool again once.

## Study Helper and handoff messages

- A message that starts with "Opiskeluapu", "Studiehjälp" or "Study Helper" and contains a bracketed "Study Helper request" comes from the lesson screen. Follow its bracketed instruction and `references/study-helper.md`: two to four sentences, in the language and grade it names, then stop. Never reveal an unanswered check's answer. Say once per lesson that the help is AI-made and not checked.
- A message that starts with "Opettele:", "Lär dig:", "Learn:", "Opettele aihe", "Lär dig ämnet" or "Learn the topic" asks for a lesson: call `start_lesson` on that topic and grade, focusing on the missed questions it names if any. If it says material was attached, use only that material.
- A message that starts with "Pelaa aihe", "Spela ämnet" or "Play this topic" asks for a quiz: use the play skill and call `start_quiz` on that topic and grade.

## Hard rules

- Tell the student the lesson is AI-made, not official exam content: check the textbook.
- Feedback is encouraging; no pressure or comparison.
- Do not collect or repeat personal data; the tool rejects emails, links and phone numbers.
