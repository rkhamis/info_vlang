#### Casting an interface

We can test the underlying type of an interface using dynamic cast operators:
```v oksyntax
interface Something {}

fn announce(s Something) {
	if s is Dog {
		println('a $s.breed dog') // `s` is automatically cast to `Dog` (smart cast)
	} else if s is Cat {
		println('a $s.breed cat')
	} else {
		println('something else')
	}
}
```
For more information, see [Dynamic casts](#dynamic-casts).

