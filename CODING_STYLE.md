# Coding Style Guidelines

---

# Go (Golang) Coding Style Guide

## Introduction

This document outlines the coding style guidelines for Go (Golang) projects in our organization. Adhering to consistent coding standards improves code readability and maintainability.

## Table of Contents

1. [Formatting](#formatting)
2. [Naming Conventions](#naming-conventions)
3. [Imports](#imports)
4. [Error Handling](#error-handling)
5. [Comments](#comments)
6. [Concurrency](#concurrency)
7. [Testing](#testing)

## 1. Formatting

- Use `gofmt` to format code automatically.
- Limit lines to 80 characters for better readability.

```go
// Incorrect
func myFunction() { fmt.Println("Hello, World!") }

// Correct
func myFunction() {
    fmt.Println("Hello, World!")
}
```

## 2. Naming Conventions

- Follow the camelCase convention for variable and function names.
- Use PascalCase for exported functions, types, and constants.
- Avoid abbreviations unless they are widely accepted (e.g., HTTP).

```go
// Incorrect
var my_var int
func HTTPRequest() {}

// Correct
var myVar int
func HTTPRequest() {}
```

## 3. Imports

- Group standard library imports first, followed by third-party packages and then local packages.
- Keep imports organized and remove unused ones.

```go
// Incorrect
import (
    "fmt"
    "net/http"
    "project/packageA"
    "project/packageB"
)

// Correct
import (
    "fmt"
    "net/http"

    "github.com/thirdparty/packageA"
    "github.com/thirdparty/packageB"
    "local/project/packageC"
)
```

## 4. Error Handling

- Always check and handle errors explicitly.
- Favor returning errors over logging them within functions.

```go
// Incorrect
func myFunction() {
    result, err := someFunction()
    // Ignoring the error
}

// Correct
func myFunction() error {
    result, err := someFunction()
    if err != nil {
        return err
    }
    // Continue with the result
    return nil
}
```

## 5. Comments

- Write clear and concise comments to explain non-obvious code.
- Document exported functions and types with comments.

```
// Incorrect
// Function to process data
func process() {}

// Correct
// processData is a function that performs data processing.
func processData() {}
```

## 6. Concurrency

- Use goroutines and channels for concurrent programming.
- Avoid using shared memory for communication; prefer communication through channels.

```go
// Incorrect
var sharedData int

func worker() {
    sharedData++
}

// Correct
func worker(ch chan int) {
    ch <- 1
}

// In the calling function
func main() {
    ch := make(chan int)
    go worker(ch)
    data := <-ch
    // Process data
}
```

## 7. Testing

- Write comprehensive unit tests for your code.
- Use the `testing` package for tests.
- Name test files with the `_test.go` suffix.

```go
// File: my_function_test.go

package mypackage

import (
    "testing"
)

func TestMyFunction(t *testing.T) {
    result := myFunction()
    if result != expectedValue {
        t.Errorf("Expected %v, got %v", expectedValue, result)
    }
}
```

## Node.js Coding Style

# Node.js Coding Style Guide

## Introduction

This document outlines the coding style guidelines for Node.js projects in our organization. Consistent coding standards improve code maintainability and collaboration.

## Table of Contents

1. [Formatting](#formatting)
2. [Naming Conventions](#naming-conventions)
3. [Modules and Imports](#modules-and-imports)
4. [Error Handling](#error-handling)
5. [Comments](#comments)
6. [Asynchronous Programming](#asynchronous-programming)
7. [Testing](#testing)

## 1. Formatting

- Use 2 spaces for indentation.
- Limit lines to 80 characters for better readability.
- End files with a newline.

```javascript
// Incorrect
function myFunction() { console.log("Hello, World!"); }

// Correct
function myFunction() {
  console.log("Hello, World!");
}
```

## 2. Naming Conventions

- Follow the camelCase convention for variable and function names.
- Use PascalCase for class names.
- Use UPPERCASE_WITH_UNDERSCORES for constants.

```javascript
// Incorrect
var my_var;
function httpRequest() {}

// Correct
var myVar;
function HttpRequest() {}
```

## 3. Modules and Imports

- Use `import` statements for module dependencies.
- Group and order import statements consistently.

```javascript
// Incorrect
const localModule = require('./localModule');
const fs = require('fs');
const express = require('express');

// Correct
const express = require('express');
const fs = require('fs');
const localModule = require('./localModule');
```

## 4. Error Handling

- Always check and handle errors explicitly.
- Use the `try-catch` block for synchronous code and `async/await` for asynchronous code.

```javascript
// Incorrect
function myFunction() {
  // Ignoring errors
}

// Correct
function myFunction() {
  try {
    // Code that might throw an error
  } catch (error) {
    // Handle the error
  }
}
```

## 5. Comments

- Write clear and concise comments to explain non-obvious code.
- Document exported functions and modules with comments.

```javascript
// Incorrect
// Function to process data
function process() {}

// Correct
// processData is a function that performs data processing.
function processData() {}
```

## 6. Asynchronous Programming

- Prefer using Promises or `async/await` for asynchronous code.
- Avoid callback hell by using modular and named functions.

```javascript
// Incorrect
fs.readFile('file.txt', (err, data) => {
  // Callback code
});

// Correct
const readFilePromise = (filename) => {
  return new Promise((resolve, reject) => {
    fs.readFile(filename, (err, data) => {
      if (err) {
        reject(err);
      } else {
        resolve(data);
      }
    });
  });
};
```

## 7. Testing

- Write comprehensive unit tests for your code.
- Use testing frameworks like Jest or Mocha.
- Name test files with the `.test.js` suffix.

```javascript
// File: myFunction.test.js

const { myFunction } = require('./myModule');

test('myFunction should return the expected value', () => {
  const result = myFunction();
  expect(result).toBe(expectedValue);
});
```
