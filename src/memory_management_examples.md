### Examples

```v
import strings

fn draw_text(s string, x int, y int) {
	// ...
}

fn draw_scene() {
	// ...
	name1 := 'abc'
	name2 := 'def ghi'
	draw_text('hello $name1', 10, 10)
	draw_text('hello $name2', 100, 10)
	draw_text(strings.repeat(`X`, 10000), 10, 50)
	// ...
}
```

The strings don't escape `draw_text`, so they are cleaned up when
the function exits.

In fact, with the `-prealloc` flag, the first two calls won't result in any allocations at all.
These two strings are small, so V will use a preallocated buffer for them.

```v
struct User {
	name string
}

fn test() []int {
	number := 7 // stack variable
	user := User{} // struct allocated on stack
	numbers := [1, 2, 3] // array allocated on heap, will be freed as the function exits
	println(number)
	println(user)
	println(numbers)
	numbers2 := [4, 5, 6] // array that's being returned, won't be freed here
	return numbers2
}
```

