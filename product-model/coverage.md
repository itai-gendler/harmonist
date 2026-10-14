---
scope: 'The Harmonist application: its web interface, background work and the code behind them.'
method: Static inspection of source, templates and documentation; nothing was run.
covered:
- description: 'Application code: scanning, matching, tagging, artwork, history, Bandcamp sync and the web routes.'
  paths:
  - src/harmonist/
- description: Page templates and the artwork viewer script.
  paths:
  - templates/
  - static/artwork-viewer.js
exclusions:
- description: Automated tests and browser tests.
  paths:
  - test/
- description: Container, build and CI configuration.
  paths:
  - Dockerfile
  - docker-compose.yml
  - Makefile
  - pyproject.toml
  - .devcontainer/
  - .github/
  - .dockerignore
- description: Compiled and source stylesheets.
  paths:
  - static/harmonist.css
  - static/input.css
- description: Developer scripts.
  paths:
  - scripts/
- description: Agent instructions and skills.
  paths:
  - .agents/
unmapped:
- description: 'Demo mode: the sample library, simulated services and Reset Demo.'
  paths:
  - src/harmonist/demo.py
  - templates/partials/demo_banner.html
- description: Built-in password, hostname checking and the password-hash command.
  paths:
  - src/harmonist/web/security.py
- description: The About page.
  paths:
  - templates/about.html
limitations: []
---

# Coverage
