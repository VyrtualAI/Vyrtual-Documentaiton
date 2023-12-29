# /routes/event.go

The `event.go` package within the event folder contains API endpoints for managing `Event` entities.

📝 **Note:** This package is a part of the `api.vyrtual.ai` project and focuses on operations related to events, such as listing, retrieving, creating, updating, and deleting events.

The file offers the following functionalities:

1. Listing of events
2. Retrieval of a specific event
3. Creation of an event
4. Updating event details
5. Deletion of an event

---

## ListEvents( ) 🚀

This endpoint lists events, supporting pagination and time-based filtering.

```go
func ListEvents(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Parses pagination parameters (page, per_page) from the request.
Determines the offset and limit based on pagination.
Retrieves events within a specified time range and based on other identifiers.
Returns the list of events along with total records, page number, and items per page.

Request:

Params (QueryString, required):

```typescript
{
  "page"?: number,
  "per_page"?: number,
  "start_time"?: Date,
  "end_time"?: Date,
  "organization"?: string,
  "organizer"?: number
}
```

| Route         | Method |
| ------------- | ------ |
| `/event/list` | GET    |

Response:

```typescript
{
    "events": [Event],
    "total_records": int,
    "page": int,
    "per_page": int
}
```

## GetEvent( ) 📚

This function retrieves details of a specific event.

```go
func GetEvent(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Extracts the event ID from the URL or request parameters.
Retrieves the details of the specified event.
Returns the event data.

Request:

Params (QueryString, required):

```typescript
{
  "id"?: number
}
```

| Route         | Method |
| ------------- | ------ |
| `/event/{id}` | GET    |
| `/event/`     | GET    |

Response:

```typescript
{
    "event": Event
}
```

## PostEvent( ) 🛠️

This endpoint is used to create a new event record.

```go
func PostEvent(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Parses event data from the request body.
Creates a new event record.
Returns the created event data.

Request:

Body (JSON, required): Contains the event data including organizers and attendees.

```typescript
{
  "title": string,
  "startTime": Date,
  "endTime": Date,
  "description": string,
  "meetingLink": string,
  "organizers": [number],
  "organization": number,
  "attendees": [number]
}
```

| Route           | Method |
| --------------- | ------ |
| `/event/create` | POST   |

Response:

```typescript
{
    "event": Event
}
```

## UpdateEvent( ) 🔄

This function updates details of an existing event.

```go
func UpdateEvent(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Parses event ID and update fields from the request.
Updates the specified event record.
Returns the updated event data.

Request:

Params (QueryString, required):

```typescript
{
  "event_id": number,
}
```

Body (JSON, required): Contains the event update data

```typescript
{
  "title"?: string,
  "start_time"?: Date,
  "end_time"?: Date,
  "description"?: string,
  "meeting_link"?: string,
  "organizer_ids"?: [number],
  "attendee_ids"?: [number]
}
```

| Route           | Method |
| --------------- | ------ |
| `/event/update` | PUT    |

Response:

```typescript
{
    "event": Event
}
```

## DeleteEvent( ) ❌

This endpoint is used to delete an event record.

```go
func DeleteEvent(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```

Process:

Parses the event ID from the request.
Deletes the specified event record.
Returns a confirmation message.

Request:

Params (QueryString, required):

```typescript
{
  "id"?: number,
}
```

| Route           | Method |
| --------------- | ------ |
| `/event/delete` | DELETE |

Response:

```typescript
{
}
```
