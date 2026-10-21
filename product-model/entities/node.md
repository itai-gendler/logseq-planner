---
references:
- kind: code
  role: implementation
  target: src/core/normalize.ts#buildNodes
- kind: code
  role: implementation
  target: src/core/nodes.ts#resolveSpan
relations:
- entity: task
  verb: has linked
  cardinality: many-to-many
---

# Node

A page or block selected by the view’s tags. A task can itself be a node of a view; its graph identity stays the same.

## Information kept

- **Title** — The displayed title with inline references resolved where known.
- **Tags** — Its graph tags and the first selected tag it belongs to in this view.
- **Dates** — The values of its existing date properties.
- **Choices** — Its values of eligible single-valued choice properties.
- **Fields** — Additional selected simple property values shown on cards.
- **References** — Links to other nodes and dependencies from the chosen property.
- **Created day** — Its local creation day, when provided by the graph.
- **Span** — Mapped Start and End, a point, a span derived from linked tasks, or no date.
- **Progress** — Done linked work over non-canceled linked work, with nested children included where applicable.
