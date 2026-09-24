# Variables

## Declaration

Variables use:

```text
name: type = value
```

Example:

```carbide
x: i32 = 10
```

## Immutability

Variables are immutable by default.

```carbide
x: i32 = 10

// x = 20
```

Mutable variables explicitly use `mut`:

```carbide
mut x: i32 = 10
x = 20
```

This makes mutation visible at the declaration site.

## Type Inference

Type inference may be supported where the initializer provides enough
information to determine the type.

For example:

```carbide
x := 10
```

The exact syntax and rules for type inference are not yet part of the
initial specification.
