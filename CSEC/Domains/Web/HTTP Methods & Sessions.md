# HTTP Request Methods
---

1. `GET` => Requests a resource from the server without changing it
2. `POST` => Submits data to the server, usually to create a new resource or trigger processing
3. `PUT` => Stores submitted data at the requested URL, replacing the current resource or creating it if it doesn’t exist. Replacing returns a success status such as `200` or `204`, and creating returns `201`
4. `HEAD` => Same as `GET` but only requests the headers and ignores the body
5. `PATCH` => Partially updates a resource with submitted data. The server must support it. Servers advertise the patch formats they accept with the `Accept-Patch` response header
6. `OPTIONS` => Asks the server which request methods it allows for a resource. The response lists them, usually in the `Allow` header
7. `TRACE` => Primarily used for debugging. The server echoes back the request it received. Many servers disable it because it can be abused 
8. `CONNECT` => Opens a two-way tunnel between the client and the server, typically through a proxy, commonly used for HTTPS
9. `DELETE` => Removes the resource at the given URL
   
#### Idempotent & Non-idempotent

> Idempotent means that sending the same request several times leaves the server in the same state as sending it once

| Idempotent                                                                                                                                                                                                                  | Non-idempotent                                      |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------- |
| `GET`, `HEAD`, `PUT`, `DELETE`, `OPTIONS`, `TRACE`                                                                                                                                                                          | `POST`, `PATCH`, `CONNECT`                          |
| -> 10 `PUT` requests submitted => 10 overwrites on the same resource<br>-> 2 `DELETE` requests submitted => 1st: returns `200` and deletes the resource, 2nd: returns `404`, but the resource is still deleted ⇒ Idempotent | -> 10 `POST` requests submitted => 10 new resources |


# Stateless & Stateful HTTP
---

| Stateful                                                                                                                                                                                | Statless                                                                                             |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| Server keeps track of clients action, profile, images, preferences & etc. to remember about the HTTP session created between client's web browser and a specific web server             | Server does not keep track of information between the requests                                       |
| Uses small text files `COOKIES` that are stored client side including site, security preferences, authentication information, etc.<br>Servers also save some in a cache or in databases | Eliminates the need for server resources to manage sessions                                          |
| Client sends a session ID (usually in a cookie) with each request so the server can find its stored data.                                                                               | Each request must contain all the authorization information, such as a key or header                 |
| Harder to scale: sessions live on the server or in a shared store, so requests may need to reach the same server                                                                        | Easy to scale: any server can handle a request, because no session is stored on one specific server. |
| **Authentication Examples:** login session cookie                                                                                                                                       | **Authentication Examples:** JWT sent in the Authorization header                                    |
