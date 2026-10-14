---
references:
- kind: code
  role: implementation
  target: src/harmonist/activity.py
- kind: code
  role: implementation
  target: src/harmonist/activity_store.py
- kind: doc
  role: intent
  target: docs/design/history.md
  title: Two records, one store
---

# Activity entry

One plain-language record of an outcome — a match, a tagging, a sync, a warning — shown in the Activity feed and in the History of the album it concerns, with the technical record of every change behind it.

## Information kept

- **What happened** — the outcome in plain language
- **Album** — the album it concerns, named as it was at the time
- **When** — when it happened
- **Level** — information, warning or error
- **Technical detail** — every file, record and download change the action made
