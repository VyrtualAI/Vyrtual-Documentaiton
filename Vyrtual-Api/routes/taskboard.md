# /routes/taskboard.go

The `taskboard` package within the TaskBoard folder contains API endpoints for managing `TaskBoard` entities.

📝 **Note:** This package is a part of the `api.vyrtual.ai` project and focuses on operations related to task boards, such as listing, retrieving, creating, updating, and deleting task boards.

The file offers the following functionalities:

1. Listing of task boards
2. Retrieval of a specific task board
3. Creation of a task board
4. Updating task board details
5. Deletion of a task board

---

## ListTaskBoards( ) 🚀

This endpoint lists task boards, supporting pagination and time-based filtering.

```go
func ListTaskBoards(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

- Parses organization ID and pagination parameters (page, per_page) from the request.
- Verifies organization membership of the requesting user.
- Retrieves task boards within the organization based on pagination.
- Returns the list of task boards along with total records, page number, and items per page.

Request:

Params (QueryString, required):

```typescript
{
"organization_id": number,
"page"?: number,
"per_page"?: number
}
```

| Route             | Method |
| ----------------- | ------ |
| `/taskboard/list` | GET    |

Response:

```typescript
{
"task_board": [TaskBoard],
"total_records": int,
"page": int,
"per_page": int
}
```

## GetTaskBoard( ) 📚

This function retrieves details of a specific task board.

```go
func GetTaskBoard(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

- Extracts the task board ID from the URL or request parameters.
- Verifies organization membership of the requesting user.
- Retrieves the details of the specified task board.
- Returns the task board data.

Request:

Params (QueryString, required):

```typescript
{
"organization_id": number,
"id"?: number
}
```

| Route             | Method |
| ----------------- | ------ |
| `/taskboard/{id}` | GET    |
| `/taskboard/`     | GET    |

Response:

```typescript
{
"task_board": TaskBoard
}
```

## PostTaskBoard( ) 🛠️

This endpoint is used to create a new task board record.

```go
func PostTaskBoard(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

- Parses organization ID and task board data from the request body.
- Verifies organization membership of the requesting user.
- Creates a new task board record.
- Returns the created task board data.

Request:

Params (QueryString, required):

```typescript
{
"organization_id": number,
}
```

Body (JSON, required): Contains the task board data including name, organization, columns, etc.

```typescript
{
"name": string,
"columns": [Column]
}
```

| Route               | Method |
| ------------------- | ------ |
| `/taskboard/create` | POST   |

Response:

```typescript
{
"task_board": TaskBoard
}
```

## UpdateTaskBoard( ) 🔄

This function updates details of an existing task board.

```go
func UpdateTaskBoard(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

- Parses task board ID and update fields from the request.
- Verifies organization membership of the requesting user.
- Updates the specified task board record.
- Returns the updated task board data.

Request:

Params (QueryString, required):

```typescript
{
"taskboard_id": number,
}
```

Body (JSON, required): Contains the task board update data

```typescript
{
"name"?: string,
"columns"?: [BoardColumn],
"task_ids"?: [number]
}
```

| Route               | Method |
| ------------------- | ------ |
| `/taskboard/update` | PUT    |

Response:

```typescript
{
"task_board": TaskBoard
}
```

## DeleteTaskBoard( ) ❌

This endpoint is used to delete a task board record.

```go
func DeleteTaskBoard(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

- Parses the task board ID from the request.
- Verifies organization membership of the requesting user.
- Deletes the specified task board record.
- Returns a confirmation message.

Request:

Params (QueryString, required):

```typescript
{
"taskboard_id": number,
}
```

| Route               | Method |
| ------------------- | ------ |
| `/taskboard/delete` | DELETE |

Response:

```typescript
{
}
```
