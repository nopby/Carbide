# Functions

## Declaration

Functions use the following syntax:

```text
name: (parameters) -> return_type {
    body
}
```

Example:

```carbide
add: (a: i32, b: i32) -> i32 {
    return a + b
}
```

## Parameters

Parameters are declared using:

```text
name: type
```

For example:

```carbide
multiply: (a: i32, b: i32) -> i32 {
    return a * b
}
```

## Arrow Operators

The two arrow operators have distinct meanings:

| Syntax | Meaning |
| --- | --- |
| `->` | Return type |
| `=>` | Expression body |

## Return Type

`->` introduces the function's return type:

```carbide
parse: (value: [u8]) -> i32 {
    ...
}
```

A function with a block body can omit the return type. Such a function
does not return a value:

```carbide
log: (message: string) {
    std::println("{}", message)
}
```

For expression-bodied functions, the return type may be omitted when
type inference is supported. See [Expression Bodies](#expression-bodies).

## Expression Bodies

Functions containing a single expression may use `=>`:

```carbide
square: (x: i32) -> i32 => x * x
```

The `=>` operator indicates that the expression itself is the function
body.

The following are equivalent in meaning:

```carbide
square: (x: i32) -> i32 => x * x
```

and:

```carbide
square: (x: i32) -> i32 {
    return x * x
}
```

When type inference is supported, the return type may be omitted:

```carbide
square: (x: i32) => x * x
```

## The main Function

The `main` function does not need to return a value:

```carbide
main: () {
    std::println("Hello, Carbide!")
}
```

When an explicit process exit code is required, `main` can return an
integer:

```carbide
main: () -> i32 {
    return 0
}
```

The C++ backend may translate a value-less `main` into a C++ `main`
function that returns `0`.
