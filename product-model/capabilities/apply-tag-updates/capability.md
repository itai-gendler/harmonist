---
availability:
- place: web
references:
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#retag
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#_tag_with_release
- kind: code
  role: implementation
  target: src/harmonist/tagger.py#tag_and_artwork
- kind: code
  role: implementation
  target: templates/partials/_album_update.html
- kind: doc
  role: intent
  target: docs/how-it-works.md
  title: Keeping tags up to date
---

# Apply tag updates

On the album's page the owner reads exactly what an update would change and applies it: Harmonist re-reads the release and writes its tags, with any artwork the Artwork section includes, into every folder of the album. Re-tag controls for a partly tagged album and for a merged release write the same way.
