---
name: meeting-to-sales-article
description: >
  Turns an internal product presentation transcript, slides, and meeting chat
  into a sales reference article. Extracts knowledge into nine source-linked
  categories, deduplicates questions and answers, assigns confidence statuses,
  collects gaps for subject-matter experts, drafts a twelve-section article,
  and prepares expert-review and rollout packages. Use when the user asks for a
  sales article, reference guide, or FAQ based on a product meeting, demo,
  presentation, or recording. Do not use for general meeting decisions and
  action items; use meeting-processing instead.
---

# Meeting → Sales Article

## Purpose

An internal product presentation and its question-and-answer discussion contain
valuable sales knowledge that quickly disappears into the recording. This skill
turns those sources into a traceable draft reference article that a salesperson
can use in a customer conversation.

The skill is designed for a Markdown vault with `AGENTS.md`, projects, contours,
`context.md`, `log.md`, and meeting history. It still works outside that vault,
but saves files in a user-selected folder and explicitly records missing
context.

Three principles:

1. Transcripts and slides are raw material, not final truth. Every fact receives
   a confidence status and a source anchor.
2. The agent does not replace a subject-matter expert. The result remains a
   draft until a person confirms expert review.
3. Meeting participants speak as insiders. The agent restores necessary terms
   and baseline knowledge from vault context so a new salesperson can
   understand the article.

## Inputs

| Input | Requirement | Notes |
|---|---|---|
| Meeting transcript (`.txt`, `.md`, `.srt`) | primary | Source for speech and questions |
| Presentation (`.pptx`, `.pdf`, slide images) | recommended | Source for exact figures, names, and diagrams |
| Meeting chat or pre-collected questions | optional | May contain unanswered questions |
| Product name and expert role | optional | Record an assumption if they are not explicit |
| `context.md`, glossary, pricing, prior material | recommended | Source for terms and implicit context |

If there is no transcript but the presentation is substantive, do not block the
work. Build the article from the slides, record that spoken questions were
unavailable, and never invent answers that the slides do not contain.

## Outputs

Create three files:

1. `<slug>-extraction.md` — sources and limitations, nine knowledge categories,
   and a status-labeled question-and-answer table.
2. `<slug>-article-draft.md` — a twelve-section article labeled
   “DRAFT — not reviewed by a subject-matter expert.”
3. `<slug>-support-package.md` — gap list, expert messages, review items,
   announcement, walkthrough plan, and maintenance plan.

Use a `<slug>` such as:
`sales-article-<product>-<YYYY-MM-DD>`.

### Where to Save

- In a compatible vault, follow `AGENTS.md` and save the files in the product's
  project or contour folder. If the location is ambiguous, ask one short
  question and do not read content files from multiple candidate contours.
- Do not delete incoming source files. Follow the vault's inbox-processing and
  index-update rules when they exist.
- In a standalone installation, ask for the destination folder; default to the
  session working directory.

## Process

### 1. Inspect the Sources

1. List the received materials.
2. Check transcript quality: speaker labels, omissions, inaudible passages, and
   abrupt cuts.
3. Read the presentation and capture exact product names, figures, prices,
   timelines, and diagrams for later comparison.
4. Identify who presented the product and who asked questions. Mark uncertain
   role attribution as an assumption.
5. Ask one combined clarification only for critical missing material, such as
   the chat, slides, or the person who will verify facts. Continue without an
   answer and record the limitation.

Begin the extraction file with a “Sources and limitations” section.

### 2. Build the Contour Lens

The contour lens is a working list of knowledge that meeting participants take
for granted but a new salesperson does not have.

In a compatible vault:

1. Identify the product project or contour according to `AGENTS.md`.
2. Read the relevant parts of:
   - `context.md` for terminology, constraints, metrics, and current terms;
   - the latest 5–7 `log.md` entries for recent decisions and changes;
   - product material such as pricing, existing descriptions, and prior
     articles.
3. If the meeting is recurring or refers to earlier discussions, use
   [context-compression](../context-compression/SKILL.md) first. Read only the
   latest 2–3 relevant meetings in full, not the whole archive.
4. Build an internal list of terms and abbreviations, baseline product facts,
   current terms, and decisions that the meeting may reference.

Outside the vault, ask once for a glossary, pricing, product description, and
prior material. If none is available, work without the lens but send unknown
terms and unclear references to the gap list. Never invent expansions.

Record which lens sources were available and which were missing in “Sources and
limitations.”

### 3. Extract Knowledge

Use three passes.

#### Pass 1 — Overall Picture

Read the entire primary source without taking notes. Identify the presentation
structure, the question-and-answer section, and places where the speaker sounds
confident or tentative.

#### Pass 2 — Nine Categories

Classify meaningful fragments into:

1. What it is.
2. Who it is for.
3. What problem it solves.
4. Value and benefits.
5. How it works.
6. Price and commercial terms.
7. Competitors and differentiation.
8. Limitations and promises that must not be made.
9. Sales process and lead handoff.

Give every fact one of two source anchors:

- `[meeting: timestamp or short quote]`;
- `[contour: file and section]`.

Do not include a fact without an anchor. A paraphrase does not replace source
traceability.

#### Pass 3 — Questions and Answers

1. Extract questions and answers from speech, chat, and the pre-collected list.
2. Merge semantic duplicates, retain the most complete wording, and record the
   frequency.
3. Assign each answer one status:
   - `complete` — confident and specific;
   - `partial` — qualified or awaiting confirmation;
   - `unanswered` — left open;
   - `disputed` — conflicts with another source.
4. Compare every spoken figure, price, and timeline with the slides. When they
   differ, preserve both versions, mark the item `disputed`, and leave the
   decision to an expert.
5. Compare terms and implicit references with the contour lens. Send anything
   unresolved to the gap list instead of reading the entire archive.
6. Compare new claims with `context.md`. Do not resolve conflicts yourself:
   show both versions and formulate an expert question.

Example:

| Question | Answer | Answered by | Status | Frequency | Anchor |
|---|---|---|---|---|---|
| Does it integrate with a CRM? | “Probably through the API, but we need to confirm.” | product expert | `partial` | 3 | [meeting: 00:42:15] |

### 4. Build the Gap List

1. Select every row labeled `partial`, `unanswered`, or `disputed`.
2. Add chat questions that the meeting did not answer.
3. Assign the likely owner by role: product owner, engineering, legal, or
   finance. If unclear, write “confirm with the owner.”
4. Group questions by recipient.
5. Draft a message for each recipient: short introduction, numbered questions
   with context, and a suggested response window of 3–5 business days.
6. Do not send messages without explicit approval of both the text and
   recipients.

Save the gap list and messages in `<slug>-support-package.md`.

### 5. Draft the Article

The article must answer “what should I say to the customer?” rather than follow
the order of the slides.

Use twelve sections. Do not remove an empty section; write
“not available in the sources — clarification pending.”

1. Header: what it is, who it is for, date, future owner, and draft label.
2. Who to sell to and who not to sell to.
3. Customer pains and scenarios.
4. Value: 3–5 points with figures or examples.
5. How it works.
6. Pricing and terms; what can be promised without approval.
7. Objections and ready-to-say conversational answers.
8. Competitors: where the product is stronger and honestly weaker.
9. Frequently asked questions, ordered by frequency.
10. Limitations and red lines.
11. Process: the next step with an interested customer.
12. Expert contact for questions outside the article.

Transfer rules:

- include `complete` facts in the main article;
- include a `partial` fact only with a visible “pending confirmation” marker;
- keep `unanswered` and `disputed` items in the gap list;
- exclude internal discussion, personal data, secrets, customer names without
  permission, and raw participant quotes;
- mark prices, timelines, legal promises, and competitor comparisons with
  sequential `[VERIFY-N]` markers.

Write for scanning: short sections, lists, and tables. Phrase headings as
salesperson questions. Every section must pass this test:
“Could a salesperson say this to a customer right now?”

Expand terms on first use. If there are more than five, add a mini-glossary to
the FAQ section.

### 6. Verify the Result

Before expert review, verify:

1. Every article fact traces to an anchor in the extraction file.
2. Figures are internally consistent and do not silently conflict with slides
   or vault context.
3. A new salesperson can understand terms and references without attending the
   meeting.
4. Every complete answer appears in the article or is deliberately excluded
   with a reason.
5. No `unanswered` or `disputed` fact appears as established truth.
6. Confidential and personal data has been removed or escalated to the owner.

Add to `<slug>-support-package.md`:

- all `[VERIFY-N]` markers with concrete questions;
- an expert checklist covering facts, pricing, promises, competitors, and
  limitations;
- a ready-to-send expert message linking to the draft.

Only a person may remove the “DRAFT — not reviewed by a subject-matter expert”
label after explicit expert confirmation.

### 7. Save and Prepare Rollout

1. Cross-link the article, extraction, support package, and source files.
2. In the article header, record the owner, creation date, review date three
   months later, and events that should trigger an earlier review.
3. Add to the support package:
   - a team-channel announcement;
   - a ten-minute sales-meeting walkthrough;
   - usefulness-check questions for 2–4 weeks later;
   - a maintenance checklist.
4. If a scheduler is available, offer reminders for three weeks and three
   months. Do not create them without consent.
5. Follow applicable `AGENTS.md` rules: update the folder index, add a short
   result entry to `log.md`, and change `plan.md`, `context.md`, or `tasks.md`
   only when their state is genuinely affected.
6. If the meeting introduces durable knowledge, propose a `context.md` change
   as “before → after” with a source anchor. Do not apply it silently.

## Anti-Patterns

- Retelling slides instead of organizing the article around salesperson needs.
- A fact without a source anchor.
- Silently choosing one version when speech, slides, and context conflict.
- Quietly dropping unanswered questions.
- Removing the draft label without human confirmation.
- Answers that a salesperson cannot say naturally to a customer.
- Blocking the whole task because one optional source is missing.
- Terms and internal references that only meeting participants understand.
- Invented expansions of unknown terms.
- Reading the whole meeting archive to resolve one reference.

## Related Skills

- [meeting-processing](../meeting-processing/SKILL.md) — general meeting
  processing: decisions, actions, risks, and routing.
- [context-compression](../context-compression/SKILL.md) — compact history for
  recurring meetings and bounded archive reading.

If the user wants both general meeting processing and a sales article, run
`meeting-processing` first and then use this skill on the same sources.
