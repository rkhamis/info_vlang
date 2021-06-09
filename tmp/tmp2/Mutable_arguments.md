### Mutable arguments

It is possible to modify function arguments by using the keyword `mut`:

```v
struct User {
	name string
mut:
	is_registered bool
}

fn (mut u User) register() {
	u.is_registered = true
}

mut user := User{}
println(user.is_registered) // "false"
user.register()
println(user.is_registered) // "true"
```

In this example, the receiver (which is simply the first argument) is marked as mutable,
so `register()` can change the user object. The same works with non-receiver arguments:

```v
fn multiply_by_2(mut arr []int) {
	for i in 0 .. arr.len {
		arr[i] *= 2
	}
}

mut nums := [1, 2, 3]
multiply_by_2(mut nums)
println(nums)
// "[2, 4, 6]"
```

Note, that you have to add `mut` before `nums` when calling this function. This makes
it clear that the function being called will modify the value.

It is preferable to return values instead of modifying arguments.
Modifying arguments should only be done in performance-critical parts of your application
to reduce allocations and copying.

For this reason V doesn't allow the modification of arguments with primitive types (e.g. integers).
Only more complex types such as arrays and maps may be modified.

Use `user.register()` or `user = register(user)`
instead of `register(mut user)`.

