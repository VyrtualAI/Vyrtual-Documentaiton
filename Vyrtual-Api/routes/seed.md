# /routes/seed.go

The `seed.go` package in the seed folder contains API endpoints for seeding data into the database for the `api.vyrtual.ai` project. This package is particularly useful for initializing the database with predefined data sets.

---

## SeedData( ) 🌱

This endpoint seeds the database with initial data for various models.

```go
func Seed(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Handles seeding data for predefined models.
Supports optional deletion of existing data based on query parameters.
Returns confirmation upon successful seeding.

Request:
* Params (QueryString, optional):
```typescript
{
  "delete"?: string // comma-separated table names or 'all'
}
```

| Route   | Method |
| ------- | ------ |
| `/seed` | GET    |

Response:

```typescript
{
    "message": "Successfully seeded database",
    "tables": [string] // List of table names
}
```

## ListTables( ) 📋
This function lists all tables in the database along with their column information.

```go
func ListTables(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Retrieves a list of all database tables and their column names.
Returns detailed information about each table.

Request:

No parameters required.

| Route         | Method |
| --------------| ------ |
| `/seed/tables`| GET    |

Response:

```typescript
[
    {
        "table_name": string,
        "columns": [string]
    },
    // More tables...
]
```

📝 Note: The seed package is critical for initializing the database with necessary data structures and default values, making it an essential part of setting up the api.vyrtual.ai project. It also provides functionality to list the current database schema, which is useful for development and debugging purposes.