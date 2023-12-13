# /routes/department.go

The `department` package contains API endpoints for managing `Department` entities.

Note: This package is part of the `api.vyrtual.ai` project and focuses on operations related to departments, such as listing and retrieving department details.

## ListDepartments( )

This endpoint lists departments, supporting pagination.

Function Signature:

```go
func ListDepartments(w http.ResponseWriter, r *http.Request, ctx *service.Service) error
```

Process:

- Parses pagination parameters (page, per_page) from the request.
- Retrieves departments based on pagination.
- Returns the list of departments along with total records, page number, and items per page.

### Request:

Params (QueryString, optional):

```typescript
{
"page": number,
"per_page": number
}
```

### Route:

| Route        | Method |
| ------------ | ------ |
| `/task/list` | GET    |

### Response:

```typescript
{
"departments": [Department],
"total_records": int,
"page": int,
"per_page": int
}
```

## GetDepartments( )

This function retrieves details of a specific department.

Function Signature:

```go
func GetDepartments(w http.ResponseWriter, r *http.Request, ctx *service.Service) error
```

Process:

- Extracts the department ID from the URL or request parameters.
- Retrieves the details of the specified department.
- Returns the department data.

### Request:

Params (QueryString, optional):

```typescript
{
"id": number
}
```

### Route:

| Route        | Method |
| ------------ | ------ |
| `/task/{id}` | GET    |

### Response:

```typescript
{
"department": Department
}
```
