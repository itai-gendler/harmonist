---
type: web
actors:
- owner
entryPoints:
- web: /
references:
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#index
- kind: code
  role: implementation
  target: src/harmonist/web/security.py#BasicAuthMiddleware
- kind: doc
  role: intent
  target: docs/security.md
  title: Security
---

# Web

The browser interface the owner manages everything from: the Inbox, the
Library, the Activity feed, each album's page and Settings, with the Bandcamp
sync control in the header. Signing in is left to the owner's reverse proxy, or
to the optional built-in password turned on in the configuration file.
