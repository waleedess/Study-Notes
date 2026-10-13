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
2. Collection as `/api/profiles/users/`
3. Subcollection as `/api/users/{user_id}/settings`