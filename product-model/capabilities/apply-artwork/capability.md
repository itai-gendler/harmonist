---
availability:
- place: web
references:
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#album_artwork
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#album_artwork_update
- kind: code
  role: implementation
  target: src/harmonist/tagger.py#apply_artwork
- kind: code
  role: implementation
  target: src/harmonist/artwork_store.py#keep_all
- kind: doc
  role: intent
  target: docs/design/artwork.md
  title: Artwork
---

# Apply artwork

In the album's Artwork section the owner sees, row by row, the image each place carries now beside what applying would put there, and every image the Cover Art Archive has for the release, its release group and the group's other releases. They can choose any image for a row or keep its current one, and Apply artwork writes exactly what the section shows, without touching tags.
