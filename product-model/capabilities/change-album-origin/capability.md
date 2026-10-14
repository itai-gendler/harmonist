---
availability:
- place: web
references:
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#set_origin
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#edit_origin
- kind: code
  role: implementation
  target: src/harmonist/provenance.py#origin
- kind: doc
  role: intent
  target: docs/how-it-works.md
  title: Where the files came from
---

# Change an album's origin

The owner states where an album's files came from when the marks in its tags tell the wrong story, or returns it to automatic detection. The choice feeds the possible mismatch and contribution checks and the Qobuz barcode suggestion without changing any tag.
