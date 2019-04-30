# queue

> A task queue for mitigating server pressure in high concurrency situations and improving task processing.

[![Build][Build-Status-Image]][Build-Status-Url] [![Codecov][codecov-image]][codecov-url] [![ReportCard][reportcard-image]][reportcard-url] [![GoDoc][godoc-image]][godoc-url] [![License][license-image]][license-url]

## Get

``` bash
go get -u -v github.com/zanjs/queue
```

## Usage

``` go
package main

import (
	"fmt"

	"github.com/zanjs/queue"
)

func main() {
	q := queue.NewQueue(10, 100)
	q.Run()

	defer q.Terminate()

	job := queue.NewJob("hello", func(v interface{}) {
		fmt.Printf("%s,world \n", v)
	})
	q.Push(job)

	// output: hello,world
}

```

## MIT License

``` text
    Copyright (c) 2019 Julian
```

[License-Url]: http://opensource.org/licenses/MIT
[License-Image]: https://img.shields.io/npm/l/express.svg
[Build-Status-Url]: https://travis-ci.org/zanjs/queue
[Build-Status-Image]: https://travis-ci.org/zanjs/queue.svg?branch=master
[codecov-url]: https://codecov.io/gh/zanjs/queue
[codecov-image]: https://codecov.io/gh/zanjs/queue/branch/master/graph/badge.svg
[ReportCard-Url]: https://goreportcard.com/report/github.com/zanjs/queue
[ReportCard-Image]: https://goreportcard.com/badge/github.com/zanjs/queue
[GoDoc-Url]: https://godoc.org/github.com/zanjs/queue
[GoDoc-Image]: https://godoc.org/github.com/zanjs/queue?status.svg