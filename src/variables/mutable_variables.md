### Mutable variables

```v
mut age := 20
println(age)
age = 21
println(age)
```

To change the value of the variable use `=`. In V, variables are
immutable by default.
To be able to change the value of the variable, you have to declare it with `mut`.

Try compiling the program above after removing `mut` from the first line.

