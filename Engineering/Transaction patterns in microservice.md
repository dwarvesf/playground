---
tags: microservice, pattern
---

### Two-phase commit pattern
- global transaction context
- prepare phrase, lock resources -> commit phase
- abort if error

**Pros**
- atomic transaction, read-write isolation

**Cons**
- synchronous, delay during calling services, blocking resources -> bottleneck, deadlock

**Q&A**  
how do we handling errors during commit phrase -> retry on commit error?!, global transaction context tracking and calling delete all committed objects?!

### Saga pattern
- local transaction, communicate through event bus
- send rollback event to rollback changes (compensation transaction)

**Pros**
- asynchronous, local transaction so there is no lock on any object/row

**Cons**
- difficult to bug and maintain event messages as system grows
- no read isolation: committed data of a service might be gone after a second due to compensation transaction

---

**Citation**
https://developers.redhat.com/blog/2018/10/01/patterns-for-distributed-transactions-within-a-microservices-architecture
