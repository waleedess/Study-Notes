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

1. **Authorization:** `<type> <token/credentials>`
2. **Content:** 


# Other Characteristics
---
- RESTful APIs can have methods beyond CRUD, have their own authentication and authorization, use subdomains instead of paths for endpoints, have different rate limits, etc.
- ==The amount of information sent back to the client is determined entirely by how the API provider programmed it==