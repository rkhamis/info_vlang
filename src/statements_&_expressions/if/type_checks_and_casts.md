#### Type checks and casts
You can check the current type of a sum type using `is` and its negated form `!is`.

You can do it either in an `if`:
```v
struct Abc {
	val string
}

struct Xyz {
	foo string
}

type Alphabet = Abc | Xyz

x := Alphabet(Abc{'test'}) // sum type
if x is Abc {
	// x is automatically casted to Abc and can be used here
	println(x)
}
if x !is Abc {
	println('Not Abc')
}
```
or using `match`:
```v oksyntax
match x {
	Abc {
		// x is automatically casted to Abc and can be used here
		println(x)
	}
	Xyz {
		// x is automatically casted to Xyz and can be used here
		println(x)
	}
}
```

This works also with struct fields:
```v
struct MyStruct {
	x int
}

struct MyStruct2 {
	y string
}

type MySumType = MyStruct | MyStruct2

struct Abc {
	bar MySumType
}

x := Abc{
	bar: MyStruct{123} // MyStruct will be converted to MySumType type automatically
}
if x.bar is MyStruct {
	// x.bar is automatically casted
	println(x.bar)
}
match x.bar {
	MyStruct {
		// x.bar is automatically casted
		println(x.bar)
	}
	else {}
}
```

Mutable variables can change, and doing a cast would be unsafe.
However, sometimes it's useful to type cast despite mutability.
In such cases the developer must mark the expression with the `mut` keyword
to tell the compiler that they know what they're doing.

It works like this:
```v oksyntax
mut x := MySumType(MyStruct{123})
if mut x is MyStruct {
	// x is casted to MyStruct even if it's mutable
	// without the mut keyword that wouldn't work
	println(x)
}
// same with match
match mut x {
	MyStruct {
		// x is casted to MyStruct even it's mutable
		// without the mut keyword that wouldn't work
		println(x)
	}
}
```

