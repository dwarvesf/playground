---
tags: engineering, architecture, diagram
author: Nguyen Xuan Anh
github_id: monotykamary
date: 2022-04-17
---

# What are C4 diagrams?
C4 diagrams, or the [C4 model](https://c4model.com/), is used to diagram domain and implementation abstractions of system software architectures. These diagrams represent system architectures in a semantically consistent format that can stand by itself with little to no prior context as they always incorporate a name, description, with relevant contexts such as type of technology or its deployment location. The semantics used for C4 diagrams are coincidentally very similar to [[State, Explain, Link]]. It is focused as an "abstraction-first" approach to diagramming, with the hierarchy of abstractions of the model going down 4 levels:

1. **System Context diagram** - shows the context of the entire system with related entities
2. **Container diagram** - a high level shape of the architecture and how it fits the IT environment
3. **Component diagram** - decompose containers into components to show implementation abstractions
4. **Code** - shows how the component is implemented as programmable code

![c4-overview](_assets/c4-overview.png)

The C4 model isn't strictly static when it comes to these levels and also supports supplementary diagrams, such as **system landscape diagrams**, **dynamic diagrams**, **deployment diagrams**, etc.

# The story of C4 diagrams
The C4 model was created by Simon Brown, designed with the goal for it to be a developer friendly approach to diagramming. The high level representations of these diagrams incidentally also allowed it to assist in communication between software development teams and product teams. The abstractions make it suitable for software consulting and allows us to do architecture evaluations and risk identification.

#### Reference
- https://c4model.com/
- https://en.wikipedia.org/wiki/C4_model

---
<!-- cta -->

### Contributing
At Dwarves, we encourage our people to read, write, share what we learn with others, and [[CONTRIBUTING|contributing to the Brainery]] is an important part of our learning culture. For visitors, you are welcome to read them, contribute to them, and suggest additions. We maintain a monthly pool of $1500 to reward contributors who support our journey of lifelong growth in knowledge and network.

### Love what we are doing?
- Check out our [products](https://superbits.co)
- Hire us to [build your software](https://d.foundation)
- Join us, [we are also hiring](https://github.com/dwarvesf/WeAreHiring)
- Visit our [Discord Learning Site](https://discord.gg/dzNBpNTVEZ)
- Visit our [GitHub](https://github.com/dwarvesf)