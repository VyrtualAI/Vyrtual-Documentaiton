# /routes/organization/management.go

The `organization/management.go` package in the organization folder contains API endpoints for managing an organization's `Management Profile` as part of the `api.vyrtual.ai` project.

📝 **Note:** The package focuses on operations such as listing, querying, creating, updating, and deleting organization's management profile information.

---

## ListOrganizationManagementProfiles( ) 🚀

This endpoint organization management profiles.

```go
func ListOrganizationManagementProfiles(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Checks whether a user is a valid member of
Vyrtual and returns organization's management
profiles

Request:

| Route                                   | Method |
| --------------------------------------- | ------ |
| `/organization/management/profile/list` | GET    |

Response:

```typescript
{
    "organization_management_profiles": [OrganizationManagementProfile],
    "total_records": int,
    "page": int,
    "per_page": int
}
```

## UpdateOrganizationManagementProfile( ) 🔄

This function updates an existing organization's details.

```go
func UpdateOrganizationManagementProfile(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Parses organization ID and update fields from the request.
Updates the organization management profile.
Returns the updated organization profile data.

Request:

- Params (QueryString, required):

```typescript
{
  "organization_id": number
}
```

- Body (JSON, required):

```typescript
{
 "managers"?: {
    "user_id": number,
    "delete"?: boolean
 }[]
}
```

| Route                                     | Method |
| ----------------------------------------- | ------ |
| `/organization/management/profile/update` | PUT    |

Response:

```typescript
{
    "organization_management_profile": OrganizationManagementProfile,
}
```
