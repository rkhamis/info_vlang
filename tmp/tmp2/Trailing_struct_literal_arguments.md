#### Trailing struct literal arguments

V doesn't have default function arguments or named arguments, for that trailing struct
literal syntax can be used instead:

```v
struct ButtonConfig {
	text        string
	is_disabled bool
	width       int = 70
	height      int = 20
}

struct Button {
	text   string
	width  int
	height int
}

fn new_button(c ButtonConfig) &Button {
	return &Button{
		width: c.width
		height: c.height
		text: c.text
	}
}

button := new_button(text: 'Click me', width: 100)
// the height is unset, so it's the default value
assert button.height == 20
```

As you can see, both the struct name and braces can be omitted, instead of:

```v oksyntax nofmt
new_button(ButtonConfig{text:'Click me', width:100})
```

This only works for functions that take a struct for the last argument.

