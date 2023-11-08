# /routes/agora.go

The `agora` package within the routes folder contains API endpoints for managing Agora Chat and Agora SDK sessions.

📝 **Note:** The `Agora` is a 3rd party company that provides RTC and Chat SDKs in multiple languages. 

The file provides the following features:

1. Creation of a chat access token
2. Retrieval of chat users profiles

---

## 1. ChatAccessToken( ) 🚀

This endpoint is used to create a chat access token for authorized users. The function checks the authorization of user and then creates a chat access token for them.

```go
func ChatAccessToken(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```
Process:

- Retrieves the user email from the request
- Retrieves the user using the authenticated email
- Creates a chat access token for the user
- Sends the chat access token to the client


| Route                     | Method |
| ------------------------- | ------ |
| `/agora/chat/access-token`| GET    |


Response:
```typescript
{
    "token": string
}
```

---

## 2. GetChatUsersProfiles( ) 📚

This function is used to retrieve the profiles of users in a chat.

```go
func GetChatUsersProfiles(w http.ResponseWriter, r *http.Request, ctx *service.Service) error { ... }
```
Process:

- Retrieves the user email from the request
- Retrieves the user using the authenticated email
- Extracts user ids from the request body
- Finds and retrieves the users
- Transforms the data
- Sends the response containing the chatrooms

The route for this function is:

| Route                      | Method |
| -------------------------  | ------ |
| `/agora/chat/user-profiles`| POST   |

Response:
```typescript
{
    "chatrooms": [
        {
        "[user_id]": {
            "theirProfile": User,
            "myProfile": User,
            "user_id": number
            }
        }
    ]
}
```