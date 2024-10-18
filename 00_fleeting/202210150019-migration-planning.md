---
authors:
 - cor3.co
description: Migration planning is a crucial part of any software development project, especially when migrating to a new database or platform.
title: Migration Planning
tags:
 - migrations
date: 2022-10-14
---

https://newsletter.pragmaticengineer.com/p/real-world-engineering-challenges

tl;dr
**Migration plan**
What do we need to consider?
- Downtime
- Data consistency
- Rollback plan
- Observable and measurable
- Team awareness

Common steps
- Dual reads / writes -> old database is primary
- Backfilling
- Compare and validate new database
- Dual reads / writes -> new database is primary
- Remove old database
