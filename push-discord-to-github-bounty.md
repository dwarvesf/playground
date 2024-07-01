---
tags:
  - ops
  - bounty
title: "Bounty: Push note from Discord to Github PR automatically"
date: 2024-07-01
description: "Seeking developers for an exciting bounty: Create an automation feature to automatically convert popular Discord links into fleeting notes. Implement a reward system, set up eligibility criteria, and develop an automated process for creating GitHub Pull Requests with article summaries. Enhance our tech community's knowledge sharing efficiency."
authors: 
  - minh_cloud
---

Last week, we announced about the reward system for fleetings notes, we understand that knowledge can come from everywhere: trainings, articles,... As there were thousand links shared in our channel #tech of our community, we want to take advantage of this activity to enrich our knowledge with the minimum effort. Therefore, we aim to build a feature in Tono bot which automatically transfer an endorsed link to a fleeting note. 

A link is eligible to be transfered to fleeting note when it has more than 5 star endorsed by community or when a member having senior role add to the fleeting note by the command /add-fleeting-note. 

This bounty expect you to deliver
- A command to transfer a link to a fleeting note: `/add-fleeting-note`.
- Automatically transfer a link having 5 stars and confirmed by the senior to a fleeting note.
- For every eligibile and confirmed article, automatically generate the summary from that and create a Pull request in which the summary file nested in folder [00_fleeting of playground](https://github.com/dwarvesf/brain/tree/master/00_fleeting). 

**Follow this flow**
![](assets/push-discord-to-github-bounty_untitled-9.webp)

**Documents**
- Detail instruction of UI: [here](https://www.notion.so/Push-from-Discord-to-Github-c405ccd051c141a79f424450e7278071)
- UI mock up: [here](https://share.discohook.app/go/739ex6n7) 
