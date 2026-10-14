---
availability:
- place: web
references:
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#manual_search
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#barcode_lookup
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#manual_candidates
- kind: code
  role: implementation
  target: src/harmonist/mb_search.py
- kind: doc
  role: intent
  target: docs/design/matching.md
  title: Barcode search
---

# Search MusicBrainz for a release

From an unmatched album's Inbox card or page, the owner looks for its release on MusicBrainz by artist and title, by the barcode its files share, or by its store URL. A lookup that finds exactly one release suggests it for review; otherwise the releases are listed to choose from.
