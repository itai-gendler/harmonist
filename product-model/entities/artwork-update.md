---
references:
- kind: code
  role: implementation
  target: src/harmonist/artwork_updates.py
- kind: code
  role: implementation
  target: src/harmonist/artwork.py
- kind: doc
  role: intent
  target: docs/design/artwork.md
  title: Artwork
---

# Artwork update

The artwork writes Harmonist proposes for an album, built from what its tracks and folder carry, the Cover Art Archive's images and any choices the owner made row by row.

## Information kept

- **Kind** — Addition when it only fills empty places, Replacement when it overwrites at least one existing image
- **Rows** — each distinct image its tracks carry, and the folder cover, with what each holds now and after applying
- **Available images** — the images the Cover Art Archive lists for the release, its release group and the group's other releases
- **Chosen images** — the image the owner chose for a row, or the row's current image kept instead of the suggestion

## States

### Available

Listed under the Library's Artwork updates filter and shown in the album's Artwork section.

### Applied

Written to the album's files.
