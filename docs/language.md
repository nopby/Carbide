# Carbide Language

This document describes the initial design of the Carbide programming
language.

The language is intentionally small during its early development.
Features may be added as the language and compiler mature.

## Contents

- [Functions](functions.md), including the `main` function
- [Types](types.md)
- [Variables](variables.md)
- [Statements](statements.md)
- [Modules](modules.md)

Each topic is described in exactly one place. This page only covers the
overall design principles.

## Hello World

```carbide
import std

main: () {
    std::println("Hello, Carbide!")
}
```

## Design Principles

- **Small and readable syntax.** The language stays small while it is
  young.
- **Explicit types.** Integer widths and mutability are visible in the
  source.
- **Language semantics belong to Carbide.** They are not defined by the
  C++ backend.

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
