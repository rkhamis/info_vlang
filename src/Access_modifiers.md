### Access modifiers

Struct fields are private and immutable by default (making structs immutable as well).
Their access modifiers can be changed with
`pub` and `mut`. In total, there are 5 possible options:

```v
struct Foo {
	a int // private immutable (default)
mut:
	b int // private mutable
	c int // (you can list multiple fields with the same access modifier)
pub:
	d int // public immutable (readonly)
pub mut:
	e int // public, but mutable only in parent module
__global:
	// (not recommended to use, that's why the 'global' keyword starts with __)
	f int // public and mutable both inside and outside parent module
}
```

For example, here's the `string` type defined in the `builtin` module:

```v ignore
struct string {
    str &byte
pub:
    len int
}
```

It's easy to see from this definition that `string` is an immutable type.
The byte pointer with the string data is not accessible outside `builtin` at all.
The `len` field is public, but immutable:
```v failcompile
fn main() {
	str := 'hello'
	len := str.len // OK
	str.len++ // Compilation error
}
```

This means that defining public readonly fields is very easy in V,
no need in getters/setters or properties.

