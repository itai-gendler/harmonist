---
availability:
- place: web
references:
- kind: code
  role: implementation
  target: src/harmonist/gardener.py#sweep
- kind: code
  role: implementation
  target: src/harmonist/gardener.py#_record_digest
- kind: doc
  role: intent
  target: docs/design/staying-current.md
  title: The background update check
---

# Find tag updates in the background

While Library updates is set to Find updates for review, Harmonist asks MusicBrainz about a few albums every ten minutes, longest-unchecked first, so the whole library comes round about weekly. It compares the files with what re-tagging would write now and only reports: it never writes to the music files.
