# goapp-live-reaload

# Setting up simple demo server

```go
  package main

  import (
    "fmt"
    "net/http"
  )

  func main() {
    http.HandleFunc("/", func(w http.ResponseWriter, r *http.Request) {
      fmt.Fprintf(w, "Hello World")
    })
    http.ListenAndServe(":8080", nil)
  }
```
# Installing reflex

```sh 
go get github.com/cespare/reflex
```
# Setting up makefile
### Every time, typing long command on terminal to build or run Go application is very tedious. So we use makefile to kind of alias to short command for long command.

```sh
build:
	go build -o server main.go

run: build
	./server

watch:
	ulimit -n 1000 #increase the file watch limit, might required on MacOS
	reflex -s -r '\.go$$' make run
```
