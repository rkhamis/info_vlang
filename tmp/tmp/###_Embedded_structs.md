### Embedded structs

V doesn't allow subclassing, but it supports embedded structs:

```v
struct Widget {
mut:
	x int
	y int
}

struct Button {
	Widget
	title string
}

mut button := Button{
	title: 'Click me'
}
button.x = 3
```
Without embedding we'd have to name the `Widget` field and do:

```v oksyntax
button.widget.x = 3
```

