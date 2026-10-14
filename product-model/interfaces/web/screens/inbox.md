---
entities:
- entity: album
  shows:
  - Title
  - Artist
  - Folders
  - Tracks on disk
  - Release
  - Store URL
  - Track and disc totals
  collects:
  - Release
- entity: suggested-match
  shows:
  - Release
  - How it was found
  - Confidence
  - Track comparison
  - No purchase found
  - Owned purchase
- entity: release
  shows:
  - Title
  - Artist credit
  - Tracklist
  - Barcode
  - Store links
  - Media
- entity: bandcamp-purchase
  shows:
  - Artist
  - Title
  - Purchase URL
- entity: tag-update
  shows:
  - Changes
- entity: artwork-update
  shows:
  - Rows
entryPoints:
- web: /?tab=inbox
references:
- kind: code
  role: implementation
  target: templates/tasks.html
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#tasks
- kind: doc
  role: intent
  target: docs/how-it-works.md
  title: The Inbox
---

# Inbox

Albums that need a decision from the owner, grouped by what they need —
Possibly mis-tagged, New, Needs MBID, Needs Linking, Inconsistent and Tagging —
each group saying what will clear it, followed by potential downloads from the
last Bandcamp sync and albums being re-downloaded. Each album card carries the
tools that clear it: search, a pasted MusicBrainz ID, the suggested match with
its side-by-side tracklist, and the Bandcamp links.
