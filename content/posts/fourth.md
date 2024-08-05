---
title: "Go Custom Server Example"
date: 2024-08-05T12:00:00+00:00
draft: false
categories:
  - programming
tags:
  - go
  - net/http
summary: "A Go code example demonstrating how to set up a basic Custom HTTP server with HTTPS support."
---

Here is an example of a simple Go Custom HTTP server:

```go
package main

import (
	"context"
	"fmt"
	"log"
	"net/http"
)

func main() {
	http.HandleFunc("/", func(w http.ResponseWriter, r *http.Request) {
		fmt.Fprintln(w, "Customer Service")
	})

	s := http.Server{
		Addr: ":3000",
	}
	go func() {
		log.Fatal(s.ListenAndServeTLS("./cert.pem", "./key.pem"))
	}()

	fmt.Println("Server started and listening on :3000 <Enter> to shutdown")
	fmt.Scanln()
	s.Shutdown(context.Background())
	fmt.Println("Server stopped")
}
