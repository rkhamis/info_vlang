### Heap structs

Structs are allocated on the stack. To allocate a struct on the heap
and get a reference to it, use the `&` prefix:

```v
struct Point {
	x int
	y int
}

p := &Point{10, 10}
// References have the same syntax for accessing fields
println(p.x)
```

The type of `p` is `&Point`. It's a [reference](#references) to `Point`.
References are similar to Go pointers and C++ references.

