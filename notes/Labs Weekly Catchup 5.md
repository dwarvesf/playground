---
title: "Labs Weekly Catchup #5"
date: 2024-01-03
description: Our fifth weekly catchup to kick off the new year! We organize an agenda the day beforehand and consolidate our findings, notable research progress, possibly new tech, insight or technique everyone should know.
authors:
  - monotykamary
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
event_date: 2023-12-13
---

| Event Date                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | Discord Channel | Type     |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------- | -------- |
| 03/01/2024 | 🍎 apple   | Internal |

Our fifth weekly catchup. We organize an agenda the day beforehand and consolidate our findings, notable research progress, possibly new tech, insight or technique everyone should know.

### Agenda:
- Auto pass reCAPTCHA by @Toan Ho
- Passkey demo by @Tay
- Github Trending Analyzer use-case discussion by @Hieu

### Output:
- Understand the research progress and passions of the labs team
- Understand any shortcomings or things to improve for the next weekly catchup

---

## Notes from the catchup
weekly meeting #5 - 03/01/2024:

🤖 **Auto-pass reCAPTCHA followup**
- A follow up of @Toan's demo ov YoloV8 over Tensorflow.js, using WebGPU as the backend, to do object detection over recaptcha images
- @Toan demo includes image autodetection, keyword detection, object separation, and auto clicking.

![](assets/labs-weekly-catchup-5-20240105153824098.webp)

🔒 **Passkey demo**
- A continuation effort with @Tay
- (@Tay) Uses Golang library instead for the backend server
- (@Tay) Different from magic links where it uses JWT token and a verification flow
![](assets/labs-weekly-catchup-5-20240105154513918.webp)

🚀 **Github Trending Analyzer use-case discussion**
- @Hieu Scaffolded a repository for scraping web data from GitHub trending, user profile, stars, and contributions
	- ![](assets/labs-weekly-catchup-5-20240105155035154.webp)
- (@Hieu) Today is more of a general discussion as to what use-cases there should be for the app
- (@Hieu) The application uses TimescaleDB to allow for high ingest rates, currently requires a bit of remodeling and general constraints
	- ![](assets/labs-weekly-catchup-5-20240105155040503.webp)
