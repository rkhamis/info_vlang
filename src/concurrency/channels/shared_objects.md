### Shared Objects

Data can be exchanged between a coroutine and the calling thread via a shared variable.
Such variables should be created as `shared` and passed to the coroutine as such, too.
The underlying `struct` contains a hidden *mutex* that allows locking concurrent access
using `rlock` for read-only and `lock` for read/write access.

```v
struct St {
mut:
	x int // data to shared
}

fn (shared b St) g() {
	lock b {
		// read/modify/write b.x
	}
}

fn main() {
	shared a := St{
		x: 10
	}
	go a.g()
	// ...
	rlock a {
		// read a.x
	}
}
```
Shared variables must be structs, arrays or maps.

