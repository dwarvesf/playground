---
tags: engineering, architecture, code-generating, quality
author: An Tran
github_id: tienan92it
date: 2023-12-22
---

### Motivation

In traditional software development, defining models and API clients is a fundamental step when using strongly-typed languages.
- **Models**: represent various data structures such as objects, request parameters, and response types.
- **API client**: acts as an intermediary, handling requests to the backend and binding the data to the models.

Syncing these elements between the backend and frontend is important in the software development process.However, this synchronization is often manual and error-prone, leading to inconsistencies that can cause runtime failures and bugs. 
To address this challenge, typesafe client-server architecture introduces a code generation layer that bridges the gap between frontend and backend more effectively.
Using API definitions in JSON or YAML format as the single source of truth, the code generator automatically validates and generates the necessary models and API clients for the frontend and corresponding models and API endpoints for the backend. This ensures that both ends of the application speak the same "data language," and any changes in the API are reflected on both sides promptly and accurately.

![[typesafe-client-server.png]]

This automated approach not only minimizes human error but also streamlines the development process, as developers can now focus on building features rather than fixing mismatches between the FE and BE. By adopting this typesafe client-server system, teams can enhance collaboration, accelerate time-to-market, and deliver a more reliable product.
### Benefits
- Enhanced Reliability
- Early Error Detection
- Improved Developer Productivity
- Security Enhancements
- Documentation and Collaboration
- Refactoring and Scalability
### How to use effectively
- **API First Development**: Begin with designing API definitions.
- **Automate Code Generation**: Set up automation tools to generate code whenever the API definitions change. This keeps the frontend and backend in sync.
- **Continuous Integration**: As part of CI/CD pipeline, validate the API definitions and ensure that auto-generated code doesn't have manual edits.
- **Testing**: Ensure that both frontend and backend have thorough unit and integration tests. Because we're using Swagger, we can also use tools to automatically generate and run tests based on the API definitions.
- **Documentation**: Use Swagger UI or ReDoc to provide interactive API documentation. This not only helps developers but also non-tech stakeholders to understand and try out the API.
- **Version Control**: As your API evolves, make sure to version it.

### Supported frameworks/tools

[openapi-generator](https://openapi-generator.tech/): Official tool to validate Swagger spec and generate clients. Using Axios for client requests.
[Orval](https://next.orval.dev/): Generate code in various clients (axios, swr, react-query…). Support mock data with [msw](https://mswjs.io/) and [faker](https://fakerjs.dev/)

### References
- https://openapi-generator.tech
- https://orval.dev
- https://docs.stoplight.io/docs/spectral/eb68e7afd463e-spectral-in-java-script
- https://swagger.io/specification
- https://trpc.io