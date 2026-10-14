---
appliesTo:
- type: capability
  id: redownload-album
- type: capability
  id: forget-album
- type: capability
  id: erase-sidecars
references:
- kind: code
  role: implementation
  target: src/harmonist/archive.py#archive_and_remove
- kind: doc
  role: intent
  target: docs/how-it-works.md
  title: What Harmonist changes, and what it never touches
---

# Harmonist never moves, renames or deletes music files except to re-download them

Folders and files stay where the owner put them, in their own formats. Re-download is the one exception: it removes an album's folders only after zipping them into the top of the music folder and checking every file in the zip, and nothing ever deletes the zip.
