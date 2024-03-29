---
tags: 
  - go
  - license
  - developer
title: Bunk License Check
date: 2020-02-05
description: Golang license and dependency checker. Prints list of all dependencies (both from std and 3rd party), number of times used, their license and saves all the license files in /licenses.
authors: 
- han
menu: memo
type: null
hide_frontmatter: false
---

## License detector tool: Glice
Golang license and dependency checker. Prints list of all dependencies (both from std and 3rd party), number of times used, their license and saves all the license files in /licenses.

### Build
* Clone Glice to your local workspace: `$go get github.com/ribice/glice`
* Go install to your $GOBIN: `$ go install github.com/ribice/glice`

### Run
`$ glice`
