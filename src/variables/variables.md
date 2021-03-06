## Variables

```v
name := 'Bob'
age := 20
large_number := i64(9999999999)
println(name)
println(age)
println(large_number)
```

Variables are declared and initialized with `:=`. This is the only
way to declare variables in V. This means that variables always have an initial
value.

The variable's type is inferred from the value on the right hand side.
To choose a different type, use type conversion:
the expression `T(v)` converts the value `v` to the
type `T`.

Unlike most other languages, V only allows defining variables in functions.
Global (module level) variables are not allowed. There's no global state in V
(see [Pure functions by default](#pure-functions-by-default) for details).

For consistency across different code bases, all variable and function names
must use the `snake_case` style, as opposed to type names, which must use `PascalCase`.

