## Builtin functions

Some functions are builtin like `println`. Here is the complete list:

```v ignore
fn print(s string) // print anything on sdtout
fn println(s string) // print anything and a newline on sdtout

fn eprint(s string) // same as print(), but use stderr
fn eprintln(s string) // same as println(), but use stderr

fn exit(code int) // terminate the program with a custom error code
fn panic(s string) // print a message and backtraces on stderr, and terminate the program with error code 1
fn print_backtrace() // print backtraces on stderr
```

`println` is a simple yet powerful builtin function, that can print anything:
strings, numbers, arrays, maps, structs.

```v
struct User {
	name string
	age  int
}

println(1) // "1"
println('hi') // "hi"
println([1, 2, 3]) // "[1, 2, 3]"
println(User{ name: 'Bob', age: 20 }) // "User{name:'Bob', age:20}"
```

<a id='custom-print-of-types' />

