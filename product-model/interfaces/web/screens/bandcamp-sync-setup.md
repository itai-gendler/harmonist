---
entities:
- entity: settings
  collects:
  - Bandcamp login cookies
references:
- kind: code
  role: implementation
  target: templates/partials/bandcamp_setup_modal.html
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#bandcamp_cookies
---

# Set up Bandcamp sync

Where the owner gives Harmonist their Bandcamp login cookies, pasted or
uploaded as a cookies.txt file, reached from the header before sync is set up
and from the Bandcamp section of Settings.
