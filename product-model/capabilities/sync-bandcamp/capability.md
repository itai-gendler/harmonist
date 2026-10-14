---
availability:
- place: web
references:
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#start_sync
- kind: code
  role: implementation
  target: src/harmonist/bandcamp_hook.py#HarmonistSyncer
- kind: code
  role: implementation
  target: src/harmonist/web/sync_runner.py#SyncRunner
- kind: code
  role: implementation
  target: templates/header.html
- kind: doc
  role: intent
  target: docs/design/bandcamp.md
  title: Bandcamp
- kind: doc
  role: intent
  target: docs/how-it-works.md
  title: Bandcamp sync
---

# Sync Bandcamp

The owner syncs their Bandcamp collection: Harmonist links purchases to albums already on disk, downloads new purchases in the chosen format and tags them, and sets aside anything it cannot tie to an album without guessing. While any album waits under Needs Linking a sync runs link-only and downloads nothing.
