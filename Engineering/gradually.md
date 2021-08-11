---
tags: pattern, cloud
---
- We have a big old, obsolete running system, we want to replace it with new architecture, new tech stack. E.g: monolith => Micro service
 - We don't have enough effort to replacing a whole new system at once, and that's also risky. We need a gradually migration.

 - Incrementally replace specific pieces of functionality with new applications and services

 - At some point, when the migration is complete, the strangler fig façade will either go away or evolve into an adaptor for legacy clients.
 - Make sure the façade doesn't become a single point of failure or a performance bottleneck

 - When requests to the back-end system cannot be intercepted.
 - Smaller systems where the complexity of wholesale replacement is low.

 - https://docs.microsoft.com/en-us/azure/architecture/patterns/strangler-fig
 - https://dzone.com/articles/monolith-to-microservices-using-the-strangler-patt
 - https://martinfowler.com/bliki/StranglerFigApplication.html

---

#### Citations