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
title: "Labs Weekly Catchup #4"
date: 2023-12-28
description: Our fourth weekly catchup. We organize an agenda the day beforehand and consolidate our findings, notable research progress, possibly new tech, insight or technique everyone should know.
authors:
  - monotykamary
menu: labs
type: labs
hide_frontmatter: false
event_date: 2023-12-13
---

| Event Date                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | Discord Channel | Type     |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------- | -------- |
| 27/12/2023 | 🍎 apple   | Internal |

Our fourth weekly catchup. We organize an agenda the day beforehand and consolidate our findings, notable research progress, possibly new tech, insight or technique everyone should know.

### Agenda:
- Broadway in elixir to handle million messages by @Hieu
- Using WebAuthn API to implement passkeys by @Vincent
- Labeling image using openAI vision and embedding flow by @Lap

### Output:
- Understand the research progress and passions of the labs team
- Understand any shortcomings or things to improve for the next weekly catchup

---

## Notes from the catchup
weekly meeting #4 - 27/12/2023:

⚖️ **Using Broadway in Elixir to Handle millions of messages**
- Broadway is a concurrent, multi-stage tool for building data ingestion and data processing pipelines in Elixir.
- @Hieu mentions that we have a backlog issue for requests through NgheNhan's websocket, and to overcome this limit, we can introduce Broadway to help manage backpressure for requests.
	- ![[Labs Weekly Catchup 4-20231228142048893.webp]]
- @Hieu mentions that we can use it to manage process groups to manage pipelines such as for getting market prices.
	- ![[Labs Weekly Catchup 4-20231228141338220.webp]]
	- ![[Labs Weekly Catchup 4-20231228141412858.webp]]
- (@Hieu) Managing and scaling across multiple nodes will require a consensus algorithm such as Raft to handle configurations between nodes and message handling
	- ![[Labs Weekly Catchup 4-20231228142136373.webp]]

🔒 **Using WebAuthn API to Implement Passkeys**
- A joint effort between @Vincent and @An Tran
- (@Vincent) We can use a WebAuthn, a growing web standard, to help simplify authentication for users: https://webauthn.wtf/
- (@Vincent) Passkeys are generated on the machine and can be stored locally, or it can be stored in another device
	- ![[Labs Weekly Catchup 4-20231228142417393.webp]]
- (@Vincent) By default, there isn't an open external service to help store passkeys for the user, apart from third-party sources such as 1Password and iCloud
- (@Vincent) Implementing WebAuthn is as simple as the processes we use for authentication Metamask on Mochi UI

🏷️ Labeling image using GPT4 Vision and Embedding flows
- (@Lap) In one of our projects, iFramely to help us get the initial metadata and we then use GPT4 vision to help label images
- The labels are then used in generating embeddings for related text and the image itself, regenerate inputs for classification, and used to create a suggestion record with weights.
	- [Cohere](https://cohere.com/) is used to do text embeddings where as [openai/clip-vit-base-patch32](https://huggingface.co/openai/clip-vit-base-patch32) is used for image embeddings, both of which help store multi-dimensional vectors 
	- ![[Labs Weekly Catchup 4-20231228143002213.webp]]
- (@Thanh) There does seem to be a 3-4 round trip process before finally getting enough data to create suggestion scores for the user