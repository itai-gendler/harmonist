---
availability:
- place: web
references:
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#activity_feed
- kind: code
  role: implementation
  target: src/harmonist/activity.py
- kind: doc
  role: intent
  target: docs/design/history.md
  title: Two records, one store
---

# Read the Activity feed

The owner reads everything Harmonist has done across the library, newest first, with the technical detail behind each entry on request. Warnings Harmonist logs reach the feed by themselves.
