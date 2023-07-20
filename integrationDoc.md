# Setup Go

Follow the instructions below to send custom events from your Go backend.

## Install

````
go get "github.com/AblaAnalytics/ablaevent-go"
Configure
package main
import (
    "github.com/AblaAnalytics/ablaevent-go"
)
func main() {
    client, _ := posthog.NewWithConfig("phc_ySCF4YinUf6DxprJ5B0jXtzgijeTqFkWPsIIfC3yTrC", posthog.Config{Endpoint: "https://e.abla.io"})
    defer client.Close()
}
```` 
## Send an Event

````
client.Enqueue(posthog.Capture{
    DistinctId: "test-user",
    Event: "test-snippet"
})

````
