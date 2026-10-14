---
availability:
- place: web
references:
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#ignore_update
- kind: code
  role: implementation
  target: src/harmonist/activity_store.py#ignore_update
- kind: code
  role: implementation
  target: templates/partials/_update_ignore.html
---

# Ignore a tag update

The owner ticks Ignore until MusicBrainz changes to take an album off the Tag updates list while an edit to the release is waiting to be accepted. It is a bookmark, not a refusal: the update returns when the release next changes.
