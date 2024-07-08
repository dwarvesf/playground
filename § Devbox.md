---
tags:
  - moc
  - devbox
title: Devbox Map of Content
description: "A map of content for Devbox, a utility for isolated, reproducible development environments that can run anywhere without Docker or virtual machines using Nix."
date: 2024-07-08
authors:
  - hnh
  - monotykamary
---

## Memos

```dsql-list
SELECT markdown_link(title, file_path)
FROM vault
WHERE ['devbox'] && tags
ORDER BY date DESC
LIMIT 10;
```