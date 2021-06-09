### Short struct literal syntax

```v
struct Point {
	x int
	y int
}

mut p := Point{
	x: 10
	y: 20
}
// you can omit the struct name when it's already known
p = {
	x: 30
	y: 4
}
assert p.y == 4
//
// array: first element defines type of array
points := [Point{10, 20}, Point{20, 30}, Point{40, 50}]
println(points) // [Point{x: 10, y: 20}, Point{x: 20, y: 30}, Point{x: 40,y: 50}]
```

Omitting the struct name also works for returning a struct literal or passing one
as a function argument.

