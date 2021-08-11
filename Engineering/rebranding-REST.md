---
tag: API. REST
---

### The demand of API
- too many devices that try to access the app (laptop, desktop, native mobile)
- demand for dataset increases
- microservices' interoperability: an app can be run in many programming language to support multiple platforms
	-> everything must be in sync > they msut understand each other -> Agree on communication protocol and API
	
### It comes with standard
- many layers 
	- application (for user)
	- application layer standards (xml. http, https)
	- transport layer 

and standards are hard to set due to the creative space (website layout, UI)


### Benefit of APIs
- APIs allows browsers to speak multiple request to servers > fetch back data without reloading 
- The contract between FE/BE: transfer state
- REST: architectural proposal of how to use HTTP components (URL, header & body).

### The current issue w REST APIs
- large URL: too many parameters
- complex objects URLs: chunky URLs
- resource identifiers explosion?
- number of devices and experiences increase, the flow between those devices starts diverting. > difference experience between each platforms -> different APIs approach

-> Multiple APIs should be adopted
-> Throw out the reusability

#### Citation
- https://medium.com/hackinghabits/rest-api-guidelines-are-insufficient-we-need-something-better-f56d91d195f2
- [distinguish URI and URL](https://danielmiessler.com/study/difference-between-uri-url/)
- [rebranding REST](https://kieranpotts.com/rebranding-rest/): REST is specifically made for distributed system (for multipe devices). Web-service APIs are documented as REST APIs, not RESTful > The reason for rebranding REST is to differentiate it with RESTful APIs. 