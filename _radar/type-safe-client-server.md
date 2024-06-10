---
tags: null
title: Type Safe Client Server
date: null
description: null
authors: null
confidence: High
assign: An Tran
priority: 🎯FOCUS
status: Trial
quadrant: Techniques
tag: Frontend
---

<!-- table_of_contents 59f48ef1-694b-475b-8b4c-ac039e75e23f -->

### Description
Developers working on Javascript Applications often face the challenge of enforcing type safety between the client and server. One effective solution is to automatically generate an OpenAPI Spec file from server code. This can then be used with the OpenAPI generator to produce a client-side library for making typesafe API calls to the backend. Our existing workflow has adopted the typesafe approach using Swagger for API documentation. We aim to upgrade this approach by automating the generation of API methods.

<!-- child_database 54105ad3-6180-4286-b4d0-03be4f054db6 -->
