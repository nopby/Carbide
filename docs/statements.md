# Statements

## Semicolons

Carbide does not use semicolons to terminate statements.

## Newlines

Newlines separate statements when the syntax is unambiguous.

Newlines inside expressions do not terminate the expression when the
grammar clearly indicates that the expression continues.

```carbide
compute: () -> i32 {
    x: i32 = 10
    y: i32 = 20
    z: i32 = x + y

    return z
}
```
