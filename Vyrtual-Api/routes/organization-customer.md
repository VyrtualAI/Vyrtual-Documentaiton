# /routes/organization/customer.go

The `organization/customer.go` package in the organization folder contains API endpoints for managing a `Stripe Customer` as part of the `api.vyrtual.ai` project.

📝 **Note:** The package focuses on operations such as listing, querying, creating, updating, and deleting organizations customer information.

---

## ListOrganizationCustomer( ) 🚀

This endpoint lists an organization's customer information.

```go
func ListOrganizationCustomer(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Parses parameters from the request.
Retrieves customer data from stripe.
Returns customer data.

Request:

- Params (QueryString, required):

```typescript
{
  "organization_id": number
}
```

| Route                         | Method |
| ----------------------------- | ------ |
| `/organization/customer/list` | GET    |

Response:

```typescript
{
    "customer": stripe.Customer,
    "subscriptions": [stripe.Subscription],
}
```
