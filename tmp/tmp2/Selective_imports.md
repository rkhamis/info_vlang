### Selective imports

You can also import specific functions and types from modules directly:

```v
import os { input }

fn main() {
	// read text from stdin
	name := input('Enter your name: ')
	println('Hello, $name!')
}
```
Note: This is not allowed for constants - they must always be prefixed.

You can import several specific symbols at once:

```v
import os { input, user_os }

name := input('Enter your name: ')
println('Name: $name')
os := user_os()
println('Your OS is ${os}.')
```

