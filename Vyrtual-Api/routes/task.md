# /routes/task.go

The `task.go` package within the `pkg/task` directory contains API endpoints for managing tasks related to an organization.

📝 **Note:** This package is part of the `api.vyrtual.ai` project and focuses on handling task-related operations, including listing, retrieving, creating, updating, and deleting tasks.

The file provides the following features:

1. Listing of tasks for an organization
2. Retrieval of a specific task
3. Creation of a new task
4. Updating task details
5. Deletion of a task

---

## ListTasks( ) 🚀

This endpoint lists tasks associated with an organization, supporting pagination.

```go
func ListTasks(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Parses pagination parameters (page, per_page) from the request
Determines the organization's membership and user privileges
Fetches tasks based on the specified organization
Returns the list of tasks along with total records, page number, and items per page

Request:

Params (QueryString, required):

```typescript
{
  "organization_id": number,
  "page"?: number,
  "per_page"?: number,
}
```

| Route        | Method |
| ------------ | ------ |
| `/task/list` | GET    |

Response:

```typescript
{
    "tasks": [Task],
    "total_records": int,
    "page": int,
    "per_page": int
}
```

## GetTask( ) 📚

This function retrieves details of a specific task associated with an organization.

```go
func GetTask(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Parses organization ID and task identifier (id or name) from the request
Checks the user's membership and privileges within the organization
Retrieves the details of the specified task
Returns the task data

Request:

Params (QueryString, required):

```typescript
{
  "organization_id": number,
  "id"?: number,
  "name"?: string
}
```

| Route        | Method |
| ------------ | ------ |
| `/task/{id}` | GET    |
| `/task`      |        |

Response:

```typescript
{
    "task": Task
}
```

## PostTask( ) 🛠️

This endpoint is used to create a new task for an organization.

```go
func PostTask(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Parses task data from the request body
Checks the user's membership and privileges within the organization
Creates a new task record for the organization
Returns the created task data

Request:

Body (JSON, required): Contains the task data, including title, description, due date, assignee, tags, and board column.

```typescript
{
    "title": string,
    "description": string,
    "due_date": string,
    "assignee": number[], // array of User IDs
    "tags": number[], // array of Tag IDs
    "board_column": number,
    "task_board_id": number,
    "category_id": number,
    "prioritized"?: boolean
}
```

| Route          | Method |
| -------------- | ------ |
| `/task/create` | POST   |

Response:

```typescript
{
    "task": Task
}
```

## UpdateTask( ) 🔄

This function updates details of an existing task associated with an organization.

```go
func UpdateTask(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Parses task ID and update fields from the request
Retrieves the task based on the provided task ID
Checks the user's membership and privileges within the organization
Updates the specified task record
Returns the updated task data

Request:

Params (QueryString, required):

```typescript
{
  "task_id": number,
}
```

Body (JSON, required): Contains the task update data.

```typescript
{
  "title"?: string,
  "description"?: string,
  "due_date"?: string,
  "assignee_ids"?:[number],
  "tag_ids"?: [number],
  "media_ids"?: [number],
  "task_board_id": number,
  "board_column_id"?: number,
  "category_id"?: number,
  "prioritized"?: boolean
}
```

| Route          | Method |
| -------------- | ------ |
| `/task/update` | PUT    |

Response:

```typescript
{
    "task": Task
}
```

## DeleteTask( ) ❌

This endpoint is used to delete a task associated with an organization.

```go
func DeleteTask(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Parses the task ID from the request
Checks the user's membership and privileges within the organization
Deletes the specified task record
Returns a confirmation message

Request:

Params (QueryString, required):

```typescript
{
  "task_id"?: number,
}
```

| Route          | Method |
| -------------- | ------ |
| `/task/delete` | DELETE |

Response:

```typescript
{
}
```
