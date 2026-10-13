Web APIs use:
1. `POST`
2. `GET`
3. `PUT`
4. `DELETE`

# API Endpoints
---

> An endpoint is the specific URL a request is sent to. It points at one resource on the server, and the method tells the server what to do with it

**Endpoint Examples**:
1. Path: `/api/v3/users`
2. Path: `/api/v3/users?updated_on=`
3. Path: `/api/state/1`
4. URL: `https://api.example.com/users/{user_id}`

# API Resource Types
---

1. Singleton as `/api/users/{user_id}`
2. Collection as `/api/users/`
3. Subcollection as `/api/users/{user_id}/settings` 

# API Gateway

> An API gateway is a single entry point that sits in front of one or more backend services. Clients send all requests to the gateway, and it forwards each one to the right service.
> Client → Gateway → Service (web server e.g. users service) → endpoint handler (code function for one method and path e.g. `GET /api/users/{user_id}`) 

Handles these tasks:
1. **Microservice Routing**: Sends `/api/users/...` to the users service and `/api/orders/...` to the orders service 
2. **Request Filtering, Logging and Monitoring:** blocks and records requests as they pass through
3. **Authentication:** Checks tokens or keys before a request reaches a backend
4. **Rate Limiting** 
5. **SSL/TLS Encryption for transit**
6. **Load Balancing**
   
###### Microservice

> Modular piece of a web application that handles a specific function or set of functions and uses APIs to transfer data & trigger actions