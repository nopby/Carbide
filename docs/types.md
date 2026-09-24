# Types

Carbide uses an explicit type system.

## Integer Types

Signed integer types:

```text
i8
i16
i32
i64
i128
```

Unsigned integer types:

```text
u8
u16
u32
u64
u128
```

These types represent integers with explicitly defined widths.

The initial C++ backend can map them to the corresponding fixed-width
types from `<cstdint>`, such as:

```cpp
std::int32_t
std::uint64_t
```

However, the Carbide types are language-level types and are not merely
aliases for C++ types.

## Collections

Collections use square-bracket syntax:

```text
[T]
```

Examples:

```carbide
[i32]
[u8]
[string]
```

Variable example:

```carbide
numbers: [i32] = [1, 2, 3, 4, 5]
```

Function example:

```carbide
sum: (values: [i32]) -> i32 {
    ...
}
```

The exact collection semantics and available operations are still under
development.

## Type Philosophy

Carbide avoids relying on implementation-dependent primitive types such
as C++ `int`.

For example:

```carbide
x: i32 = 42
```

is explicit about the intended integer width.

This makes the source language independent from the platform-specific
width of C++ fundamental types.
