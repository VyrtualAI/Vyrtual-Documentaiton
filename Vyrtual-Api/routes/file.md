# /routes/file.go

The `file.go` package within the file folder contains API endpoints for managing `File` entities.

📝 **Note:** This package is a part of the `api.vyrtual.ai` project and is focused on operations related to files, such as listing, retrieving, creating, updating, and deleting files.

The file offers the following functionalities:

1. Listing of files
2. Retrieval of a specific file
3. Creation of a file
4. Updating file details
5. Deletion of a file
6. Querying files

---

## ListFiles( ) 🚀

This endpoint lists files, supporting pagination and user-based access control.

```go
func ListFiles(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Parses pagination parameters (page, per_page) from the request.
Determines the offset and limit based on pagination.
Retrieves files based on the user's organizations and access rights.
Returns the list of files along with total records, page number, and items per page.

Request:

- Params (QueryString, required):

```typescript
{
  "page"?: number,
  "per_page"?: number
  "organization_id": number
  "file_ids"?: [number]
}
```

| Route        | Method |
| ------------ | ------ |
| `/file/list` | GET    |

Response:

```typescript
{
    "files": [File],
    "total_records": int,
    "page": int,
    "per_page": int
}
```

## QueryFile( ) 📚

This function retrieves details of a specific file based on path and organization.

```go
func QueryFile(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Extracts file path and organization ID from the request.
Retrieves the file data based on the path, organization, and user access.
Returns the file data.
Request:

- Params (QueryString, required):

```typescript
{
  "path": string,
  "organization_id": number
}
```

| Route   | Method |
| ------- | ------ |
| `/file` | GET    |

Response:

```typescript
{
    "file": File
}
```

## GetFile( ) 📘

This endpoint retrieves a specific file by its ID and organization.

```go
func GetFile(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Parses file ID and organization ID from the request.
Retrieves the file data based on ID and user access.
Returns the file data.

Request:

- Params (QueryString, required):

```typescript
{
  "id"?: number,
  "organization"?: number
}
```

| Route        | Method |
| ------------ | ------ |
| `/fire/{id}` | GET    |

Response:

```typescript
{
    "file": File
}
```

## PostFile( ) 🛠️

This endpoint is used to create a new file record.

```go
func PostFile(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Parses file data from the request body.
Validates user access and folder permissions.
Creates a new file record with specified permissions and associations.
Returns the created file data.

Request:

- Body (JSON, required): Contains the file data including permissions and associations.

```typescript
{
  "name": string,
  "thumbnail": string,
  "organizationID": number,
  "viewableBy": [number],
  "editableBy": [number],
  "accessibleBy": [string],
  "parentFolderID": number,
  "size": number,
  "path": string
}
```

| Route          | Method |
| -------------- | ------ |
| `/file/create` | POST   |

Response:

```typescript
{
    "file": File
}
```

## UpdateFile( ) 🔄

This function updates details of an existing file.

```go
func UpdateFile(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Parses file ID and update fields from the request.
Validates user permissions for updating the file.
Updates the specified file record with new data.
Returns the updated file data.

Request:

- Params (QueryString, required):

```typescript
{
  "id": number,
}
```

- Body (JSON, required): Contains the file update data

```typescript
{
  "name": string,
  "path": string,
  "thumbnail"?: string,
  "parent_folder_id"?: number,
  "size"?: number,
  "viewableBy"?: [number],
  "editableBy"?: [number],
  "accessibleBy"?: [string],
  "modifiableBy"?: [string],
}
```

| Route          | Method |
| -------------- | ------ |
| `/file/update` | PUT    |

Response:

```typescript
{
    "file": File
}
```

## DeleteFile( ) ❌

This endpoint is used to delete a file record.

```go
func DeleteFile(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Parses the file ID from the request.
Validates user permissions for deleting the file.
Deletes the specified file record.
Returns a confirmation message.

Request:

- Params (QueryString, required):

```typescript
{
  "id"?: number,
}
```

| Route          | Method |
| -------------- | ------ |
| `/file/delete` | DELETE |

Response:

```typescript
{
}
```
