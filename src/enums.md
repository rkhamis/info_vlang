### Enums

```v
enum Color {
	red
	green
	blue
}

mut color := Color.red
// V knows that `color` is a `Color`. No need to use `color = Color.green` here.
color = .green
println(color) // "green"
match color {
	.red { println('the color was red') }
	.green { println('the color was green') }
	.blue { println('the color was blue') }
}
```

Enum match must be exhaustive or have an `else` branch.
This ensures that if a new enum field is added, it's handled everywhere in the code.

Enum fields cannot re-use reserved keywords. However, reserved keywords may be escaped
with an @.

```v
enum Color {
	@none
	red
	green
	blue
}

color := Color.@none
println(color)
```

Integers may be assigned to enum fields.

```v
enum Grocery {
	apple
	orange = 5
	pear
}

g1 := int(Grocery.apple)
g2 := int(Grocery.orange)
g3 := int(Grocery.pear)
println('Grocery IDs: $g1, $g2, $g3')
```

Output: `Grocery IDs: 0, 5, 6`.

Operations are not allowed on enum variables; they must be explicity cast to `int`.

