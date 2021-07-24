---
tags: 
---
To resolve this problem we have "The Proof Key for Code Exchange (PKCE, pronounced pixie) extension describes a technique for public clients to mitigate the threat of having the authorization code intercepted. The technique involves the client first creating a secret, and then using that secret again when exchanging the authorization code for an access token. This way if the code is intercepted, it will not be useful since the token request relies on the initial secret" - rfc7636

In March 2019, the OAuth 2.0 Security Best Current Practice deprecated the Implicit flow in favor of the Authorization Code flow with PKCE (Proof Key for Code Exchange).

**Why are Refresh Tokens considered insecure for an SPA?**

The refresh tokens are not used in SPAs, because in order to use it - and to get a new access token from the /token, the SPA needs to have a client secret, which cannot be stored securely in a browser. But since the OAuth 2.0 for Native Apps RFC recommends not requiring a client secret for the /token endpoint (for public clients), the refresh tokens could be used even in SPAs.

How to resolve or decrease this problem?
- Refresh Token Rotation + BFF
- Silent authentication

---

#### Citations