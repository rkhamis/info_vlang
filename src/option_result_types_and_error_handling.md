### Option/Result types and error handling

Option types are declared with `?Type`:
```v
struct User {
	id   int
	name string
}

struct Repo {
	users []User
}

fn (r Repo) find_user_by_id(id int) ?User {
	for user in r.users {
		if user.id == id {
			// V automatically wraps this into an option type
			return user
		}
	}
	return error('User $id not found')
}

fn main() {
	repo := Repo{
		users: [User{1, 'Andrew'}, User{2, 'Bob'}, User{10, 'Charles'}]
	}
	user := repo.find_user_by_id(10) or { // Option types must be handled by `or` blocks
		return
	}
	println(user.id) // "10"
	println(user.name) // "Charles"
}
```

V combines `Option` and `Result` into one type, so you don't need to decide which one to use.

The amount of work required to "upgrade" a function to an optional function is minimal;
you have to add a `?` to the return type and return an error when something goes wrong.

If you don't need to return an error message, you can simply `return none`
(this is a more efficient equivalent of `return error("")`).

This is the primary mechanism for error handling in V. They are still values, like in Go,
but the advantage is that errors can't be unhandled, and handling them is a lot less verbose.
Unlike other languages, V does not handle exceptions with `throw/try/catch` blocks.

`err` is defined inside an `or` block and is set to the string message passed
to the `error()` function. `err` is empty if `none` was returned.

```v oksyntax
user := repo.find_user_by_id(7) or {
	println(err) // "User 7 not found"
	return
}
```