---
tags:
  - dwarves
  - work
  - internal
  - discussion
  - event
  - labs
  - catchup
  - LLM
  - rust
title: "Labs Weekly Catchup #1"
date: 2023-12-06
description: Our first weekly catchup. We organize an agenda the day beforehand and consolidate our findings, notable research progress, possibly new tech, insight or technique everyone should know.
authors:
  - monotykamary
menu: labs
type: labs
hide_frontmatter: false
event_date: 2023-12-06
---

| Event Date                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | Discord Channel | Type     |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------- | -------- |
| 06/12/2023 | 🍎 apple   | Internal |

Our first weekly catchup. We organize an agenda the day beforehand and consolidate our findings, notable research progress, possibly new tech, insight or technique everyone should know.

### Agenda:
Among the topics we will cover, there will be a short topic discussion and demonstration on AI Realtime memory knowledge updates by Tom. this will include:
- New approaches to memory consolidation  
- A small preview demo of what it looks like

### Output:
- Understand the research progress and passions of the labs team
- Understand any shortcomings or things to improve for the next weekly catchup

---

## Notes from the catchup
🧠 **AI - Realtime Memory**

- LLMs are now using Retrieval Augmented Generation (RAG) for context and updates.
- Realtime memory is another step into optimizing new data into an LLM's intuition through more unique base prompting.
- Challenges like token limits are being addressed with fewer steps and unique base prompting.

🕹️ **Rust Game Server on Actix**

- Significant progress on the Rust game server built on Actix.
- @khacvy also demoed a short multiplayer shooter game. 👾 
- Exploring Tokio as an alternative framework to see cost benefits between it and Actix.
- Documentation gaps identified, considering better tooling for a smoother development experience.

🎨 **Mochi UI Practices**

- Focus on standardization across Figma designs, component naming, and usability.
- Practices and our open-source standard are mostly finished, with us hosting a workshop at Thursday, December 14, 2023 400 PM.

🌐 **WebStudio - Emerging Tech**

- WebStudio, an open-source low-code helper for building websites similar to WebFlow.
- Utilizes immerhin for large tree synchronization and real-time collaboration.

🌟 **Potential Standards**

- JSON patches (RFC 6902) and design tokens (W3C standard) introduced by WebStudio.
- JSON patches for lightweight changes to JSON documents.
- Design tokens for consistent visual style in design systems.
