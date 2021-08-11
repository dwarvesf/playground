---
tags: 
---
**What**
- serverless computation .eg "lambda function"
- create & deploy directly on Cloudflare
- arguably the most accessible serverless platform

**Why**
- No cold start 🚀
- Cheap & fast 💸 100k free reqs, reset daily
- Aim to get you started & deploy quickly (https://workers.new/)
    - 10-lines-of-code examples: https://developers.cloudflare.com/workers/examples
- Perfect deploy platform for SSR apps
    - (I also created an http proxy for Setel internal api, try https://lts.huygn.dev/api/deals/catalogues/deals, pls don't bomb it)

**Simple yet smartly made api** 🎯
- CF worker api is implemented after the standard Service Worker api, hence the name "Worker"
- Request routing made easy, just inspect incoming `request` url/method/.etc like you normally did on browser
    - for AWS you'll have to mess with Route53 to get the right behavior (and eventually got slapped with CORS issues) <:khoc:819507964427501568> 
- **Service Worker** is a web standard created specifically for intercepting request/response, and has been around for some times
- By implementing CF Worker after Service Worker api, Cloudflare made it familiar for JS web devs to easily get used to the api, why avoiding re-invent yet another serverless api like AWS Lambda or Google Cloud functions .etc

**Batteries included**
- built-in fast KV store with async api
    - in contrast AWS/Google/Azure require you to use their platform services .eg RDS, SQS bla bla with their own setup ceremonies to complex your setup (& decrease your wallet balance <:stonks:774369557531459664> )
- ScheduledEvent, WebSocket, Stream, HTML rewriter, rate limit
- Durable Objects: a transactional, key-value storage API

**Loved by community**
- https://github.com/lukeed/worktop: fully typed framework for CF worker
- https://github.com/mrbbot/miniflare: fast local env for CF worker
- https://flareact.com/: Next.js but built for CF worker deployment
- https://github.com/frandiox/vitedge (which I contributed <:pepebrain:843794594876751903> ): Vite app on CF worker

---

#### Citations