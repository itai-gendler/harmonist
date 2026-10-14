---
id: harmonist
summary: A self-hosted music librarian that tends a collection's metadata and artwork using MusicBrainz, with every change previewed, logged and reversible.
category: music-library
tags:
- music
- musicbrainz
- tagging
- artwork
- bandcamp
- self-hosted
authors:
- name: Alastair Rankine
  url: https://github.com/randomphrase
license: GPL-3.0-or-later
languages:
- en
limitations:
- 'MusicBrainz is the only source of metadata: there is no per-album override, and a correction belongs on MusicBrainz.'
- Harmonist never edits MusicBrainz itself; it opens the release's editor on MusicBrainz with the value ready to copy.
- Music files are never moved, renamed or converted, and genres and comments are never written; Re-download is the one change that removes files, and it zips them first.
- Each folder of audio files belongs to one album; a folder holding several albums stays Inconsistent until it is split outside Harmonist.
- One person runs Harmonist on their own network; signing in is left to a reverse proxy or the optional built-in password.
references:
- kind: doc
  role: intent
  target: README.md
  title: README
- kind: doc
  role: intent
  target: docs/how-it-works.md
  title: How Harmonist works
- kind: doc
  role: intent
  target: docs/design/principles.md
  title: Design principles
---

# Harmonist

Harmonist is a self-hosted music librarian. It scans a music folder, works out
which MusicBrainz release each album is, and keeps the albums' Picard-compatible
tags and artwork current with MusicBrainz and the Cover Art Archive. Albums that
need a decision wait in the **Inbox**, settled albums are browsed and filtered in
the **Library**, and the **Activity** feed lists everything Harmonist has done.
Matches, tag updates and artwork changes are proposed and previewed before
anything is written, every tagging is recorded field by field, and tag and
artwork changes can be undone. It can also sync, download and tag the owner's
Bandcamp purchases.

## Intent

Ongoing care of a music collection, with MusicBrainz as the source of metadata
and the owner in control of changes: tag all your music with Picard-compatible
metadata, keep your own folders and formats, keep tags current, fill missing
covers and upgrade artwork, find the gaps and inconsistencies in the
collection, undo tag and artwork changes, and give back to MusicBrainz.
Matching uses MusicBrainz data and explicit rules, with uncertain matches left
for the owner to review.
