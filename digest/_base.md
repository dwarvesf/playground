---
tags:
  - dwarves
  - work
  - event
title: Events
date: 2023-12-11
description: A collection of both our internal and external events, including the things we do with the Labs team, Consulting team, Operations, team, and the community.
authors:
  - monotykamary
menu: 
type: events
hide_frontmatter: true
---
This page holds a collection of both our internal and external events, including the things we do with the Labs team, Consulting team, Operations, team, and the community.

## Events
```dataview
LIST
FROM #event
SORT event_date DESC
WHERE !contains(file.path, "_index") AND !contains(file.path, "_base")
```
