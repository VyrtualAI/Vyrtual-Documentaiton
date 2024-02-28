# /routes/organization/profile.go

The `organization/profile.go` package in the organization folder contains API endpoints for managing `Organization Profiles` entities as part of the `api.vyrtual.ai` project.

📝 **Note:** The package focuses on operations such as listing, querying, creating, updating, and deleting organizations profiles.

---

## ListOrganizationProfiles( ) 🚀

This endpoint lists organizations with support for pagination.

```go
func ListOrganizationProfiles(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Parses pagination parameters from the request.
Retrieves a paginated list of organizations profiles.
Returns organization profiles along with metadata.

Request:

- Params (QueryString, required):

```typescript
{
  "page"?: number,
  "per_page"?: number
  "organization_id": number
}
```

| Route                        | Method |
| ---------------------------- | ------ |
| `/organization/profile/list` | GET    |

Response:

```typescript
{
    "organization_profiles": [OrganizationProfile],
    "total_records": int64,
    "page": int,
    "per_page": int
}
```

## GetOrganizationProfile( ) 📚

This function retrieves details of a specific organization.

```go
func GetOrganizationProfile(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Extracts organization ID and organization profile ID from the request.
Retrieves the specified organization profiles.
Returns the organization profile data.

Request:

- Params (QueryString, required):

```typescript
{
  "id"?: number
  "organization_profile_id"?: number
  "organization_id"?: number
}
```

| Route                | Method |
| -------------------- | ------ |
| `/organization/{id}` | GET    |
| `/organization`      | GET    |

Response:

```typescript
{
    "organization_profile": Organization_Profile
}
```

## UpdateOrganizationProfile( ) 🔄

This function updates an existing organization's details.

```go
func UpdateOrganization(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Parses organization ID, organization profile ID and update fields from the request.
Updates the organization profile.
Returns the updated organization profile data.

Request:

- Params (QueryString, required):

```typescript
{
  "organization_id": number
  "organization_profile_id": number
}
```

- Body (JSON, required):

```typescript
{
 "main_language_id": number;
 "ai_language_id": number;
 "position_name": string;
 "push_notifications_enabled" boolean;
 "assignee_notifications_enabled": boolean;
 "due_date_notifications_enabled": boolean;
 "message_notifications_enabled": boolean;
 "meeting_schedule_notifications_enabled": boolean;
}
```

| Route                  | Method |
| ---------------------- | ------ |
| `/organization/update` | PUT    |

Response:

```typescript
{
    "organization_profile": OrganizationProfile
}
```
