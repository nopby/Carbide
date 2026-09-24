# Modules

## Imports

Modules are imported using `import`:

```carbide
import std
```

Imported names remain explicitly qualified:

```carbide
std::println("Hello")
```

## The use Declaration

The `use` declaration is intentionally not part of the initial language
specification.

This distinction may be revisited later if Carbide needs a mechanism
for bringing individual names into the current scope.
