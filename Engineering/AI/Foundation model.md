---
tags: engineering/ai, llm, foundation-model, fine-tuning
author: Pham Duc Thanh
github_id: zlatanpham
date: 2023-05-18
icy: 10
---

Foundation models are an emerging class of artificial intelligence (AI) models that have been gaining prominence recently. These models, initially coined by a team from Stanford, represent a paradigm shift in the field of AI. Unlike traditional AI models, which were trained on specific task-specific data to perform individual tasks, foundation models provide a foundational capability to drive a multitude of applications and use cases.

![[foundation-model.png]]

Foundation models are characterized by their ability to be transferred to any number of tasks, as they are trained on vast amounts of unstructured data in an unsupervised manner. This gives them the unique capability to perform various functions. In the case of language models, these are trained by feeding them numerous sentences, often terabytes of data, and teaching them to predict the next word in a sentence based on the preceding words. This generative capability of predicting and generating the next word from previous words categorizes foundation models as a part of the AI field known as generative AI.

While at their core, these models are trained for a generative task, they can be adapted to perform traditional Natural Language Processing (NLP) tasks, such as classification or named-entity recognition. This process, known as tuning, involves introducing a small amount of labeled data to update the parameters of the model for a specific NLP task. However, even in low-labeled data domains, these models perform well via a process called prompting or prompt engineering.

Foundation models have key advantages, the foremost being their performance. Having been trained on vast quantities of data, they can outperform models trained on only a few data points when applied to smaller tasks. Another advantage is the productivity gains they offer. Through prompting or tuning, these models require significantly less labeled data to create task-specific models than if starting from scratch.

However, foundation models do come with disadvantages. The first is their computing cost, making them expensive to train, especially for smaller enterprises. They can also be costly to run inference on, especially large models with billions of parameters, as they may require multiple GPUs. Additionally, the trustworthiness of these models can be a concern. Although they've seen a lot of unstructured data, this can come with risks, especially with language data scraped from the internet, which may contain bias, hate speech, or other toxic information. The exact datasets these models have been trained on are often unknown, further exacerbating trust issues.

Foundation models aren't limited to the language domain; they can be applied to other domains as well. Examples include vision models like DALL-E 2, which generates images from text data, and coding models like Copilot which assist with authoring code. Other applications extend to the fields of chemistry, such as molecule discovery, and climate research, with the use of geospatial data.

## References

- [What are Generative AI models](https://www.youtube.com/watch?v=hfIUstzHs9A)
