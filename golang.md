# Golang

An interesting language that build with concurrency in mind. If you intended to run your application in multiple thread, give it a try.

## Common Error
- could not determine kind of name for C.****
 * remove blank line above `import "C"`
- if `CGO` can't find your include header files. `"...header.h" : no such file or directory`
 * add `#cgo CFLAGS: -v` will help you debug.
