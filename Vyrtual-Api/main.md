# /main.go

This is the entry point of the application

## Introduction

The **main.go** file in the root of the project is the entry point for the application. The main function initializes the application and sets up the necessary routing for the associated services.

The file imports packages from the Go standard library and the application's own custom packages which include routes and services.

## Code Breakdown

1. **Import Packages**

    At the beginning of the file, there are several packages imported. These packages provide the necessary functionality for the application. 

    ```go 
    import (
        "fmt"
        "log"
        "os"
        "strconv"
        "api.vyrtual.ai/pkg/service"
        "api.vyrtual.ai/routes/agora"
        "api.vyrtual.ai/routes/attendee"
        "api.vyrtual.ai/routes/event"
        "api.vyrtual.ai/routes/file"
        "api.vyrtual.ai/routes/folder"
        "api.vyrtual.ai/routes/organization"
        "api.vyrtual.ai/routes/ping"
        "api.vyrtual.ai/routes/seed"
        "api.vyrtual.ai/routes/user"
        env "github.com/joho/godotenv"
    )
    ```

2. **BuildRoutes Function**

    The function `BuildRoutes` is a helper function used to build and return all the routes for the application combining both internal and consumer APIs.

3. **APIs**

    The `InternalApis` and `ConsumerApis` variables hold the routes for the APIs.

4. **Main Function**

    This is where the application is initialized and run. It loads environment variables, sets up the server's port, lists all available routes for both internal and consumer APIs, primes the server, retrieves the available database tables and finally initializes the server.

```go
func main() {
    //...
}
```

## Tables

The table below gives a summary of the functions and variables in the **main.go** file:

| Function/Variable     | Description                                                      |
|-----------------------|------------------------------------------------------------------|
| `main()`              | This is the main function that starts the server                 |
| `BuildRoutes()`       | This function is used to build the routes for the APIs           |
| `InternalApis`        | This variable holds the routes for the internal APIs             |
| `ConsumerApis`        | This variable holds the routes for the consumer APIs             |
