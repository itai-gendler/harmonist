---
appliesTo:
- type: entity
  id: artwork-update
  effect: creates
permits:
- unattended: true
  when:
  - entity: settings
    fact: Library updates
    is: Find updates for review
- actors:
  - owner
references:
- kind: code
  role: implementation
  target: src/harmonist/artwork_updates.py#sweep
---

# The background check finds artwork updates only while Library updates is Find updates for review

The Cover Art Archive is asked in the background only under the same setting; the owner's own refresh asks it whatever the setting says.
