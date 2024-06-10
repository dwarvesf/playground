---
tags: null
title: Loki
date: null
description: null
authors: null
confidence: null
assign: quang
priority: null
status: Adopt
quadrant: Platforms
tag: DevOps
---

## Description
Loki is a horizontally scalable, highly available, multi-tenant log aggregation system inspired by Prometheus. Like Prometheus, it is a log and data driver to be used in Grafana.

## Output Goal
* Apply log system to all Kubernetes related projects
* Have the log system integrated with related pods and applications in their respective namespaces in the cluster
* Create common configurations for projects to organize logging

## Timeline
* (2022-01-15) - (Tom, Quang) Fix production disk issues related to [https://github.com/grafana/loki/issues/3219](https://github.com/grafana/loki/issues/3219)
* (2021-12-02) - (Tom, Quang) Add CRI pipeline stages for project LFW
* (2020-01-01) - **[Adopted]** (Tom) Added description and basic output.