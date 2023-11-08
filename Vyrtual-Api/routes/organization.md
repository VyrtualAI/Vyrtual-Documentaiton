# /routes/organization.go

The `organization.go` package in the organization folder contains API endpoints for managing `Organization` entities as part of the `api.vyrtual.ai` project.

📝 **Note:** The package focuses on operations such as listing, querying, creating, updating, and deleting organizations, along with handling organization invitations.

---

## ListOrganizations( ) 🚀

This endpoint lists organizations with support for pagination.

```go
func ListOrganizations(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Parses pagination parameters from the request.
Retrieves a paginated list of organizations.
Returns organizations along with metadata.

Request:

* Params (QueryString, required):
```typescript
{
  "page"?: number,
  "per_page"?: number
}
```

| Route               | Method |
| ------------------- | ------ |
| `/organization/list`| GET    |

Response:

```typescript
{
    "organizations": [Organization],
    "total_records": int64,
    "page": int,
    "per_page": int
}
```

## GetOrganization( ) 📚
This function retrieves details of a specific organization.

```go
func GetOrganization(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Extracts organization ID from the request.
Retrieves the specified organization.
Returns organization data.

Request:

* Params (QueryString, required):
```typescript
{
  "id"?: number
}
```
| Route               | Method |
| ------------------- | ------ |
| `/organization/{id}`| GET    |
|  `/organization`    | GET    | 

Response:

```typescript
{
    "organization": Organization
}
```

## PostOrganization( ) 🛠️
This endpoint creates a new organization.

```go
func PostOrganization(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Parses organization data from the request body.
Creates a new organization.
Returns the created organization data.

Request:
* Body (JSON, required):

```typescript
{
  // Organization data fields
}
```

| Route                 | Method |
| --------------------- | ------ |
| `/organization/create`| POST   |

Response:

```typescript
{
    "organization": Organization
}
```

## UpdateOrganization( ) 🔄
This function updates an existing organization's details.

```go
func UpdateOrganization(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Parses organization ID and update fields from the request.
Updates the organization.
Returns the updated organization data.

Request:
* Params (QueryString, required):

```typescript
{
  "organization_id": number
}
```

* Body (JSON, required):
```typescript
{
  // Update fields
}
```

| Route                 | Method |
| --------------------- | ------ |
| `/organization/update`|  PUT   |

Response:

```typescript
{
    "organization": Organization
}
```

## DeleteOrganization( ) ❌
This endpoint deletes an organization record.

```go
func DeleteOrganization(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Parses the organization ID from the request.
Deletes the specified organization.
Returns a confirmation message.

Request:
* Params (QueryString, required):

```typescript
{
  "id"?: number
}
```

| Route                 | Method |
| --------------------- | ------ |
| `/organization/delete`| DELETE |

Response:

```typescript
{}
```

## ListOrganizationInvitations( ) 📨
This endpoint lists invitations for a specific organization.

```go
func ListOrganizationInvitations(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Retrieves organization invitations based on query parameters.
Returns a list of organization invitations with pagination.

Request:
* Params (QueryString, required):
```typescript
{
  "page"?: number,
  "per_page"?: number,
  "id"?: number // organization id
}
```

| Route                      | Method |
| -------------------------- | ------ |
| `/organization/invitations`| GET    |

Response:

```typescript
{
    "organization_invitations": [OrganizationInvitation],
    "page": int,
    "per_page": int
}
```

## GetOrganizationInvitation( ) 💌
Retrieves a specific organization invitation.

```go
func GetOrganizationInvitation(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Extracts email and organization ID from the request.
Retrieves the specified organization invitation.
Returns the invitation data.

Request:
* Params (QueryString, required):
``` typescript
{
  "email"?: string,
  "organization_id"?: number
}
```

| Route                     | Method |
| ------------------------- | ------ |
| `/organization/invitation`| GET    |

Response:

```typescript
{
    "organization_invitation": OrganizationInvitation
}
```


## PostOrganizationInvitation( ) ✉️
Creates a new invitation for an organization.

```go
func PostOrganizationInvitation(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Parses invitation data from the request body.
Creates a new organization invitation.
Returns the created invitation data.

Request:
* Body (JSON, required):

```typescript
{
  "email": string,
  "organization_id": number
}
```

| Route                            | Method |
| -------------------------------- | ------ |
| `/organization/invitation/create`| POST   |

Response:

```typescript
{
    "organization_invitation": OrganizationInvitation
}
```

## UpdateOrganizationInvitation( ) 📝
Updates an existing organization invitation.

```go
func UpdateOrganizationInvitation(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Parses invitation data and updates fields from the request.
Updates the specified organization invitation.
Returns the updated invitation data.

Request:
* Params (QueryString, required):
```typescript
{
  "email": string,
  "organization_id": number
}
```
* Body (JSON, required):
```typescript
{
  // Update fields
}
```

| Route                            | Method |
| -------------------------------- | ------ |
| `/organization/invitation/update`|  PUT   |

Response:

```typescript
{
    "organization_invitation": OrganizationInvitation
}
```

## DeleteOrganizationInvitation( ) 🗑️
Deletes an organization invitation.

```go
func DeleteOrganizationInvitation(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Parses email and organization ID from the request.
Deletes the specified organization invitation.
Returns a confirmation message.

Request:
* Params (QueryString, required):

```typescript
{
  "email": string,
  "organization_id": number
}
```

| Route                           | Method |
| ------------------------------- | ------ |
| `/organization/inviation/delete`| DELETE |

Response:

```typescript
{}
```

## PostBatchOrganizationInvitations( ) 📦
Creates multiple invitations for an organization in a batch.

```go
func PostBatchOrganizationInvitations(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Parses a batch of invitations from the request body.
Creates multiple organization invitations.
Returns the created invitations.

Request:
* Body (JSON, required):

```typescript
{
  "invitations": [structs.OrganizationInvitation],
  "organization_id": number
}
```

| Route                            | Method |
| -------------------------------- | ------ |
| `/organization/inviations/create`| POST   |

Response:

```typescript
{
    "organization_invitations": [OrganizationInvitation]
}
```