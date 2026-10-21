---
scope: Planner plugin entry, interactive and in-page planning, graph interpretation, saved views and graph-backed
  state.
method: Static inspection of tracked source, approved requirements, guide and selected test cases at map-base.
covered:
- description: Plugin entry and Logseq integration for opening, graph switching, persistence and surface selection.
  paths:
  - src/app.ts
  - src/index.ts
  - src/sdk.ts
- description: Graph schema, selected nodes and tasks, dates, filtering, rollups, view calculations and checked
    writes.
  paths:
  - src/core/
- description: Interactive workspace and in-page renderer behavior across all five planning views.
  paths:
  - src/ui/
- description: Saved configurations, remembered graph preferences and legacy configuration reading.
  paths:
  - src/storage.ts
  - src/ui-state.ts
  - src/vendor/plugin-config/
exclusions:
- description: Developer probes, timings and SDK import guard are engineering tools rather than planning contracts.
  paths:
  - src/dev-probe.ts
  - src/dev-timings.ts
  - src/__sdk_guard__.ts
- description: Seed, tracker and probe scripts are development fixtures and maintenance tooling.
  paths:
  - scripts/
- description: Build, packaging and continuous integration files do not define planning behavior.
  paths:
  - vite.config.ts
  - tsconfig.json
  - package.json
  - .github/
- description: Theme, icon, styling and host key forwarding mechanics are presentation and integration design linked
    from the existing guide.
  paths:
  - src/ui/theme.ts
  - src/ui/theme.css
  - src/ui/host-icons.ts
  - src/ui/host-keys.ts
  - src/ui/block-style.ts
  - src/ui/dock-neighbours.ts
unmapped:
- description: Fine-grained dock resizing and Timeline title-width manipulation are peripheral layout controls;
    preference retention is covered.
  paths:
  - src/ui/dock-resize.ts
  - src/ui/workspace.ts
limitations: []
---

# Coverage
