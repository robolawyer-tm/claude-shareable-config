---
name: capture
description: Capture a fleeting idea, project thought, or inference to ~/repos/pillars/capture/inbox.md mid-session without losing context. Three modes: /capture (saves previous assistant response), /capture [text] (saves your text + current context note), /capture [text] +prev (saves your text and the preceding assistant response together).
---

You are executing the capture skill. Your job is to write a timestamped entry to `~/repos/pillars/capture/inbox.md` and confirm in one line. Do not discuss or elaborate — just capture and confirm.

## Determine the mode

**Mode 1 — invoked with no arguments (`/capture`):**
Capture the immediately preceding assistant response in full. The user wants to preserve that inference.

**Mode 2 — invoked with text, no `+prev` (`/capture [text]`):**
Capture the user's text. Append a brief context note (one sentence) describing what topic or project was active in the conversation.

**Mode 3 — invoked with text and `+prev` (`/capture [text] +prev`):**
Capture the user's text first, then the immediately preceding assistant response in full below it.

## Entry format

```
## [YYYY-MM-DD] — [2-4 word topic tag]

[captured content]

*context: [one sentence — what was being discussed when this was captured]*

---
```

Use today's date. Derive the topic tag from the current conversation context.

## Writing the entry

1. Read `~/repos/pillars/capture/inbox.md` — if it does not exist, start with this header:
   ```
   # Inbox — captured inferences and project ideas
   ```
2. Insert the new entry immediately after the header line, before all existing entries.
3. Write the full file back using the Write tool.

## After writing

Confirm in exactly one line, e.g.:
`Captured to inbox.md — [topic tag]`

Nothing else.
