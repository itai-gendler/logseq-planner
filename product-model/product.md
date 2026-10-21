---
id: logseq-planner
summary: Planning views over the tags, dates and choice properties in a Logseq DB graph.
category: productivity
tags:
- planning
- logseq
- calendar
- kanban
authors:
- name: hdansou
license: MIT
languages:
- en
limitations:
- Planner requires a Logseq DB graph; file graphs are not supported.
- Planner uses existing tag properties and leaves creation of user schemas and general node editing to Logseq.
- In-page Planner views are read-only; editing happens in the interactive Planner surface.
- The sidebar surface requires the Logseq desktop app.
- A view is defined by its tags and shared filters; Planner offers no free-query views, no filters per tag and no
  repeating tasks.
references:
- kind: doc
  role: intent
  target: README.md
- kind: spec
  role: intent
  target: REQUIREMENTS.md
- kind: doc
  role: intent
  target: docs/guide.md
- kind: code
  role: implementation
  target: src/app.ts#registerApp
---

# Planner

Planner shows the nodes of any tag in a Logseq DB graph as a Timeline, Calendar, Agenda, Kanban board or Matrix. People plan with their own tags and properties, save views in the graph, and change dates or choice values directly from planning views. Logseq supplies the graph, its persistence and the surrounding page experience.

This Product Model complements the [approved requirements](../REQUIREMENTS.md), [Using Planner](../docs/guide.md), [limits](../docs/limits.md) and [plugin config convention](../docs/plugin-config.md). Read them together; the model does not replace those specifications.

## Intent

In the project's own words, Planner exists to "show the nodes of any tag in a Logseq DB graph, including tags users create" as planning views ([requirements](../REQUIREMENTS.md)). Its user stories say why: someone who plans in Logseq sees "every project on a timeline with how far along it is, so I know what is on track"; a task user sees "what is overdue and what is due in the next two weeks in one list"; a project lead sees "project spans and the deadlines inside them"; a team member moves cards across a Kanban board "and the change is saved on the node"; and a returning user saves a view that "is there on my other devices because it lives in the graph". The [README](../README.md) adds the Matrix to the original four views and runs Planner in a workspace, a desktop sidebar and read-only views in pages.
