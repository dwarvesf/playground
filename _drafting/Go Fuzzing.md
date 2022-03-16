---
tags: go, fuzzing, test, toolset
author: HP
---

# Go fuzz tool

## Why Fuzzing?

We spent time and more effort to cover our source code by unit tests. Fuzzing technique provides results with little effort - once a fuzzer’s up and running, it can be left for hours, days, or months to look for bugs with no interaction. It can reveal bugs missed in a manual audit.

Fuzzing is a way of discovering bugs in software by providing randomized inputs to programs to find test cases that cause a crash. Fuzzing your programs can give you a quick view on their overall robustness and help you find and fix critical bugs.

## Fuzzing in Go

Go fuzz is supported from version 1.18. Behind the scenes of fuzzing is generate subset of built-in types for the function's input to discover coding errors and security loopholes in our lines of code. We prepare an input set, go fuzz help us generate a huge set of testing set and invoke the testing function. The testing set can be valid values, boundary values, invalid values, etc... 

## How to use

As normal test function, the fuzzing test function is placed in `<xxx>_test.go` file.
The fuzzing test function must begin by Fuzz<Function> with first params belongs to `testing.F`

```go
func FuzzFoo(f *testing.F) {
	f.Add(5, "str") // Seed corpus addition
	f.Fuzz(func(t *testing.T, i int, s string) {
		out, err := Foo(i, s)
		if err != nil && out != "" {
			t.Errorf("%v, %v", out, err)
		}
	})
}
```

To enable fuzzing, run go test with the -fuzz flag, providing a regex matching a single fuzz test. By default, all other tests in that package will run before fuzzing begins. This is to ensure that fuzzing won’t report any issues that would already be caught by an existing test.

```
go test -fuzz=Fuzz
```

When go fuzz find out the issues, go test CLI will show the command to reproduce the test case. Fixing our code and rerun the failed cases.

```
go test -run=FuzzFoo/1ffc28f7538e29d79fce69fef20ce5ea72648529a9ca10bea392bcff28cd015c
```

#### Reference

- [Tutorial: Getting started with fuzzing](https://go.dev/doc/tutorial/fuzz)
- [Go Fuzzing](https://go.dev/doc/fuzz)