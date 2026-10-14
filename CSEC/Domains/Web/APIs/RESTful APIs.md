# What are RESTful APIs
---
> REST (Representational State Transfer) is an architectural style for designing web APIs. It isn’t a protocol or a standard. Most REST APIs run over HTTP using methods (`GET`, `POST`, `PUT` & `DELETE`) to accomplish CRUD (Create, Read, Update & DELETE), REST APIs follow:

1. **Uniform Interface => Standardized:** All resources are accessed the same way. Clients work with representations, usually JSON, and messages are self-descriptive (they include the method and content type).
	- **HATEOAS** (Hypermedia as the Engine of Application State): Responses include links to related actions, so clients can navigate the API without hardcoding URLs.
2. **Client-Server** 
3. **Stateless => Scalable:** Each request contains everything the server needs to process it. The server doesn’t store session context between requests
4. **Cacheable => High Performance:** Responses must declare whether they can be cached, so clients and intermediaries can reuse them and reduce load
5. **Layered System:** The client can’t tell whether it’s talking directly to the server or to something in between, such as a load balancer, gateway, or cache. This is why an API gateway can sit in front of services
6. **Code on demand (optional):** The server can send executable code, such as JavaScript, to the client. This is the only optional constraint

# RESTful APIs Headers
---

1. **Authorization:** Carries credentials so the server can identify the client
   => Format: `<type> <token/credentials>`
2. **Content & Accept:** Tells the server the format of the request body & which response format the client wants respectively
   => Such as `application/(json, XML, x-www-form-urlencoded)`
3. **Middleware (x):** Custom headers added or read by proxies, load balancers, and gateways as requests pass through
   => Format: `x-<anything>`, such as:
   `X-Response-Time` -> How long a response took to process
   `X-Powered-By` -> Additional info about backend services like the framework or technology serving the request
   `X-Rate-Limit`
   `X-RateLimit-Remaining` 
   
   `X-API-Key` -> A custom header that carries an API key for authentication. It isn’t the standard `Authorization` header, but it serves the same purpose
   `X-Forwarded-For` -> Lists Clients IP & Proxies request went through
   `X-Forwarded-Proto` -> Shows whether the client used `HTTP/S` before a proxy handled it


# Other Characteristics
---
- RESTful APIs can have methods beyond CRUD, have their own authentication and authorization, use subdomains instead of paths for endpoints, have different rate limits, etc.
- ==The amount of information sent back to the client is determined entirely by how the API provider programmed it==