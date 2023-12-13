# package category

The `category` package contains API endpoints for managing `Category` entities.

Note: This package is part of the `api.vyrtual.ai` project and focuses on operations related to categories, such as listing, retrieving, creating, updating, and deleting categories.

## ListCategories( )

This endpoint lists categories, supporting pagination and time-based filtering.

```go
func ListCategories(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

- Parses organization ID and pagination parameters (page, per_page) from the request.
- Verifies organization membership of the requesting user.
- Retrieves categories within the organization based on pagination.
- Returns the list of categories along with total records, page number, and items per page.

Request:

Params (QueryString, required):

```typescript
{
"organization_id": number,
"page"?: number,
"per_page"?: number
}
```

| Route          | Method |
| -------------- | ------ |
| /category/list | GET    |

Response:

```typescript
{
"categories": [Category],
"total_records": int,
"page": int,
"per_page": int
}
```

## GetCategories( )

This function retrieves details of a specific category.

```go
func GetCategories(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

- Extracts the category ID from the URL or request parameters.
- Verifies organization membership of the requesting user.
- Retrieves the details of the specified category.
- Returns the category data.

Request:

Params (QueryString, required):

```typescript
{
"organization_id": number,
"id"?: number
}
```

| Route          | Method |
| -------------- | ------ |
| /category/{id} | GET    |
| /category/     | GET    |

Response:

```typescript
{
"category": Category
}
```

## PostCategories( )

This endpoint is used to create a new category record.

func PostCategories(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }

Process:

- Parses organization ID and category data from the request body.
- Verifies organization membership of the requesting user.
- Creates a new category record.
- Returns the created category data.

Request:

Body (JSON, required): Contains the category data including name, department, organization, watchers, etc.

```typescript
{
"name": string,
"department_id": number,
"organization_id": number,
"watchers": [User]
}
```

| Route            | Method |
| ---------------- | ------ |
| /category/create | POST   |

Response:

```typscript
{
"category": Category
}
```

## UpdateCategories( )

This function updates details of an existing category.

func UpdateCategories(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }

Process:

- Parses category ID and update fields from the request.
- Verifies organization membership of the requesting user.
- Updates the specified category record.
- Returns the updated category data.

Request:

Params (QueryString, required):

```typescript
{
"category_id": number
}
```

Body (JSON, required): Contains the category update data

```typescript
{
"name"?: string,
"watchers"?: [User]
}
```

| Route            | Method |
| ---------------- | ------ |
| /category/update | PUT    |

Response:
{
"category": Category
}

## DeleteCategories( )

This endpoint is used to delete a category record.

```go
func DeleteCategories(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

- Parses the category ID from the

Request:

Params (QueryString, required):

```typescript
{
"category_id": number
"organization_id": number
}
```

| Route            | Method |
| ---------------- | ------ |
| /category/delete | DELETE |

```typescript
{
}
```
