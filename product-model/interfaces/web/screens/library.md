---
entities:
- entity: album
  shows:
  - Title
  - Artist
  - Origin
  - Added
  - Tracks on disk
  - Track and disc totals
  - Accepted as complete
  - Embedded artwork
  - Folder cover
  - Possible mismatch
  - MB contribution
- entity: tag-update
  shows:
  - Significance
- entity: artwork-update
  shows:
  - Kind
entryPoints:
- web: /?tab=library
references:
- kind: code
  role: implementation
  target: templates/partials/library_page.html
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#library
- kind: doc
  role: intent
  target: docs/how-it-works.md
  title: The Library
---

# Library

Every album with nothing left to decide, as a paged grid of tiles that can
be searched by artist and title and narrowed by filters that combine: Origin,
New, Incomplete, Partially tagged, Artwork, Format, Tag updates by
significance, Artwork updates by kind, Possible mismatch and MB contributions,
each with a count of albums.
