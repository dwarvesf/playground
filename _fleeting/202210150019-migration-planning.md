---
discord_id: antran#3200
discord_channel: engineering
tags: migrations
date: 2022-10-14
icy: 5
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
@brain master
#migrations 