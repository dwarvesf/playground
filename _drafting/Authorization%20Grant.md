---
tags: 
---
Have 4 types

- Authorization code
  - Using an authorization server as intermediary between client and resource owner
  - Authorization code is a temporary code that the client will exchange for an access token
  - Authorization server authenticates the resource owner and obtains authorization
  - client call to autho server => redirect to resource owner and verified owner with autho server => send autho code to client => exchange code + client secret to autho server => access token
  - Resource owner's credentials are never shared with the client.
  - Server to server communication.

- Implicit
  - Simplified authorization code flow
  - Instead of issuing the client an authorization code, the client is issued an access token directly
- Resource owner password credentials
  - User resource owner username and password directly
- Client credentials
  - Each client has it own identifier and password.
  - The authorization server MUST support the HTTP Basic authentication scheme for authenticating clients that were issued a client password.
  - Or including the client credentials in the request-body using the following parameters: client_id and client_secret (NOT RECOMMENDED and SHOULD be limited)

---

#### Citations