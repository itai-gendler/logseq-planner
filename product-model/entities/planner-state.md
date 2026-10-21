---
references:
- kind: code
  role: implementation
  target: src/ui/workspace.ts#createWorkspace
- kind: code
  role: implementation
  target: src/ui-state.ts#createUiStore
---

# Planner state

The current planning context and remembered preferences for a graph. Current settings and the selected saved view are distinct: changing the current settings does not replace the saved copy until Update.

## Information kept

- **Selected tags** — The selected tags in selection order.
- **Include child tags** — Whether extending tags contribute nodes.
- **Date mappings** — Start and End chosen separately for each selected tag.
- **Depends on** — The chosen node-reference property, None, or the tag-derived default.
- **Done values** — Overrides for which shared choice values close a node.
- **Filters** — Selected shared choice values and, with multiple tags, selected view tags.
- **Find** — Words sought in displayed node and task titles.
- **Added** — Today or a relative number of creation days, or no creation-date restriction.
- **View kind** — Timeline, Calendar, Agenda, Kanban or Matrix.
- **Timeline settings** — Zoom and arrangement.
- **Calendar settings** — Month, Week, 3 days or Day.
- **Agenda settings** — Grouping by node or date and whether done entries show.
- **Kanban settings** — Columns, swimlanes, hidden columns per property, sort and card fields per tag.
- **Matrix settings** — Axes, band membership and order, mode, labels, hidden values per property and Show done.
- **Saved view** — The saved view whose settings were opened, if any.
- **Anchor day** — The session’s Timeline and Calendar period, initially today; not part of a saved view.
- **Expanded task rows** — Nodes whose linked tasks are expanded for this session.
- **Collapsed parents** — Nested parents whose children are folded for this session.
- **Open Agenda buckets** — Later, No date and Earlier buckets opened for this session.
- **Panel** — Visibility in wide and narrow contexts and remembered folded headings.
- **Focus** — Whether planning controls are temporarily hidden for focused reading.
- **Surface** — Workspace or, on desktop, Sidebar; remembered for the graph on the device.
- **Edit dates** — Whether direct Timeline and Calendar time-grid date editing is enabled; remembered per graph on the device.
- **Error** — The current load or write error, if any.
- **Displayed data** — The graph facts and derived results currently presented.
- **Title width** — The remembered Timeline title width, stored with the graph.
- **Dock width** — The sidebar width remembered on this device.

## States

### Hidden

Planner is closed; remembered settings remain.

### Loading

Planner is loading the graph for use.

### Ready

Planner has completed its initial graph load; an empty graph is also ready.

### Load failed

The initial schema or week-start load failed and can be retried.
