# hackernews
A project to learn integration of go with gqlgen

A Hackernews clone with Go and gqlgen. 

The API should be able to handle registration, authentication, submitting links and getting list of links.

## Instructions

1. Cli
```
git clone https://github.com/ellieasager/hackernews
cd hackernews
go mod init github.com/ellieasager/hackernews
go get github.com/99designs/gqlgen
printf '// +build tools\npackage tools\nimport _ "github.com/99designs/gqlgen"' | gofmt > tools.go
go mod tidy
go run github.com/99designs/gqlgen init
go run server.go
```

2. In your browser go to http://localhost:8080/