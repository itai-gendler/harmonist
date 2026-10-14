---
entities:
- entity: album
  shows:
  - Title
  - Artist
  - Folders
  - Tracks on disk
  - Release
  - Tag values
  - Track and disc totals
  - Store URL
  - Linked purchase
  - Purchase candidates
  - Origin
  - Origin choice
  - Embedded artwork
  - Folder cover
  - Stand-in artwork
  - Accepted as complete
  - Accepted release
  - Possible mismatch
  - MB contribution
  collects:
  - Release
  - Origin choice
  - Accepted as complete
  - Accepted release
- entity: release
  shows:
  - Title
  - Artist credit
  - Tracklist
  - Barcode
  - Store links
  - Release group
  - Media
  - Cover art
  - Last read
  - Cover Art Archive checked
- entity: suggested-match
  shows:
  - Release
  - How it was found
  - Confidence
  - Track comparison
  - No purchase found
  - Owned purchase
- entity: tag-update
  shows:
  - Significance
  - Changes
  - Follows settings
  - Tracklist changed
- entity: artwork-update
  shows:
  - Kind
  - Rows
  - Available images
  - Chosen images
  collects:
  - Chosen images
- entity: tagging
  shows:
  - Release
  - Field changes
  - Written at
- entity: artwork-change
  shows:
  - Kind
  - Targets
  - Written at
- entity: activity-entry
  shows:
  - What happened
  - When
- entity: bandcamp-purchase
  shows:
  - Artist
  - Title
entryPoints:
- web: /album/{album-id}
references:
- kind: code
  role: implementation
  target: templates/album.html
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#album_page
- kind: code
  role: implementation
  target: templates/partials/_artwork.html
---

# Album

Everything Harmonist knows about one album: its identity and Origin, its
tags beside MusicBrainz's, the tracklist with each file paired to its track,
the artwork it carries now beside what applying would write and every image
available for it, the release group check with any possible mismatch or
contribution to MusicBrainz, and the album's History of taggings and artwork
changes with their Undo controls. It also carries the same matching tools as
the album's Inbox card.
