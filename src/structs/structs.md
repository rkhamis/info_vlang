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


read further:
- [Heap Structs](heap_structs)
- [Embedded Structs](embedded_structs)
- [Default Field Values](default_field_values)
- [Required Fields](required_fields)
- [Short Struct Literal Syntax](short_struct_literal_syntax)
- [Trailing Struct Literal Arguments](trailing_struct_literal_arguments)
- [Access Modifiers](access_modifiers)
