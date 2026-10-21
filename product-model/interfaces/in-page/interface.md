---
type: web
actors:
- planner-user
references:
- kind: code
  role: implementation
  target: src/ui/block.ts#createBlocks
- kind: code
  role: implementation
  target: src/app.ts#SLASH_COMMAND
- kind: doc
  role: intent
  target: docs/guide.md
---

# In-page Planner

The read-only saved-view renderer in a Logseq page. People insert a Planner view block, read its results, open its items in Logseq or continue in Planner. Logseq persists the containing page.
