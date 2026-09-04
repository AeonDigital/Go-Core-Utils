xreflect
================================

> Reflection helpers to simplify common runtime type operations in Go.

&nbsp;

This package gathers lightweight helpers that make common `reflect`-based operations
simpler to use. Its intent is to provide small, reusable utilities for runtime type
inspection and instance allocation.

At the moment the package exposes a single convenience function but is intended to
grow with additional reflection helpers.




&nbsp;
________________________________________________________________________________

## PURPOSE

`xreflect` centralizes small utilities that reduce boilerplate when working with
Go's `reflect` package. It is especially useful for CLI tools, tests, and factories
where dynamic instance allocation and generic convenience functions improve ergonomics.




&nbsp;
________________________________________________________________________________

## INSTALLATION

Add the package to your module:

```shell
  go get github.com/AeonDigital/Go-Core/xreflect@latest
```

Import it in your code:

```go
import "github.com/AeonDigital/Go-Core/xreflect"
```




&nbsp;
________________________________________________________________________________

## BASIC USAGE

Allocate an initialized instance of a type `T` at runtime. For value types (e.g.,
`int`, `struct`), `NewInstanceOf[T]()` returns a non-nil initialized value. For pointer
types, it returns a non-nil pointer to the underlying struct type, preventing nil
pointer panics.

```go
// For a struct value type
type Config struct { Port int }
cfg := xreflect.NewInstanceOf[Config]() // returns Config with zero-values

// For a pointer type
ptr := xreflect.NewInstanceOf[*Config]() // returns *Config (non-nil)
```


This helper is intended for dynamic factories, test fixtures, and code that needs
to allocate types generically without writing reflection boilerplate.




&nbsp;
________________________________________________________________________________

## SUPPORTED APIS

Currently the package exposes:

- `xreflect.NewInstanceOf[T any]() T`

This function uses `reflect` under the hood to allocate either a value or a pointer
instance depending on the generic type parameter supplied.




&nbsp;
________________________________________________________________________________

## EXTERNAL DEPENDENCIES

`xreflect` depends only on the Go standard library:

- `reflect`

No third-party libraries are required.