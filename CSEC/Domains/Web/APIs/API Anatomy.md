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

> A small, independently deployed service that handles one specific function (e.g., users or orders). Microservices communicate with each other through APIs to transfer data and trigger actions. Each service can be updated, scaled, or restarted without affecting the others.

> Clients usually don’t call microservices directly. An API gateway routes each request to the right service, for example `/api/users/` to the users service and `/api/orders/` to the orders service.

**Example**: Web app with payment page can do the job either way

| Several Different Microservices                                             | Monolith                       |
| --------------------------------------------------------------------------- | ------------------------------ |
| One function for each of billing, logging user info, sending email receipts | One function does all of these |
- **Monolith**: a single application where all functions live in one codebase and deploy together.
