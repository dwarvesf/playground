---
tags: engineering/ai, ai, chatgpt, llm, vector-database
author: Pham Duc Thanh
github_id: zlatanpham
date: 2023-06-09
icy: 10
---

Large Language Models (LLMs) are increasingly central to a range of applications, spanning from natural language processing tasks to predictive typing and beyond. A significant challenge with these models, however, lies in their processing speed and computational cost. But with the emergence of a novel approach to query caching, there's promise of a radical transformation, enhancing efficiency and cost-effectiveness of LLMs.

This innovative technique relies on semantic vector databases, taking advantage of the semantic similarities between queries. In practice, when an LLM processes a query and provides an answer, this response is cached for potential future use. If a later query is semantically similar to a previous one, the system can simply retrieve the cached answer, bypassing the need for additional, time-consuming computations.

![[LLM query caching.png]]

Consider an e-commerce context as an example. If a customer asks an AI assistant, _"What are the store's operating hours?"_ and the AI responds, the system caches this response. When another customer later asks a semantically similar question—_"When does the store open and close?"_—the system leverages the cached answer, averting the need for another processing cycle. This approach significantly reduces computational time and resources.

Users can customize this process by defining a threshold for semantic similarity, which allows for the fine-tuning of the system's response time. This capability offers users a balance between efficiency and precision in addressing queries.

There are numerous benefits to this approach, not least of which are considerable savings in computational and financial resources. The method notably addresses the persistent speed issue with large language models. Furthermore, this strategy holds potential for almost any application that employs LLMs, broadening its applicability to a diverse range of sectors.

## References

- https://github.com/zilliztech/GPTCache
