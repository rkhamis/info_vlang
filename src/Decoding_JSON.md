## Decoding JSON

```v
import json

struct Foo {
	x int
}

struct User {
	name string
	age  int
	// Use the `skip` attribute to skip certain fields
	foo Foo [skip]
	// If the field name is different in JSON, it can be specified
	last_name string [json: lastName]
}

data := '{ "name": "Frodo", "lastName": "Baggins", "age": 25 }'
user := json.decode(User, data) or {
	eprintln('Failed to decode json')
	return
}
println(user.name)
println(user.last_name)
println(user.age)
// You can also decode JSON arrays:
sfoos := '[{"x":123},{"x":456}]'
foos := json.decode([]Foo, sfoos) ?
println(foos[0].x)
println(foos[1].x)
```

Because of the ubiquitous nature of JSON, support for it is built directly into V.

The `json.decode` function takes two arguments:
the first is the type into which the JSON value should be decoded and
the second is a string containing the JSON data.

V generates code for JSON encoding and decoding.
No runtime reflection is used. This results in much better performance.

