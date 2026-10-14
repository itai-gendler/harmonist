---
availability:
- place: web
references:
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#assignment_editor
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#move_assignment
- kind: code
  role: implementation
  target: src/harmonist/track_assignment.py
- kind: doc
  role: intent
  target: docs/design/matching.md
  title: Which file is which track
---

# Edit track assignments

The owner reviews which file is paired with which of the release's tracks and corrects the pairing before anything is written. Harmonist pairs by release-track ID, then by a disc and track number unique on both sides, then by file order, and leaves anything ambiguous as a gap; the draft lives only on the page until the owner accepts it.
