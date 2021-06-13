##### Map `for`

```v
m := map{
	'one': 1
	'two': 2
}
for key, value in m {
	println('$key -> $value')
	// Output: one -> 1
	//         two -> 2
}
```

Either key or value can be ignored by using a single underscore as the identifier.
```v
m := map{
	'one': 1
	'two': 2
}
// iterate over keys
for key, _ in m {
	println(key)
	// Output: one
	//         two
}
// iterate over values
for _, value in m {
	println(value)
	// Output: 1
	//         2
}
```

