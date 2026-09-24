# Carbide Language

This document describes the initial design of the Carbide programming
language.

The language is intentionally small during its early development.
Features may be added as the language and compiler mature.

## Hello World

```carbide
import std

main: () {
    std::println("Hello, Carbide!")
}
```

## Function Syntax

A function is declared using:

```text
name: (parameters) -> return_type {
    body
}
```

For example:

```carbide
add: (a: i32, b: i32) -> i32 {
    return a + b
}
```

An expression-bodied function can use `=>`:

```carbide
square: (x: i32) -> i32 => x * x
```

The return type may be omitted when type inference is supported:

```carbide
square: (x: i32) => x * x
```

The two arrow operators have distinct meanings:

| Syntax | Meaning |
| --- | --- |
| `->` | Return type |
| `=>` | Expression body |

## Types

Primitive integer types use explicit widths.

### Signed integers

```text
i8
i16
i32
i64
i128
```

### Unsigned integers

```text
u8
u16
u32
u64
u128
```

Collection types use square brackets:

```carbide
values: [i32] = [1, 2, 3]
```

The semantic meaning of `[T]` belongs to Carbide. Its representation in
the C++ backend is an implementation detail.

## Variables

Variables are immutable by default.

```carbide
x: i32 = 10
```

Mutable variables use `mut`:

```carbide
mut x: i32 = 10
x = 20
```

## Statements and Semicolons

Carbide does not require semicolons.

```carbide
main: () {
    x: i32 = 10
    y: i32 = 20
    z: i32 = x + y

    return z
}
```

Newlines separate statements when the syntax is unambiguous.

Newlines inside expressions do not terminate the expression when the
grammar clearly indicates that the expression continues.

## Imports

Modules are introduced using `import`:

```carbide
import std
```

Imported names are explicitly qualified:

```carbide
std::println("Hello")
```

The `use` declaration is not part of the initial language.

This distinction may be revisited later if Carbide needs a mechanism
for bringing individual names into the current scope.

## Main Function

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

## C++ Interoperability

Carbide initially targets C++.

C++ interoperability is a core feature of the language, but Carbide
types and semantics are not defined solely by their C++ representation.

For example, Carbide's `i32` may initially be emitted as:

```cpp
std::int32_t
```

The exact backend representation is not part of the Carbide language
semantics.

This separation allows a future native Carbide compiler to preserve
the same language semantics without requiring C++ as its implementation
language.
