### String interpolation

Basic interpolation syntax is pretty simple - use `$` before a variable name.
The variable will be converted to a string and embedded into the literal:
```v
name := 'Bob'
println('Hello, $name!') // Hello, Bob!
```
It also works with fields: `'age = $user.age'`.
If you need more complex expressions, use `${}`: `'can register = ${user.age > 13}'`.

Format specifiers similar to those in C's `printf()` are also supported.
`f`, `g`, `x`, etc. are optional and specify the output format.
The compiler takes care of the storage size, so there is no `hd` or `llu`.

```v
x := 123.4567
println('x = ${x:4.2f}')
println('[${x:10}]') // pad with spaces on the left => [   123.457]
println('[${int(x):-10}]') // pad with spaces on the right => [123       ]
println('[${int(x):010}]') // pad with zeros on the left => [0000000123]
```

