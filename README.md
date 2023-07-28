# Ablaevent Go

# Quickstart

Install ablaevent to your gopath
```bash
$ go get github.com/AblaAnalytics/ablaevent-go
```

Go 🦔!
```go
package main

import (
    "os"
    "github.com/AblaAnalytics/ablaevent-go"
)

func main() {
    client := posthog.New(os.Getenv("POSTHOG_API_KEY"))
    defer client.Close()

    // Capture an event
    client.Enqueue(posthog.Capture{
      DistinctId: "test-user",
      Event:      "test-snippet",
      Properties: posthog.NewProperties().
        Set("plan", "Enterprise").
        Set("friends", 42),
    })
    
    // Add context for a user
    client.Enqueue(posthog.Identify{
      DistinctId: "user:123",
      Properties: posthog.NewProperties().
        Set("email", "john@doe.com").
        Set("proUser", false),
    })
    
    // Link user contexts
    client.Enqueue(posthog.Alias{
      DistinctId: "user:123",
      Alias: "user:12345",
    })
    
    // Capture a pageview
    client.Enqueue(posthog.Capture{
      DistinctId: "test-user",
      Event:      "$pageview",
      Properties: posthog.NewProperties().
        Set("$current_url", "https://example.com"),
    })
}

```
