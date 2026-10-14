---
availability:
- place: web
references:
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#set_tracks_unavailable
- kind: code
  role: implementation
  target: templates/partials/_completeness.html
---

# Accept an incomplete album as complete

The owner ticks Don't warn me about this beside an Incomplete album's shortfall: the Library drops its badge and leaves it out of the Incomplete filter, while the album page keeps stating the shortfall. No state, tag or file changes.
