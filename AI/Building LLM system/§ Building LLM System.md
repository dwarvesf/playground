---
tags:
  - moc
  - llm
title: '§ Building LLM System'
description: 'This Map of Content (MoC) outlines the critical components required to design and build a large language model (LLM) system, focusing on architecture, model customization, safeguarding, performance evaluation, and more.'
date: 2024-09-11
authors:
  - thanh
---

In recent years, the emergence of Large Language Models (LLMs) has revolutionized AI applications, providing new opportunities for solving complex problems with natural language understanding and generation. This map of content explores the foundational aspects of building robust LLM-based systems, ranging from model selection and context enhancement to safeguarding mechanisms and performance evaluation.

## Overview

The rise of AI applications, especially LLMs, has unlocked diverse use cases across industries like customer support, content generation, and programming assistance. Building a scalable LLM system requires not only choosing the right model but also following architecture best practices and integrating a robust tech stack.

- [The rise of AI applications with LLM](the-rise-of-AI-applications-with-LLM.md)
- [Use cases](use-cases-for-LLM-applications.md)
- Architecture and stack

## Model Select and Customization

Selecting and customizing the right LLM is critical for addressing specific business needs, balancing between performance and cost.

- Choose the right model
- Fine-tuning
- Prompt engineering

## Context Enhancement

Methods for augmenting query context to improve model performance and accuracy.

- Retrieval-Augmented Generation (RAG)
- [RAG for multimodal data](multimodal-in-rag.md)
- Agentic RAG
- Query rewriting

## Management Output Structure

Standardizing and managing the output of an LLM system ensures that responses are structured and actionable.

- Output formatting
- Schema enforcement
- Chaining model outputs

## Safeguarding

Systems to prevent model misuse, sensitive data leaks, and bad outputs.

- Input Guardrails
- Output Guardrails
- Guardrail Tradeoffs

## Model Routing and Gateway

Managing multiple models and securing access to them through a unified system.

- [Intent Classifiers](intent-classification-by-llm.md)
- Model Gateways
- Next-Action Prediction

## Caching for Latency Optimization

Using caching techniques to reduce latency and costs in generative AI applications.

- Prompt Cache
- Exact Cache
- Semantic Cache

## Complex Logic and Write Actions

LLM systems need to handle complex reasoning, task delegation, and actions based on AI output.

- Conditional logic and task iteration
- Write Actions
- [Prevent Prompt Injection](prevent-prompt-injection.md)
- [Supervior-Worker architecture ( Divide and Conquer)](multi-agent-collaboration-for-task-completion.md)
- [ReAct](react-in-llm.md)
- [ReWOO (Reasoning without Observations)](rewoo-in-llm.md)

## Evaluating Performance

Using right metrics and method for specific use case in LLM.

- [Evaluation Metrics](evaluation-guideline-for-LLM-application.md)
- [AI-as-a-Judge](llm-as-a-judge.md)

## Observability and Orchestration

Monitoring the system's performance and orchestrating the complex AI workflows that tie the components together.

- [Observability in AI Platforms](observability-in-AI-platforms.md)
- AI Pipeline Orchestration
