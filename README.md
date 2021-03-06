Go PyRun - simple interactation with Python
===========================================

It runs a Python interpreter in single dedicated thread and allows to get
result of Python code evaluation in Golang.

[![CircleCI](https://circleci.com/gh/ei-grad/go-pyrun.svg?style=svg)](https://circleci.com/gh/ei-grad/go-pyrun)

Install
-------

You would need python-2.7 headers to build and install go-pyrun. On Ubuntu just
install the python2.7-dev package:

    apt-get install python2.7-dev

Then you should be able to install go-pyrun by `go get`:

    go get github.com/ei-grad/go-pyrun

Example
-------

```go
package main

import "github.com/ei-grad/go-pyrun"
import "fmt"
import "log"

func main() {
    py := pyrun.NewPython()
    err := py.Execute(`
def hello():
    return 'Hello, world!'
`)
    if err != nil {
        log.Fatalf("Execute failed: %s", err)
    }
    ret, err := py.EvalToString("hello()")
    if err != nil {
        log.Fatalf("EvalToString failed: %s", err)
    }
    fmt.Printf("Hello from Python: %s\n", ret)
}
```

Contributing
------------

Feel free to open issues and send pull requests implementing new useful methods.

But it shouldn't be more than a something between a joke and a ducktape for emeregency cases and experimenting.

Look also to @bradfitz's similar module for perl: https://github.com/bradfitz/campher.
