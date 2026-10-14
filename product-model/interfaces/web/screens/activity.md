---
entities:
- entity: activity-entry
  shows:
  - What happened
  - Album
  - When
  - Level
  - Technical detail
entryPoints:
- web: /?tab=activity
references:
- kind: code
  role: implementation
  target: templates/partials/activity.html
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#activity_feed
---

# Activity

Everything Harmonist has done across the whole library, newest first, one
plain-language entry per outcome, each linked to its album, with the
technical detail beneath each entry on request.
