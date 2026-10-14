---
availability:
- place: web
references:
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#library_rematch
- kind: code
  role: implementation
  target: templates/partials/_release_gone.html
- kind: doc
  role: intent
  target: docs/troubleshooting.md
  title: An album is matched to the wrong release
---

# Clear a wrong MusicBrainz match

The owner says an album's release is wrong; the album returns to Needs MBID with no suggestion, keeping its tags, store link and purchase until the right release is chosen.
