---
tags:
  - dwarves
  - work
  - internal
  - discussion
  - event
  - labs
  - catchup
  - rust
  - elixir
  - LLM
title: "Labs Weekly Catchup #2"
date: 2023-12-14
description: Our second weekly catchup. We organize an agenda the day beforehand and consolidate our findings, notable research progress, possibly new tech, insight or technique everyone should know.
authors:
  - monotykamary
menu: labs
type: labs
hide_frontmatter: false
event_date: 2023-12-13
---

| Event Date                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | Discord Channel | Type     |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------- | -------- |
| 13/12/2023 | 🍎 apple   | Internal |

Our second weekly catchup. We organize an agenda the day beforehand and consolidate our findings, notable research progress, possibly new tech, insight or technique everyone should know.

### Agenda:
- Kick-off topic - Self-hosted AI model in browsers with a quick demo by Thanh Phan and Toan Ho
- Elixir cluster problem: scalability, broadcast messaging, leader election by Hieu Phan
- Compare Rust 101 vs Go with experience in running Rust classes with the team by Hieu
- Rust and understanding monadic error handling by Khac Vy
- AI trending and understanding model and runtime architectures in LLMs by Tom Nguyen

### Output:
- Understand the research progress and passions of the labs team
- Understand any shortcomings or things to improve for the next weekly catchup

---

## Notes from the catchup
🧠 **Self-hosted AI model in browsers:**
- @thanh expressed concerns about the usage and download size of LLMs on weak internet connections.
- @toanho is exploring WebGPU and its application for our use case, although browser support is still limited.
- Action items for next week are being planned.

⚙️ **Elixir Cluster Problem:**
- @hieuthu1 proposed one possible solution in solving Elixir clustering and scalability through using Process Groups to group and orchestrate actions between processes, enabling message broadcasting across multiple instances/pods.
- Raft consensus (leader voting) is also being considered to help orchestrate state and work.

⚖️ **Comparing Rust 101 vs Go:**
- @hieuthu1 discussed the differences in concurrency between Rust and Go, highlighting Rust's focus on functional style and managing references, borrowing, and closures.
- Rust may have a moderate barrier of entry for new learners due to the nuanced understanding required for references and borrowing.
- @hieuthu1 mentioned that a workshop/session on Rust will be organized soon.

🎮 **Rust Game Server:**
- @khacvy demoed a more interactive and flushed UI for the spaceship Rust game.
- He also mentioned the challenges he encountered, and gave a short course in running Rust

💡 **Updates on AI:**
- @Tom shared information about Mixtral 8x7B AI, based on Mixture of Experts.
- Mixture of Experts is extensively used in ChatGPT, but advancements in multi-agent LLMs have led to clearer architectures for scaling multi-modal and specialized infrastructure.
