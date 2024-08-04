---
title: "Go Code Example"
date: 2024-08-04T12:00:00+00:00
draft: false
categories:
  - programming
tags:
  - go
  - net/http
---

This is a Go code example using the `net/http` package:

```go
package main

import (
	"fmt"
	"log"
	"net/http"
)

func main() {
	http.HandleFunc("/", func(w http.ResponseWriter, r *http.Request) {
		fmt.Fprintln(w, "Hello, World!")
	})

	log.Fatal(http.ListenAndServe(":3000", nil))
}
