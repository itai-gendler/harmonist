---
relations:
- entity: suggested-match
  verb: has
  cardinality: one-to-many
- entity: tag-update
  verb: has
  cardinality: one-to-many
- entity: artwork-update
  verb: has
  cardinality: one-to-many
- entity: tagging
  verb: has
  cardinality: one-to-many
- entity: artwork-change
  verb: has
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: src/harmonist/models.py#AlbumState
- kind: code
  role: implementation
  target: src/harmonist/models.py#Album
- kind: code
  role: implementation
  target: src/harmonist/sidecar.py
- kind: code
  role: implementation
  target: src/harmonist/provenance.py#origin
- kind: doc
  role: intent
  target: docs/design/model.md
  title: The model
---

# Album

One album in the music folder: the files that name one MusicBrainz release, wherever they are, or a folder of files on its own when they name none. Its state is worked out from its files and its Harmonist record every time Harmonist looks, and every album is in exactly one state.

## Information kept

- **Title** — the album title its files carry
- **Artist** — the album artist its files carry
- **Folders** — the folders holding its files; one album can span several folders holding different tracks of one release
- **Tracks on disk** — its audio files, each with its disc and track position and its audio format
- **Release** — the MusicBrainz release the album is matched to
- **Tag values** — the values of the tags Harmonist owns, field by field and track by track
- **Track and disc totals** — the release's track and disc counts written into its files, from which completeness is read
- **Store URL** — the store page its files came from, such as the Bandcamp album URL in the comment
- **Linked purchase** — the one Bandcamp purchase it is linked to
- **Purchase candidates** — the several Bandcamp purchases it could be when no rule can tell them apart
- **Origin** — where its files came from — Bandcamp, Qobuz, Amazon, Beatport, CD or Unknown — deduced from the marks stores and rippers leave in the tags, unless the owner chose one
- **Origin choice** — the owner's explicit Origin, or Automatic detection
- **Embedded artwork** — the cover image embedded in each track
- **Folder cover** — the cover.jpg or cover.png beside its files
- **Stand-in artwork** — images it carries that were borrowed from the release group or another release for want of the release's own front
- **Accepted as complete** — the owner has asked Harmonist to stop flagging its missing tracks
- **Accepted release** — the release the owner said is the one they bought, which stops the possible mismatch warning for that release
- **No purchase to link** — the owner accepted that no Bandcamp purchase belongs to it
- **Added** — when Harmonist first found it
- **Possible mismatch** — the reasons its source evidence points to another release in its release group
- **MB contribution** — the next thing its release is missing on MusicBrainz that its files could supply: a store link or a barcode

## States

### New

Harmonist has found the folder but has no record of which release it is.

### Inconsistent

The files in one folder disagree about which album they belong to.

### Needs MBID

There is no confirmed release yet; a suggested match may be waiting for review.

### Tagging

The album's record names a release its files do not carry yet; Harmonist is writing tags or adopting the files' own.

### Needs Linking

Matched and from Bandcamp, but not yet linked to the purchase it came from.

### Incomplete

Matched, with fewer tracks on disk than the files' own totals say the release has.

### Complete

Matched, and nothing above applies.
