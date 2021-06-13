#### Interface method definitions

Also unlike Go, an interface may implement a method.
These methods are not implemented by structs which implement that interface.

When a struct is wrapped in an interface that has implemented a method
with the same name as one implemented by this struct, only the method
implemented on the interface is called.

```v
struct Cat {}

fn (c Cat) speak() string {
	return 'meow!'
}

interface Adoptable {}

fn (a Adoptable) speak() string {
	return 'adopt me!'
}

fn new_adoptable() Adoptable {
	return Cat{}
}

fn main() {
	cat := Cat{}
	assert cat.speak() == 'meow!'
	a := new_adoptable()
	assert a.speak() == 'adopt me!'
	if a is Cat {
		println(a.speak()) // meow!
	}
}
```

