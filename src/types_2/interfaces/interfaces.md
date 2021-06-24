### Interfaces

```v
struct Dog {
	breed string
}

struct Cat {
	breed string
}

fn (d Dog) speak() string {
	return 'woof'
}

fn (c Cat) speak() string {
	return 'meow'
}

// unlike Go and like TypeScript, V's interfaces can define fields, not just methods.
interface Speaker {
	breed string
	speak() string
}

dog := Dog{'Leonberger'}
cat := Cat{'Siamese'}

mut arr := []Speaker{}
arr << dog
arr << cat
for item in arr {
	println('a $item.breed says: $item.speak()')
}
```

A type implements an interface by implementing its methods and fields.
There is no explicit declaration of intent, no "implements" keyword.

