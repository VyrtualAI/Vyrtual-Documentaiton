# /routes/ping.go

The `ping.go` package within the ping folder contains a simple API endpoint for the `api.vyrtual.ai` project. This endpoint is typically used for health checking and service availability verification.

---

## GetPing( ) 🏓

This endpoint provides a basic response to check the health and availability of the service.

```go
func GetPing(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Responds with a simple message to indicate the service is operational.

Request:

No parameters required.

| Route  | Method |
| ------ | ------ |
| `/ping`| GET    |

Response:

```typescript
"Pong"
```