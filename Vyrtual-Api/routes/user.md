# /routes/user.go

The `user.go` package in the user folder contains API endpoints related to user management for the `api.vyrtual.ai` project. This includes retrieving, creating, updating, and deleting user data.

---

## ListUsers( ) 👥

Lists all users with support for pagination.

```go
func ListUsers(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Request:

- Params (QueryString, optional):

```typescript
{
  "page"?: number,
  "per_page"?: number
}
```

| Route        | Method |
| ------------ | ------ |
| `/user/list` | GET    |

Response:

Returns a list of users with pagination details.

## GetUser( ) 👤

Retrieves detailed information about a specific user.

```go
func GetUser(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

| Route        | Method |
| ------------ | ------ |
| `/user`      | GET    |
| `/user/{id}` | GET    |

Response:

Returns detailed user information based on the provided identifier.

## PostUser( ) 🆕

Creates a new user record.

```go
func PostUser(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

| Route          | Method |
| -------------- | ------ |
| `/user/create` | POST   |

Response:

Returns the created user data.

## UpdateUser( ) 🔄

Updates details of an existing user.

```go
func UpdateUser(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Request:

- Params (QueryString, optional):

```typescript
{
  "user_id"?: number,
}
```

Body (JSON, required): Contains the task board update data

```typescript
{
"language_codes"?: [string],
"first_name"?: string,
"last_name"?: string,
"primary_organization_id"?: number,
"email"?: string,
"phone_number"?: string,
"image"?: string
}
```

| Route          | Method |
| -------------- | ------ |
| `/user/update` | PUT    |

Response:

Returns the updated user data.

## DeleteUser( ) ❌

Deletes a user record.

```go
func DeleteUser(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

| Route          | Method |
| -------------- | ------ |
| `/user/delete` | GET    |

Response:

```typescript
{
}
```

Confirms the deletion of the user.
