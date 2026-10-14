---
availability:
- place: web
references:
- kind: code
  role: implementation
  target: src/harmonist/scanner.py#scan
- kind: code
  role: implementation
  target: src/harmonist/web/scan_runner.py#ScanRunner
- kind: code
  role: implementation
  target: src/harmonist/web/dir_watcher.py#watch_music_dir
- kind: code
  role: implementation
  target: src/harmonist/web/reconcile_runner.py
- kind: doc
  role: intent
  target: docs/design/staying-current.md
  title: Noticing changes on disk
- kind: doc
  role: intent
  target: docs/design/model.md
  title: State is derived
---

# Scan the library

Harmonist reads the music folder on its own — when files change on a local disk, every hour as a backstop, and after its own changes — and works out each album and its state from the files and their records. It never moves or renames anything.
