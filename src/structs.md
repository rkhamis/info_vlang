## Structs

```v
struct Point {
	x int
	y int
}

mut p := Point{
	x: 10
	y: 20
}
println(p.x) // Struct fields are accessed using a dot
// Alternative literal syntax for structs with 3 fields or fewer
p = Point{10, 20}
assert p.x == 10
```

