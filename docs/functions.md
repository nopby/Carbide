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

## Return Type

`->` introduces the function's return type:

```carbide
parse: (value: [u8]) -> i32 {
    ...
}
```

The return type may eventually be inferred where appropriate.

## Functions Without a Return Value

A function can omit the return type:

```carbide
log: (message: string) {
    std::println("{}", message)
}
```

Such a function does not return a value.
