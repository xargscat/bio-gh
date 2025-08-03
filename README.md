## Description:
bio-gh is a small CLI tool written in Go that prints the GitHub bio of the currently authenticated user using the GitHub CLI (gh).

## Requirements:

* Go (to Build)
* GitHub CLI (gh) with an authenticated session (gh auth login)
* Internet connection


## Installation:
```sh
go install github.com/u0a316/bio-gh@v1.0.0
```

## Buil
```sh
go build -o bio-gh bio-gh.go
sudo install bio-gh /usr/bin/
```

Usage:
```sh
bio-gh
```
This will print your current GitHub profile bio to stdout.

