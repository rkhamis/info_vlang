#### $tmpl for embedding and parsing V template files

V has a simple template language for text and html templates, and they can easily
be embedded via `$tmpl('path/to/template.txt')`:


```v ignore
fn build() string {
	name := 'Peter'
	age := 25
	numbers := [1, 2, 3]
	return $tmpl('1.txt')
}

fn main() {
	println(build())
}
```

1.txt:

```
name: @name

age: @age

numbers: @numbers

@for number in numbers
  @number
@end
```

output:

```
name: Peter

age: 25

numbers: [1, 2, 3]

1
2
3
```




