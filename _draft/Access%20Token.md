---
tags: 
---
- Credentials to access protected resource
- Opaque to the client
- Tokens represent specific scopes and durations of access
- Abstraction layer => replacing different authorization constructs (e.g., username and password) => more restrictive than authorization code => resource server does not need to understand a wide range of authentication methods.
- Access tokens can have different formats, structures, and methods of utilization (e.g., cryptographic properties)
- ttl is usually short, take advantage of refresh token => decrease ability to take by bad guy

**Refresh Token**

- Refresh tokens are credentials used to obtain access tokens when
  - Access token becomes invalid or expires
  - Obtain additional access tokens with identical or narrower scope
- Issued to the client by the authorization server
- Refresh tokens are intended for use only with authorization servers and are never sent to resource servers

---

#### Citations