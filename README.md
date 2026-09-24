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
independent from C++. This allows the C++ backend to be replaced by a
native compiler in the future without changing the language itself.

## Language at a glance

- [Functions](docs/functions.md): `name: (params) -> type { ... }`, with
  `=>` for expression bodies.
- [Types](docs/types.md): explicit-width integers (`i32`, `u64`, ...) and
  collections written `[T]`.
- [Variables](docs/variables.md): immutable by default, `mut` for
  mutable.
- [Statements](docs/statements.md): no semicolons; newlines separate
  statements.
- [Modules](docs/modules.md): `import`, with explicitly qualified names.

## Documentation

The language documentation is available in [`docs/`](docs/), starting
with [`docs/language.md`](docs/language.md).

The current documentation describes the initial language design and
should be considered a living specification.
