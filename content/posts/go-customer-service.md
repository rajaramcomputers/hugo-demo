---
title: "Go Customer Service Example"
date: 2024-08-04T12:00:00+00:00
draft: false
categories:
  - programming
tags:
  - go
  - net/http
summary: "A Go code example demonstrating how to set up a basic HTTP server with HTTPS support."
---

This is a Go code example demonstrating how to set up a basic HTTP server with HTTPS support using the `net/http` package:

```go
package main

import (
	"fmt"
	"log"
	"net/http"
)

func main() {
	http.HandleFunc("/", func(w http.ResponseWriter, r *http.Request) {
		fmt.Fprintln(w, "Customer Service")
	})

	log.Fatal(http.ListenAndServeTLS(":3000", "./cert.pem", "./key.pem", nil))
}
