# /routes/folder.go

The `folder.go` package within the folder folder contains API endpoints for managing `Folder` entities.

📝 **Note:** This package is part of the `api.vyrtual.ai` project and focuses on operations related to folders, such as listing, querying, creating, updating, and deleting folders.

The file offers the following functionalities:

1. Listing of folders
2. Querying a specific folder
3. Retrieving a specific folder
4. Creating a folder
5. Updating folder details
6. Deleting a folder

---

## ListFolders( ) 🚀

This endpoint lists folders, supporting pagination and organization-based access control.

```go
func ListFolders(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Parses pagination and organization parameters from the request.
Determines the offset and limit based on pagination.
Retrieves folders based on the user's access rights within the organization.
Returns the list of folders along with total records, page number, and items per page.

Request:

- Params (QueryString, required):

```typescript
{
  "page"?: number,
  "per_page"?: number,
  "organization_id"?: number
}
```

| Route          | Method |
| -------------- | ------ |
| `/folder/list` | GET    |

Response:

```typescript
{
    "folders": [Folder],
    "total_records": int,
    "page": int,
    "per_page": int
}
```

## QueryFolder( ) 📚

This function retrieves details of a specific folder based on path and organization.

```go
func QueryFolder(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Extracts folder path and organization ID from the request.
Retrieves the folder data based on the path, organization, and user access.
Returns the folder data.

Request:

Params (QueryString, required):

```typescript
{
  "path"?: string,
  "organization_id"?: number
}
```

| Route     | Method |
| --------- | ------ |
| `/folder` | GET    |

Response:

```typescript
{
    "folder": Folder
}
```

## GetFolder( ) 📘

This endpoint retrieves a specific folder by its path and organization.

```go
func GetFolder(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Parses folder path and organization ID from the request.
Retrieves the folder data based on path and user access.
Returns the folder data.

Request:

- Params (QueryString, required):

```typescript
{
  "organization_id"?: number,
  "path"?: string
}
```

| Route                    | Method |
| ------------------------ | ------ |
| `/fodler/{organization}` | GET    |

Response:

```typescript
{
    "folder": Folder
}
```

## PostFolder( ) 🛠️

This endpoint is used to create a new folder record.

```go
func PostFolder(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Parses folder data from the request body.
Validates user access and permissions.
Creates a new folder record with specified permissions and associations.
Returns the created folder data.

Request:

- Body (JSON, required): Contains the folder data including permissions and associations.

```typescript
{
  "name": string,
  "organizationID": number,
  "path": string,
  "viewableBy": [number],
  "editableBy": [number],
  "accessibleBy": [string],
  "modifiableBy": [string],
  "parentFolderID": number
}
```

| Route            | Method |
| ---------------- | ------ |
| `/folder/create` | POST   |

Response:

```typescript
{
    "folder": Folder
}
```

## UpdateFolder( ) 🔄

This function updates details of an existing folder.

```go
func UpdateFolder(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Parses folder ID and update fields from the request.
Validates user permissions for updating the folder.
Updates the specified folder record with new data.
Returns the updated folder data.

Request:

- Params (QueryString, required):

```typescript
{
  "folder_id": number,
  "organization_id": number
}
```

- Body (JSON, required): Contains the folder update data

```typescript
{
  "viewable_by_ids"?: [number],
  "editable_by_ids"?: [number],
  "accessible_by_groups"?: [string],
  "modifiable_by_groups"?: [string],
  "file_ids"?: [number],
  "folder_ids"?: [number],
  "parent_folder_id": number,
  "name": string,
  "path": string,
  "size": number
}
```

| Route            | Method |
| ---------------- | ------ |
| `/folder/update` | PUT    |

Response:

```typescript
{
    "folder": Folder
}
```

## DeleteFolder( ) ❌

This endpoint is used to delete a folder record.

```go
func DeleteFolder(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Parses the folder ID from the request.
Validates user permissions for deleting the folder.
Deletes the specified folder record.
Returns a confirmation message.

Request:

- Params (QueryString, required):

```typescript
{
  "id"?: number,
}
```

| Route            | Method |
| ---------------- | ------ |
| `/folder/delete` | DELETE |

Response:

```typescript
{
}
```
