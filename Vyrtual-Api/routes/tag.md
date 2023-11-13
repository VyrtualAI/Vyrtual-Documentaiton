# /routes/tag.go

The `tag.go` package within the `pkg/tag` directory contains API endpoints for managing tags related to an organization.

📝 **Note:** This package is part of the `api.vyrtual.ai` project and is focused on handling tag-related operations, such as listing, retrieving, creating, updating, and deleting tags.

The file provides the following features:

1. Listing of tags for an organization
2. Retrieval of a specific tag
3. Creation of a new tag
4. Updating tag details
5. Deletion of a tag

---

## ListTags( ) 🚀

This endpoint lists tags associated with an organization, supporting pagination.

```go
func ListTags(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Parses pagination parameters (page, per_page) from the request
Determines the organization's membership and user privileges
Fetches tags based on the specified organization
Returns the list of tags along with total records, page number, and items per page

Request:
Params (QueryString, required):

```typescript
{
  "organization_id": number,
  "page"?: number,
  "per_page"?: number,
}
```

| Route       | Method |
| ----------- | ------ |
| `/tag/list` | GET    |

Response:

```typescript
{
    "tags": [Tag],
    "total_records": int,
    "page": int,
    "per_page": int
}
```

## GetTag( ) 📚

This function retrieves details of a specific tag associated with an organization.

```go
func GetTag(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Parses organization ID and tag identifier (id or name) from the request
Checks the user's membership and privileges within the organization
Retrieves the details of the specified tag
Returns the tag data

Request:

Params (QueryString, required):

```typescript
{
  "organization_id": number,
  "id"?: number,
  "name"?: string
}
```

| Route       | Method |
| ----------- | ------ |
| `/tag/{id}` | GET    |
| `/tag`      | GET    |

Response:

```typescript
{
    "tag": Tag
}
```

## PostTag( ) 🛠️

This endpoint is used to create a new tag for an organization.

```go
func PostTag(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Parses tag data from the request body
Checks the user's membership and privileges within the organization
Creates a new tag record for the organization
Returns the created tag data

Request:

Body (JSON, required): Contains the tag data, including the tag's name.

```typescript
{
    "name": string
}
```

| Route         | Method |
| ------------- | ------ |
| `/tag/create` | POST   |

Response:

```typescript
{
    "tag": Tag
}
```

## UpdateTag( ) 🔄

This function updates details of an existing tag associated with an organization.

```go
func UpdateTag(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Parses tag ID and update fields from the request
Retrieves the tag based on the provided tag ID
Checks the user's membership and privileges within the organization
Updates the specified tag record
Returns the updated tag data

Request:

Params (QueryString, required):

```typescript
{
  "tag_id": number,
}
```

Body (JSON, required): Contains the tag update data.

```typescript
{
  "name"?: string
}
```

| Route         | Method |
| ------------- | ------ |
| `/tag/update` | PUT    |

Response:

```typescript
{
    "tag": Tag
}
```

## DeleteTag( ) ❌

This endpoint is used to delete a tag associated with an organization.

```go
func DeleteTag(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Parses the tag ID from the request
Checks the user's membership and privileges within the organization
Deletes the specified tag record
Returns a confirmation message

Request:

Params (QueryString, required):

```typescript
{
  "tag_id"?: number,
}
```

| Route         | Method |
| ------------- | ------ |
| `/tag/delete` | DELETE |

Response:

```typescript
{
}
```
