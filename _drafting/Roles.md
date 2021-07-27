---
tags: , 
---
Traditional client-server authentication model: resource owner provides credentials for client to access resource
- Store credentials on the third-party to reuse => stolen credentials risk
- Password authentication => weak
- Resource owner does not have ability to restrict accessible resource
- Could not revoke access for specific party
- Intermediary hold user credentials => lost protected info

OAuth2 was born to resolve above problem

OAuth 2.0 is the industry-standard protocol for authorization. OAuth 2.0 focuses on client developer simplicity while providing specific authorization flows for web applications, desktop applications, mobile phones, and living room devices.

- Resource owner: server, end user - an entity capable of granting access to a protected resource
- Resource server: the server hosting the protected resources
- Client:  the application making protected resource requests on behalf of the resource owner and with its authorization
- Authorization server: the server issuing access tokens to the client after successful authentication of the resource owner and obtaining authorization

Note: The authorization server may be the same server as the resource server or a separate entity. A single authorization server may issue access tokens accepted by multiple resource servers.

---

#### Citations