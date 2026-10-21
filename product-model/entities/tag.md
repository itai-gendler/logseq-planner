---
references:
- kind: code
  role: implementation
  target: src/core/schema.ts#buildTagInfos
relations:
- entity: property
  verb: offers
  cardinality: many-to-many
- entity: node
  verb: classifies
  cardinality: many-to-many
---

# Tag

A built-in or user-created tag whose nodes can be planned.

## Information kept

- **Title** — The tag name shown to the user.
- **Built in** — Whether Logseq supplies this tag.
- **Parents** — Tags this tag extends.
- **Properties** — Own and inherited properties available for planning.
