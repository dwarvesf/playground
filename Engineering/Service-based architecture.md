---
tags: engineering, architecture, diagram, service, domain
author: Nguyen Xuan Anh
github_id: monotykamary
date: 2022-06-21
---

## What is service-based architecture?

Service-based architecture is a kind of hybrid or middle-ground architecture between microservices and a monolith and is noted as a pragmatic architecture style due to its flexibility. Like a microservice architecture, it is essentially a distributed architecture, but it doesn't come with the cost of or complexity of other distributed architectures.

![[Pasted image 20220922153254.png]]

### What are the differences between microservices, service-oriented, and service-based architectures?

> Microservices Architecture and Service-Oriented Architecture (SOA) are considered service-based architectures

Mark Richards, one of the authors who helped coin the term in the book _Fundamentals of Software Architecture: An Engineering Approach_, notes that service-based architectures lie as a **superset** of microservice and service-oriented architectures. The most notable patterns shared between the architectures, service contracts and a reliance on the [[BASE model]] with regard to database transactions.

## Why use a service-based architecture?

It is quite arguably a one-size fits a lot of stuff architecture. It is very suitable for projects that contain business requirements a bit too complex to manage (or otherwise accrue technical debt) with a monolith. Likewise, it also doesn't require the level of loose coupling you would typically see in a strict microservice environment.

#### References

- Fundamentals of Software Architecture: An Engineering Approach—by Mark Richards, Neal Ford
- https://microservices.io/
- https://en.wikipedia.org/wiki/Microservices
- https://nofluffjuststuff.com/magazine/2015/10/the_challenges_of_service_based_architecture

---
<!-- CTA -->
### Contributing

At Dwarves, we encourage our people to read, write, share what we learn with others, and [contributing to the Brainery](./CONTRIBUTING.md) is an important part of our learning culture. For visitors, you are welcome to read them, contribute to them, and suggest additions. We maintain a monthly pool of $1500 to reward contributors who support our journey of lifelong growth in knowledge and network.

### Love what we are doing?

- Check out our [products](https://superbits.co)
- Hire us to [build your software](https://d.foundation)
- Join us, [we are also hiring](https://github.com/dwarvesf/WeAreHiring)
- Visit our [Discord Learning Site](https://discord.gg/dzNBpNTVEZ)
- Visit our [GitHub](https://github.com/dwarvesf)