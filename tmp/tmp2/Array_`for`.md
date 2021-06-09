##### Array `for`

```v
numbers := [1, 2, 3, 4, 5]
for num in numbers {
	println(num)
}
names := ['Sam', 'Peter']
for i, name in names {
	println('$i) $name')
	// Output: 0) Sam
	//         1) Peter
}
```

The `for value in arr` form is used for going through elements of an array.
If an index is required, an alternative form `for index, value in arr` can be used.

Note, that the value is read-only.
If you need to modify the array while looping, you need to declare the element as mutable:

```v
mut numbers := [0, 1, 2]
for mut num in numbers {
	num++
}
println(numbers) // [1, 2, 3]
```
When an identifier is just a single underscore, it is ignored.

