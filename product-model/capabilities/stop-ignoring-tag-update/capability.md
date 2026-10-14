---
availability:
- place: web
references:
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#ignore_update
- kind: code
  role: implementation
  target: src/harmonist/activity_store.py#unignore_update
---

# Stop ignoring a tag update

The owner unticks Ignore until MusicBrainz changes, so the album's update is listed again whether or not MusicBrainz has changed.
