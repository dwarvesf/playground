---
tags: ci, cd
---

### CI
- avoid merge conflicts
- auto merge source code from different locals
- constantly build & test
- notify when bug arrives
- only merge if `no errors`

### CD
- after code is compiled & merge
- code is moved to another env for more test
- passed these tests, code is ready for production
- CD ensures a safety net for production code
	- i.e: once code is shipped to production, it can still be tested and notify bugs

### The CI/CD pipeline
- automatic // infinite loop of testing, notifying and building
- saves times. prevents developers to deal with merge conflicts and bugs
- provides constant feedback
- the pipeline keeps traverse between production // source code for bug tracking

**Source**
- https://kylefarmer85.medium.com/what-is-ci-cd-76d71b82898d