---
tags:
  - labs
  - market-report
  - AI
  - LLM
title: Market Report May 2024
date: 2024-06-19
description: In May's market report, we explore GPT-4o's advancements, the rising demand for veteran programmers, the transformative power of prescriptive AI, React 19's impact on network gaps, the growing complexity of GraphQL codebases, and Bend, a new parallel programming language.
authors:
  - thanh
  - monotykamary
---

## Key Takeaways

- GPT-4o's new advancements can challenge many current businesses while making LLMs foundational for a new wave of software applications.
- The demand for advanced and veteran programmers is rising as companies seek seasoned professionals who can navigate complex challenges and contribute significantly from day one.
- Prescriptive AI is transforming industries by providing actionable recommendations based on data insights, enhancing decision-making processes and operational efficiency.
- React 19 aims to manage the network gap, which might make traditional frontend-backend API connection code obsolete.
- Growth in GraphQL codebases increases complexity problems, leading to a preference for traditional REST APIs.
- Bend, a new parallel programming language designed to optimize the usage of multiple computers or cores, appears ideal for data processing and machine learning tasks.

## GPT-4o: Opportunities and Disruptions

OpenAI has released GPT-4o, a model with enhanced emotional recognition and output capabilities that can interrupt conversations when appropriate, giving users the feel of talking to a real person. Compared to previous versions, GPT-4o has made significant improvements in natural language processing, conversation fluency, and emotional expression. Whether it's for everyday conversations or professional inquiries, ChatGPT-4o provides accurate and in-depth answers. This advancement could disrupt existing business models and technologies, particularly in conversational AI, Ed-tech, and call centers, which may struggle to keep up with the rapid progress of AI.

We have already seen individuals use the capabilities of multimodal reasoning and generation to handle complex tasks, such as watching hours of video, writing reports, and sending them to relevant parties. With a large context window of up to 128,000 tokens and faster, cheaper APIs, the efficiency and scope of these models have dramatically increased.

Large Language Models (LLMs) like those from OpenAI are becoming foundational for a new wave of software. The release of GPT-4o suggests that these models should be considered akin to operating systems (OS), upon which many rich applications can be built.

Moreover, we think there will be a growing trend of connecting LLM platforms with various data sources and types. For instance, integrating a chat interface with data services to extract insights from reports. This process involves reading diverse data sources and translating them into useful insights. Additionally, there is an increasing demand for optimizing frontend user experiences, such as rendering charts or 3D models based on processed data.

![[may-2024-market-report-gpt4o.png]]

_Integrate GPT-4o chatbot with Google Sheets to generate insights from reports._

## Job Market Trends: Demand for Advanced and Veteran Programmers

The demand for advanced and veteran programmers is rising as companies seek to address the increasing complexity of modern software development and the need for efficient problem-solving skills. Many organizations now prefer candidates with extensive experience over newcomers. This trend is partly driven by the limitations observed in some programmers' skills, leading companies to favor seasoned professionals who can navigate complex challenges and contribute significantly from day one, now with the demand for hardware engineering growing.

The barrier to entry for programming has never been lower than before with AI, but now with emerging barriers for more bespoke and advanced software. We expect this trend to continue, as there has been great emphasis and importance on continuous learning and skill enhancement in the tech industry.

## The Rise of Prescriptive AI

Prescriptive AI is becoming a significant trend, offering solutions that go beyond predictive analytics by recommending actions based on data insights. This form of AI can transform industries by optimizing decision-making processes and operational efficiency to enable resilient supply chains or better manage public finances. One example, in manufacturing, prescriptive AI analysis can process vast amounts of vision data to suggest improvements, reduce downtime, and recommend/alert on urgent fixes. Its ability to provide actionable recommendations makes it a powerful tool for businesses aiming to leverage data for strategic advantage.

With agentic designs for AI being more mainstream, we think that the integration of prescriptive AI will soon become a standard practice across various sectors, driving innovation with actionable AI assistants in both the software and hardware space.

## Web Development Shift: Is Your Code Outdated?

The web development landscape is undergoing a transformative shift. React 19 has introduced a major change, reflecting the evolving nature of JavaScript frameworks and the ongoing debates in the developer community. A significant trend is the move towards keeping HTML templates on the server while maintaining front-end interactivity similar to technologies like Hotwire and LiveView. React, traditionally focused on component-based development, is now venturing into this space, offering solutions for managing the network gap.

The seamless integration between the frontend and backend in React eliminates the need for developers to worry about data passing between them. Although it may seem unconventional for a frontend library to handle network and backend tasks, the "[Mind The Gap](https://www.youtube.com/watch?v=zqhE-CepH2g)" demo showcased React components rendered on the server and then teleported to the browser. This blurring of the network gap between frontend and backend frameworks, while maintaining high interactivity on the client side, is an approach worth exploring. Developers should stay curious about these new methodologies as they could potentially make traditional frontend-backend API connections obsolete.

![[may-2024-market-report-react-19.png]]

_React code can now interact with the network and a small part of the backend._

## GraphQL: Not Our Choice

GraphQL is a technology we have never fully committed to. While we have experimented with it and inherited projects that use it, we prefer the simplicity of having all API endpoint code in one file rather than navigating the complexities of GraphQL’s various layers and models. JSON REST APIs remain our preferred choice.

A recent [debate](https://bessey.dev/blog/2024/05/24/why-im-over-graphql/) highlighted dissatisfaction with GraphQL. Like many trendy technologies, GraphQL works well for small projects but becomes problematic as project requirements grow more complex. Increased adoption and demand on the API lead to more debugging time. GraphQL exacerbates these challenges, with vague issue descriptions, harder-to-find log entries, and performance issues appearing randomly. For us, the "boring" REST API remains the preferred choice.

## Bend: A Parallel Programming Language for the AI Age?

This month introduced [Bend](https://higherorderco.com/), a new programming language designed to scale performance by default on massively parallel hardware like GPUs. Parallel computing accelerates problem-solving by using multiple computers or cores, but it can be challenging due to synchronization issues. Bend simplifies this by making parallelism the default, requiring no specialized knowledge of CUDA or other parallel technologies.

Bend replaces traditional loops with the concept of “fold,” allowing recursive data types to be consumed in parallel. The performance gains are significant, with code execution times dropping from 30 seconds on a CPU to just 1.5 seconds on a GPU using Bend. Despite its high-level features akin to Python and Haskell, Bend supports fast object allocations, higher-order functions with closures, unrestricted recursion, and continuations, making it an exciting prospect for data processing and machine learning tasks.

![[may-2024-market-report-ben-lang.png]]

## References

- [https://openai.com/index/hello-gpt-4o/](https://openai.com/index/hello-gpt-4o/)
- [https://platform.openai.com/docs/models/gpt-4o](https://platform.openai.com/docs/models/gpt-4o)
- [https://openai.com/index/improvements-to-data-analysis-in-chatgpt/](https://openai.com/index/improvements-to-data-analysis-in-chatgpt/)
- [https://openai.com/index/be-my-eyes/](https://openai.com/index/be-my-eyes/)
- [https://github.com/HigherOrderCO/Bend](https://github.com/HigherOrderCO/Bend)
- [https://bessey.dev/blog/2024/05/24/why-im-over-graphql/](https://bessey.dev/blog/2024/05/24/why-im-over-graphql/)
- [https://news.ycombinator.com/item?id=40521518](https://news.ycombinator.com/item?id=40521518)
- [Mind The Gap" by Ryan Florence](https://www.notion.so/Market-Report-May-2024-9ad25dcb3fbb4a0ebb9744a44733913c?pvs=21)
- [https://news.ycombinator.com/item?id=40224213](https://news.ycombinator.com/item?id=40224213)
- [https://x.com/aznweng/status/1780594562597081362](https://x.com/aznweng/status/1780594562597081362)
- [https://www.linkedin.com/pulse/data-driven-manufacturing-exploring-intersection-ai-analytics-goyal-exqcc/](https://www.linkedin.com/pulse/data-driven-manufacturing-exploring-intersection-ai-analytics-goyal-exqcc/)
- [https://www.tandfonline.com/doi/full/10.1080/00207543.2024.2341415](https://www.tandfonline.com/doi/full/10.1080/00207543.2024.2341415)
- [https://graphite-note.com/prescriptive-data-analysis-game-changer-for-businesses/](https://graphite-note.com/prescriptive-data-analysis-game-changer-for-businesses/)
- https://one.oecd.org/document/GOV/SBO(2024)14/en/pdf
