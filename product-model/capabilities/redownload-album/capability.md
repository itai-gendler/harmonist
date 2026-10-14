---
availability:
- place: web
references:
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#redownload
- kind: code
  role: implementation
  target: src/harmonist/archive.py#archive_and_remove
- kind: code
  role: implementation
  target: src/harmonist/redownloads.py
- kind: doc
  role: intent
  target: docs/design/bandcamp.md
  title: Re-download
---

# Re-download an album

The owner fetches an album from Bandcamp again, for a better format or for tracks the artist added later. The current files are zipped into the top of the music folder and checked before they are removed, and the replacement keeps the album's match.
