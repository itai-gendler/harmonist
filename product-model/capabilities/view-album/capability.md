---
availability:
- place: web
references:
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#album_page
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#library_compare
- kind: code
  role: implementation
  target: src/harmonist/gardener.py#refresh_flag
- kind: code
  role: implementation
  target: templates/album.html
---

# Open an album

The owner opens an album's page from the Library, the Inbox or an Activity entry. Harmonist re-reads the album's folders from disk first, so the page describes the files as they are, compares them with the release, and checks whether re-tagging would change anything.
