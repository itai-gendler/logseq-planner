---
availability:
- place: planner
references:
- kind: code
  role: implementation
  target: src/ui/workspace.ts#timeline
- kind: doc
  role: intent
  target: docs/guide.md
domain: timeline
---

# Collapse nested node

Fold a nested parent so the Timeline lists it without its child nodes. Nested parents start open; the fold lasts for the session.
