---
tags:
  - labs
  - market-report
  - AI
  - LLM
title: Market Report Mar 2024
date: 2024-03-01
description: 
  - monotykamary
  - thanh
menu: labs
type: labs
hide_frontmatter: false
pinned: true
hide_title: false
---

In this month's market report, we explore the evolving landscape of artificial intelligence, API techniques, toolings, programming languages, and the intersection of design and engineering. Our insights shed light on the dynamic shifts and emerging trends across these domains, highlighting the advancements that are shaping the future of technology and software development.

## Subtle advances in app design for LLMs pave the way for advance assistants
Apps like [Devin AI](https://preview.devin.ai/), [Devika](https://github.com/stitionai/devika), [GPT-Pilot](https://github.com/Pythagora-io/gpt-pilot) (also backed by YCombinator), and many others are a signal of a more robust AI scene where platforms are now powerful and fast enough to host complex agents. With now many ways to design an app for LLMs, the platforms that surround them are given better peformance, lower latencies, and more robust logic to maintain coherency that allows the designs of multi-agent applications. Libraries like [Langgraph](https://blog.langchain.dev/langgraph-multi-agent-workflows/) and [Autogen](https://github.com/microsoft/autogen) are some of the toolings that have made great steps into complex and stateful AI application design. In addition, there is a ton of research in different styles of application design that we might see grow in the upcoming months, such as [LLMCompiler](https://github.com/SqueezeAILab/LLMCompiler/blob/main/figs/thumbnail.png), [Plan-and-Execute](https://github.com/langchain-ai/langgraph/blob/main/examples/plan-and-execute/plan-and-execute.ipynb), [Reasoning without Observation](https://github.com/langchain-ai/langgraph/blob/main/examples/rewoo/rewoo.ipynb) and AI feedback loops.

## Open Source AI Repositories: A Surge in Innovation
[Huyen Chip's comprehensive analysis](https://huyenchip.com/2024/03/14/ai-oss.html) of over 845 open-source repositories, each with more than 500 stars, reveals significant insights into the AI tools domain. Following the introduction of transformative technologies like Stable Diffusion and ChatGPT in 2023, there was a noticeable explosion in the creation of new AI tools. This surge began to stabilize by September 2023, indicating a shift in the competitive landscape of generative AI and a more grounded approach to AI development.

![](https://i.postimg.cc/bv1Xht3d/lab-1.avif)

### Focused Evolution of AI Infrastructure
In the realm of AI infrastructure, categories such as computing management (e.g., [skypilot](https://arc.net/l/quote/dlhznxrv)), serving (e.g., [vllm](https://github.com/vllm-project/vllm)), and monitoring (e.g., [uptrain](https://github.com/uptrain-ai/uptrain)) have seen steady growth. The explosion of interest in model development is particularly evident in areas related to inference optimization, evaluation, and parameter-efficient finetuning, highlighting a concentrated effort to refine AI operational efficiency.

### The Rise of Individual-Led Application Development
Application development remains a highly active domain, predominantly driven by individual developers. This segment covers a diverse range of applications, including coding tools, bots, and information aggregation solutions. Interestingly, tools centered around prompt engineering, AI interfaces, agents, and AI engineering frameworks have gained popularity. Applications initiated by individuals tend to attract more attention than those launched by organizations, suggesting the potential for valuable one-person companies in the AI space.

### Dominance of Tech Giants in AI Contributions
An analysis of GitHub accounts reveals that 19 out of the top 20 AI contributors are from leading technology companies like Google, OpenAI, and Microsoft, with a significant presence of Chinese developers. This dominance underscores the significant resources and influence these entities have in shaping the AI ecosystem.

### Rapid Development and Visibility of AI Projects
The AI domain has witnessed projects that quickly capture significant attention, only to see interest wane over time. However, the pace at which developers are releasing new AI tools demonstrates an impressive ability to innovate rapidly.

## API Techniques and Tooling
### Advancements in Model Training and Compression
- **Retrieval Augmented Fine Tuning ([RAFT](https://techcommunity.microsoft.com/t5/ai-ai-platform-blog/raft-a-new-way-to-teach-llms-to-be-better-at-rag/ba-p/4084674))**: This technique aims to enhance Large Language Models' (LLMs) performance by "pre-studying" relevant documents, improving their Retrieval-Augmented Generation (RAG) capabilities.
- **Long Context Models**: The view towards using [long-context models](https://twitter.com/amanrsanger/status/1772742457937060288?utm_source=ainews&utm_medium=email&utm_campaign=ainews-dbrx-best-open-model-but-not-most-efficient) with extensive custom prompts could potentially eliminate the need for traditional fine-tuning, marking a significant evolution in handling new knowledge within LLMs.
- **Model Compression**: The focus on model compression reflects the necessity to manage latency and costs effectively. The industry has moved from 16-bit to 2-bit, and recent research on [1-bit](https://arxiv.org/abs/2402.17764) quantization, highlighting the ongoing efforts to optimize model efficiency.

### Scalable Vector Database for Enhanced LLM Applications
The Scalable Vector Database emerges as a crucial solution to challenges associated with long-term memory and long-range context dependency in LLM applications. The demand for high-performance vector databases is on the rise, underscoring the importance of advanced indexing algorithms for efficient data retrieval.

![](https://i.postimg.cc/fRG4pK76/labs-2.avif)

## AI Startups breaking the VC barrier
There are a lot of growing startups that are making the scene with more compelling apps. Apps like [Patchwork](https://www.atpatchwork.com/), [PointOne](https://pointone.ai/) backed by YCombinator  - and growing apps on ProductHunt like [Saner.AI](https://www.producthunt.com/products/saner-ai), [Vapi](https://www.producthunt.com/products/vapi). Domains like Law, Medicine, Support Calling have their own set of challenges and although there isn't really any new technology in the AI space, disciplines in organizing and transforming data for use with AI has brought nuance and complexity to these apps that make them differentiate with other software.

## Other Notable Trends
- **Rust Adoption by Google and Microsoft**: While Google advocates for Rust to address [memory safety vulnerabilities](https://security.googleblog.com/2024/03/secure-by-design-googles-perspective-on.html), Microsoft offers [resources](https://microsoft.github.io/rust-for-dotnet-devs/latest/introduction.html) for .NET developers to learn Rust.
- **Emergence of Design Engineers**: The role of design engineers, who bridge the gap between design and engineering, is becoming increasingly prominent. They are poised to lead in areas such as product architecture, design infrastructure, and R&D.
- **TailwindCSS v4 Alpha Release**: The [new version](https://tailwindcss.com/blog/tailwindcss-v4-alpha), rebuilt with Rust and integrated with the Lightning CSS parser, promises a significant performance boost, making it ten times faster than its predecessor.

## References
- https://techcommunity.microsoft.com/t5/ai-ai-platform-blog/raft-a-new-way-to-teach-llms-to-be-better-at-rag/ba-p/4084674
- https://huyenchip.com/2024/03/14/ai-oss.html
- https://gorilla.cs.berkeley.edu/blogs/9_raft.html
- https://www.gartner.com/en/articles/30-emerging-technologies-that-will-guide-your-business-decisions
- https://twitter.com/cognition_labs/status/1767548763134964000
- twitter.com/amanrsanger/status/1772742457937060288
- https://twitter.com/llama_index/status/1772662480210198809
- https://arxiv.org/abs/2402.17764
- https://security.googleblog.com/2024/03/secure-by-design-googles-perspective-on.html
- https://microsoft.github.io/rust-for-dotnet-devs/latest/introduction.html
- https://maggieappleton.com/design-engineer
- https://www.proofofconcept.pub/p/design-engineering