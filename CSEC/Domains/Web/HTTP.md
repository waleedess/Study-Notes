# HTTP Request Methods
---

1. `GET`
2. `POST`
3. `PUT` => Stores submitted data by adding or replacing current under a requested URL, if successful a new URL should be created.
4. `HEAD` => Same as `GET` but only requests the headers and ignores the body
5. `PATCH` => Used to partially update resources with submitted data. Possible only if the HTTP response's headers includes `Accept: PATCH`
6. `OPTIONS` => Used to identify all the request methods allowed for the web server as it responses with the allowed ones
7. `TRACE` => Primarily used for debugging input sent from client to server as it asks the server to echo the original client request 
8. `CONNECT` => Initiate a two-way network connection creating a proxy tunnel between client's web browser and the web server
9. `DELETE` => Removes given resource
   
   