# csvq

SQL like query language for csv

[![Build Status](https://travis-ci.org/mithrandie/csvq.svg?branch=master)](https://travis-ci.org/mithrandie/csvq)
[![codecov](https://codecov.io/gh/mithrandie/csvq/branch/master/graph/badge.svg)](https://codecov.io/gh/mithrandie/csvq)

## Install

### Binary

1. Download an archive file from [release page](https://github.com/mithrandie/csvq/releases).
2. Extract the downloaded archive and add a binary file in it to your path.

### Build from source

1. Install Go. (ref. [Getting Started - The Go Programming Language](https://golang.org/doc/install))
2. ```$ go get -u github.com/mithrandie/csvq```

## Usage

```shell
# Simple query
csvq "select id, name from user.csv"
csvq "select id, name from user"

# Specify data delimiter as tab character
csvq -d "\t" "select count(*) from user.csv"

# Load from another directory
csvq "select id, name from `/path/to/user.csv`"
csvq -r /path/to "select user.id, user.name, country.name from user.csv natural join country.csv"

# Load no-header-csv
csvq --no-header "select c1, c2 from user.csv"

# Load from standard input
csvq "select * from stdin" < user.csv
csvq "select *" < user.csv
cat user.csv | csvq "select *"

# Output in JSON format
csvq write -f json "select integer(id) as id, name from user.csv"

# Output to a file
csvq write -o new_user.csv "select id, name from user"

# Show help
csvq -h
```