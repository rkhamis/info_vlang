### Maps

```v
mut m := map[string]int{} // a map with `string` keys and `int` values
m['one'] = 1
m['two'] = 2
println(m['one']) // "1"
println(m['bad_key']) // "0"
println('bad_key' in m) // Use `in` to detect whether such key exists
m.delete('two')
```
Maps can have keys of type string, rune, integer, float or voidptr.

The whole map can be initialized using this short syntax:
```v
numbers := map{
	'one': 1
	'two': 2
}
println(numbers)
```

If a key is not found, a zero value is returned by default:

```v
sm := map{
	'abc': 'xyz'
}
val := sm['bad_key']
println(val) // ''
```
```v
intm := map{
	1: 1234
	2: 5678
}
s := intm[3]
println(s) // 0
```

It's also possible to use an `or {}` block to handle missing keys:

```v
mm := map[string]int{}
val := mm['bad_key'] or { panic('key not found') }
```

The same optional check applies to arrays:

```v
arr := [1, 2, 3]
large_index := 999
val := arr[large_index] or { panic('out of bounds') }
```

