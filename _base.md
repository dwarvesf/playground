---
tags:
  - dwarves
  - labs
  - home
title: Labs Team
date: 2023-11-30
description: This is our Labs team homepage, where we list out the latest advances in our engineering team, our publications, events & workshops, as well as frequently asked questions on who and what team labs are.
authors:
  - monotykamary
hide_frontmatter: true
---
<!-- col-2 #1 -->
<!-- labs-latest -->

## Latest from Labs Team
```dataview
LIST
FROM "labs" AND !"labs/_index" AND !"labs/_base"
SORT date DESC
LIMIT 10
```
<!-- /labs-latest -->
<!-- forward-engineering-publications -->

## Forward Engineering Publications
```dataview
LIST
FROM #forward-engineering
SORT date DESC
LIMIT 3
```
<!-- /forward-engineering-publications -->
<!-- /col-2 #1-->

<!-- col-2 #2 -->
<!-- faq -->

## Frequently Asked Questions (FAQ)
### Who we are
At Labs, our team is united by a shared passion for new technologies. We are a diverse group of individuals, each with unique backgrounds and personalities, but our common ground lies in our dedication to exploring and understanding emerging technologies. Our goal is to investigate and learn about advancements that have the potential to enhance our lives and contribute to a better future.

For a deeper insight into the core beliefs that drive us, please visit this [[Labs - Who we are|link]].

### How we work
We collaborate to exchange insights about emerging technologies and assess their potential for innovative applications. In partnership with consulting and product teams, we rigorously reexamine our assumptions and immerse ourselves hands-on in these technologies. Our goal is to ensure that these advancements are not only practical but also instrumental in unlocking the doors to the future.

For a comprehensive understanding of our workflow, please refer to the detailed documentation available in this [[Labs x Consulting Workflow|note]].

### What we are working towards
We are diligently exploring and analyzing trending technologies, identifying those with the potential to unleash innovations and shape a promising future. To discover the latest technologies we are focusing on, please explore our roadmap [[Labs Roadmap (Nov 23 update)|here]].

### How to become a member?
Currently, we primarily onboard new members through recommendations from existing members of our Labs team. However, if you're not yet connected with us but aspire to join, we invite you to actively contribute to tech discussions on our Discord server. Demonstrate your passion for technology there. We are always on the lookout for like-minded individuals and will warmly welcome those who share our enthusiasm and mindset.

Once invited, you'll be paired with a mentor who will guide you through our operational practices and assist you in focusing on a specific research topic. You'll have one month to delve into this topic, culminating in the presentation of a technical report and a demonstration highlighting the advantages of the new technology.

For a detailed outline of the onboarding process, please refer to [[Labs - New Member Onboarding|our guidance]].

### How to propose a topic?
Only members of the labs and consulting teams can officially propose new topics. However, if you're not part of these teams, you can still catch our eye by sharing your insights or discoveries on our Discord server. Our labs team is always eager for fresh ideas, and if your topic truly stands out, we'll not only champion it but also express our gratitude with some ICY tokens as appreciation. See more details [[Labs - Topic proposal & progress tracking|here]].

### How do we reward?
We celebrate your technological contributions by awarding ICY tokens, with the amount varying based on the impact of your input. This could range from enriching our knowledge base to driving real-world innovation. For more details on how we value different contributions, you can refer to our guidelines [[Reward Model & Nomination|here]].

For Dwarves team members, engaging in future research projects is an excellent way to foster personal growth. Your R&D outputs play a crucial role in our performance evaluations. To understand how your research and development efforts contribute to your performance review, please visit [[How R&D contributes to Performance Review|this note]].

<!-- /faq -->
<!-- events -->

## Events
### Upcoming
```dataview
LIST description
FROM #labs AND #event 
LIMIT 3
WHERE event_date >= date(today)
SORT event_date DESC
```

### Past Events
```dataview
LIST description
FROM #labs AND #event 
LIMIT 3
WHERE event_date < date(today)
SORT event_date DESC
```

<!-- /events -->
<!-- /col-2 #2 -->

---

![](assets/_base-20231130183110925.webp)
