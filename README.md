# Carbide

Carbide is a modern systems programming language designed for clarity,
safety, and seamless C++ interoperability.

Carbide initially compiles to C++ and is designed to eventually support
a native compiler.

## Example

```carbide
import std

main: () {
    std::println("Hello, Carbide!")
}
```

## Design

Carbide is designed around a small and readable syntax while keeping a
strong, explicit type system.

The initial compiler targets C++, but Carbide's language semantics are
independent from C++.

This allows the C++ backend to be replaced by a native compiler in the
future without changing the language itself.

## Functions

Functions use `:` after the function name, followed by parameters and
an optional return type.

```carbide
add: (a: i32, b: i32) -> i32 {
    return a + b
}
```

Single-expression functions can use `=>`:

```carbide
square: (x: i32) -> i32 => x * x
```

The meaning of these operators is intentionally simple:

```text
->    return type
=>    expression body
```

## Types

Carbide uses explicit-width primitive integer types:

```text
i8
i16
i32
i64
i128

u8
u16
u32
u64
u128
```

Floating-point and other primitive types will be documented as the
language specification evolves.

Collection types use square brackets:

```carbide
numbers: [i32] = [1, 2, 3, 4, 5]
```

## Statements

Carbide does not use semicolons to terminate statements.

Statements are separated by newlines where syntactically unambiguous.

```carbide
main: () {
    x: i32 = 10
    y: i32 = 20

    return x + y
}
```

## Imports

Modules are imported using `import`:

```carbide
import std
```

Imported names remain explicitly qualified:

```carbide
std::println("Hello")
```

The `use` declaration is intentionally not part of the initial language
specification. It may be introduced later for bringing individual names
into scope.

## Documentation

The language documentation is available in [`docs/`](docs/).

The current documentation describes the initial language design and
should be considered a living specification.
