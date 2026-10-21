---
references:
- kind: code
  role: implementation
  target: src/core/schema.ts#collectProps
---

# Property

An existing graph property interpreted by Planner. Properties retain graph identity across title changes.

## Information kept

- **Title** — The displayed property name.
- **Type** — Date, DateTime, choice, node reference or another supported simple value type.
- **Cardinality** — Whether one or several values can be held.
- **Closed values** — The property’s allowed choices, their order, titles and built-in done or canceled meanings when present.
- **Hidden** — Whether the property is hidden from card-field selection.
