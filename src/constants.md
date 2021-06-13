## Constants

```v
const (
	pi    = 3.14
	world = '世界'
)

println(pi)
println(world)
```

Constants are declared with `const`. They can only be defined
at the module level (outside of functions).
Constant values can never be changed. You can also declare a single
constant separately:

```v
const e = 2.71828
```

V constants are more flexible than in most languages. You can assign more complex values:

```v
struct Color {
	r int
	g int
	b int
}

fn rgb(r int, g int, b int) Color {
	return Color{
		r: r
		g: g
		b: b
	}
}

const (
	numbers = [1, 2, 3]
	red     = Color{
		r: 255
		g: 0
		b: 0
	}
	// evaluate function call at compile-time*
	blue = rgb(0, 0, 255)
)

println(numbers)
println(red)
println(blue)
```
\* WIP - for now function calls are evaluated at program start-up

Global variables are not normally allowed, so this can be really useful.

