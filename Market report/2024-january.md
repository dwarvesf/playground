---
tags:
  - labs
  - market-report
  - AI
  - rust
  - frontend
  - htmx
  - LLM
  - cybersecurity
title: Market report January 2024
short_title: January 2024
date: 2024-01-26
description: Here are some of the few trends we are seeing across the industry, in our projects, as well as our community. This market report isn't exhaustive, at least just yet, with certain trends not yet listed such as Blockchain, data management, DevEx, etc. We see a lot of promising trends and we hope that understanding what engineers and firms are becoming more passionate about that it will help us create a foundation of ideas and knowledge.
authors:
  - monotykamary
  - thanh
---

## Trends on our radar

Here are some of the few trends we are seeing across the industry, in our projects, as well as our community. This market report isn't exhaustive, at least just yet, with certain trends not yet listed such as Design, DevEx, etc. We see a lot of promising trends and we hope that understanding what engineers and firms are becoming more passionate about that it will help us create a foundation of ideas and knowledge.

### Stagnation of React and the need to simplify the frontend

React has been the powerhouse to many small, medium, and large enterprise systems. It's declarative model along with the backing of Facebook plus its expansive ecosystem makes it the default go-to library for frontend systems. However, There has no major update in the recent two years, with a lot of the core members moving towards Vercel and Next.js. Next.js and Vercel have become extremely prevalent in every startup stack which has raised concerns of **vendor lock-in**, not to mention **increase in prices** for their services. In addition, there has been greater demand to move towards Multi-Page Applications (MPAs), vs what React commonly aims for: Single-Page Applications (SPAs), which creates a competition space against React.

To add upon, there have been more interest towards HTMX, both in our community, team, and the industry. HTMX is a library that simplifies HTTP request handling by making common functionality available via HTML attributes. Since it complements HTML, it can fit into almost every type of frontend application that interacts with the Web. It's been trending as the ideal way to minimize JavaScript usage across apps.

### A rising ecosystem of Rust applications

Rust’s ecosystem is constantly improving and expanding. Many big projects use Rust and experience the success that the power of the language brings. Some examples of projects using Rust are Zed, a code editor, and Mastro, a UNIX-like OS. Moreover, in the most accessible environment - the web, Rust is becoming a mainstream choice for front-end infrastructure and compiler engines. Just recently, Servo, a new Rust-based browser engine, was released. We can expect Rust to have more applications playing the role for rendering UI, as it enables compilation into higher-quality WebAssembly code, with its presence will gradually appear in browsers. The idea to "Rewrite It In Rust" (RIIR), once a meme, is now unironically becoming the approach to act as the most rounded programming language in the industry.

### Rise of in-house, AI-assisted productivity tools

The rise in in-house productivity tools is driven by the need for businesses to adapt to remote work, improve efficiency, facilitate collaboration, and enhance employee motivation and satisfaction. Although there are a myriad of tools, **there is not a single tool that rules them all** and fits the needs of specific use-cases for certain firms. There is a common trend to **move away from data silos and fragmented tooling to more highly integrated software**.

Likewise, tightly coupled integration of data enrichment for AI virtual assistants has allowed them to become generally available as consumer products. Although not a new trend, AI with knowledge enrichment has been a growing effort across all industries. Complex task AI apps like [Taskade](https://www.taskade.com/) as well as complementary apps like [Murf](https://murf.ai/) and [ElevenLabs](https://elevenlabs.io/) have changed the landscape for what a productivity tool can provide.

### The big step towards LLMs away from OpenAI

`mistral-medium`, one of Mistral's strongest (and currently not open-sourced LLMs) have been in closed-preview to a select few API subscribers. It has been touted as being able to compete with GPT4, which creates a path to democratizing LLMs strong enough to move away from OpenAI. Lately, there have been news that they accidentally leaked [`miqu-1-70b`](https://anakin.ai/blog/miqu-1-70b/). There are mixed reviews as to whether it beats GPT4, but it is still pretty close along with many of the state-of-the-art LLMs on comparative benchmarks. The space for LLM engineering has been growing at a break-neck pace, closing the gap of large companies like OpenAI, Anthropic, and Google within the past year.

### Trading bots

**Trading bots** are automated software programs designed to execute buy and sell orders in financial markets, including **currencies**, **stocks**, **crypto**, and other assets. These bots operate autonomously, allowing traders to engage in passive trading 24/7. Precision trading bots such as 1000pip Climber System, Waka Forex, and for crypto - L2T Algo, are some of the few popular ones leading up to 2024.

Across both the crypto world and in the finance industry, there has been growing consumer and business demand for trading bots and price watchers. The problem space isn't new, but there are many areas for optimization which traders want to take advantage of. Likewise, there is a demand for copy trading for US stocks on winning traders, people in congress, and notable figures.

### A need for updating cybersecurity

With an increase in cybercrime with the [‘Mother of all breaches’](https://www.msn.com/en-us/money/other/mother-of-all-breaches-data-leak-reveals-26-billion-account-records-stolen-from-twitter-linkedin-more/ar-BB1h8uz2) and the Congress hearing on [child safety on social networks](https://www.msn.com/en-us/news/technology/tiktok-snap-x-and-meta-ceos-grilled-at-tense-senate-hearing-on-social-media-and-kids/ar-BB1hxlbh), the demand for cybersecurity is higher than ever. Ransomware attacks continue to plague organizations worldwide, with these malicious incidents demanding better response strategies and proactive measures to prevent them. In addition, cybercriminals are increasingly using AI to craft sophisticated social engineering attacks.

In the industry, there is a growing **skill gap** for cybersecurity engineers, creating demand on initiatives for upskilling and reskilling know-how on cybersecurity. The concept of [Zero Trust](https://www.isaca.org/resources/news-and-trends/industry-news/2023/track-these-7-trends-for-proactive-cybersecurity-in-2024)—where no one is automatically trusted, even within the organization—has gained much higher prominence leading up towards 2024.

## References

- [穿越时空：2023 年前端技术盘点与 2024 年技术展望](https://mp.weixin.qq.com/s/LiygBJqMN8U_vSpAjxMibQ)
- [Increased investment in productivity and collaboration tools](https://discord.com/channels/462663954813157376/788084358991970337/1200049567765368882)
- [‘Mother of all breaches’ data leak reveals 26 billion account records stolen from Twitter, LinkedIn, more (msn.com)](https://www.msn.com/en-us/money/other/mother-of-all-breaches-data-leak-reveals-26-billion-account-records-stolen-from-twitter-linkedin-more/ar-BB1h8uz2)
- [The Growing Cybersecurity Skills Gap: Recognizing the Need for Action](https://www.linkedin.com/pulse/growing-cybersecurity-skills-gap-recognizing-need-action-khatri)
- [A New Era of Galaxy AI is Coming — Here’s a Glimpse – Samsung Global Newsroom](https://news.samsung.com/global/a-new-era-of-galaxy-ai-is-coming-heres-a-glimpse)
- [Freethink on X: "#CES2024: AI startup Rabbit’s R1 device sells out in 24 hours https://t.co/Wzr2lzuh68 @rabbit_hmi https://t.co/4l3omjGjfX" / X (twitter.com)](https://twitter.com/freethinkmedia/status/1745560844824396135)
- [NPUs are essential for AI, but what are they, and how do they differ from GPUs? | Windows Central](https://www.windowscentral.com/hardware/what-is-npu-vs-gpu)
- [Django, HTMX and Alpine.JS: A Match Made In Heaven - DEV Community](https://dev.to/nicholas_moen/what-i-learned-while-using-django-with-htmx-and-alpine-js-24jg)
- [React, where are you going?](https://dev.to/matfrana/react-where-are-you-going-5284)
- [Annoyed at React](https://blog.cassidoo.co/post/annoyed-at-react/)
- [Trending Frontend Technologies](https://virtuslab.com/blog/trending-frontend-technologies/)
- [Zed Repository](https://github.com/zed-industries/zed)
- [Servo Repository](https://github.com/servo/servo)
- [Mistral CEO confirms ‘leak’ of new open source AI model nearing GPT-4 performance](https://venturebeat.com/ai/mistral-ceo-confirms-leak-of-new-open-source-ai-model-nearing-gpt-4-performance)
- [Taskade](https://www.taskade.com/)
- [13 Best Trading Robots for February 2024 Reviewed (techopedia.com)](https://www.techopedia.com/investing/best-trading-robots)
- [Track These 7 Trends for Proactive Cybersecurity in 2024](https://www.isaca.org/resources/news-and-trends/industry-news/2023/track-these-7-trends-for-proactive-cybersecurity-in-2024)
