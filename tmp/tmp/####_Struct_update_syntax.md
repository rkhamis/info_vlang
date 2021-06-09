#### Struct update syntax

V makes it easy to return a modified version of an object:

```v
struct User {
	name          string
	age           int
	is_registered bool
}

fn register(u User) User {
	return {
		...u
		is_registered: true
	}
}

mut user := User{
	name: 'abc'
	age: 23
}
user = register(user)
println(user)
```

