---
availability:
- place: web
references:
- kind: code
  role: implementation
  target: src/harmonist/reconcile.py#reconcile_album
- kind: code
  role: implementation
  target: src/harmonist/web/reconcile_runner.py#reconcile_pending_orphans
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#reconcile_album_route
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#tasks
- kind: doc
  role: intent
  target: docs/design/matching.md
  title: Adopting an album
---

# Reconcile albums from their tags

Harmonist adopts albums from the evidence already in their files: a MusicBrainz release ID written by Picard or an earlier Harmonist, a store URL in the comment, or a barcode. It starts by itself when the Inbox is opened with a New album that carries a release ID or barcode, and the owner can run it for one album with Reconcile from tags.
