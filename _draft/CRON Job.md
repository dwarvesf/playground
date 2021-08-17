---
tags: development, practice
---

### What
A system daemon to execute task on designed times.

*daemon*: run in linux system. works underlying in background

It's a long-running process to execute command at specifice date/time

### How it works
Using crontab file.
A configed text file, contains a list of command to schedule tasks. 
This file can be edit/ adjust using crontab command

*crontab command*: list of action you wish to execute

### Example
**Format**
- minute
- hour
- day
- month
- day of the week
- command

`30 09 ** 08 * / home/ramesh/update-db`

task: Auto update database at 09:30AM on every day of August

**Source**
- https://ostechnix.com/a-beginners-guide-to-cron-jobs/
- https://www.marksanborn.net/linux/learning-cron-by-example/
- https://www.thegeekstuff.com/2009/06/15-practical-crontab-examples/