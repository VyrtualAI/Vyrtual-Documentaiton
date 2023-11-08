# /routes/attendee.go

```typescript
type Attendee = {
id: number
created_at: Date
updated_at: Date
deleted_at: Date
user_id: number
user: User
event_id: number
event: Event
}
```

The `attendee.go` package within the routes folder contains API endpoints for managing `Event` attendees.

📝 **Note:** This package is part of the `api.vyrtual.ai` project and is focused on handling attendee-related operations, such as listing, creating, updating, and deleting attendees.

The file provides the following features:

1. Listing of attendees
2. Retrieval of a specific attendee
3. Creation of an attendee
4. Updating attendee details
5. Deletion of an attendee

---

## ListAttendees( ) 🚀

This endpoint lists attendees, with support for pagination and filtering by specific identifiers.

```go
func ListAttendees(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Parses pagination parameters (page, per_page) from the request
Determines the offset and limit based on pagination
Retrieves attendees based on the specified identifier and pagination
Returns the list of attendees along with total records, page number, and items per page

Request:
* Params (QueryString, required):
  ```typescript
  {
    "attendee_id"?: number,
    "user_id"?: number,
    "event_id"?: number
    "page"?: number,
    "per_page"?: number,
  }
  ```

| Route           | Method |
| --------------- | ------ |
| `/attendee/list`| GET    |

Response:

```typescript
{
    "attendees": [Attendee],
    "total_records": int,
    "page": int,
    "per_page": int
}
```

## GetAttendee( ) 📚
This function retrieves details of a specific attendee.

```go
func GetAttendee(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Extracts the attendee ID from the URL or request parameters
Retrieves the details of the specified attendee
Returns the attendee data

Request:
* Params (QueryString, required):
  ```typescript
  {
    "attendee_id"?: number,
    "user_id"?: number,
    "event_id"?: number
  }
  ```

| Route                     | Method |
| ------------------------- | ------ |
| `/attendee/{id}`          | GET    |
| `/attendee`               | GET    |

Response:

```typescript
{
    "attendee": Attendee
}
```

## PostAttendee( ) 🛠️
This endpoint is used to create a new attendee record.

```go
func PostAttendee(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Parses attendee data from the request body
Creates a new attendee record
Returns the created attendee data

Request:

* Body (JSON, required): Contains the attendee data including User and Event identifiers.
```typescript
{
    "user": number,
    "event": number
}
```
| Route                     | Method |
| ------------------------- | ------ |
| `/attendee/create`        | POST   |

Response:

```typescript
{
    "attendee": Attendee
}
```

## UpdateAttendee( ) 🔄
This function updates details of an existing attendee.

```go
func UpdateAttendee(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Parses attendee ID and update fields from the request
Updates the specified attendee record
Returns the updated attendee data

Request:
* Params (QueryString, required):
  ```typescript
  {
    "attendee_id": number,
  }
  ```
* Body (JSON, required): Contains the attendee update data
  ```typescript
  {
    "user_id"?: number,
    "event_id"?: number
  }
  ```

| Route                     | Method |
| ------------------------- | ------ |
| `/attendee/update`        | PUT    |

Response:

```typescript
{
    "attendee": Attendee
}
```

## DeleteAttendee( ) ❌
This endpoint is used to delete an attendee record.

```go
func DeleteAttendee(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Parses the attendee ID from the request
Deletes the specified attendee record
Returns a confirmation message

Request:
* Params (QueryString, required):
  ```typescript
  {
    "attendee_id"?: number,
  }
  ```

| Route                     | Method |
| ------------------------- | ------ |
| `/attendee/delete`        | DELETE |

Response:

```typescript
{}
```
