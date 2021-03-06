#### Array methods

All arrays can be easily printed with `println(arr)` and converted to a string
with `s := arr.str()`.

Copying the data from the array is done with `.clone()`:

```v
nums := [1, 2, 3]
nums_copy := nums.clone()
```

Arrays can be efficiently filtered and mapped with the `.filter()` and
`.map()` methods:

```v
nums := [1, 2, 3, 4, 5, 6]
even := nums.filter(it % 2 == 0)
println(even) // [2, 4, 6]
// filter can accept anonymous functions
even_fn := nums.filter(fn (x int) bool {
	return x % 2 == 0
})
println(even_fn)
words := ['hello', 'world']
upper := words.map(it.to_upper())
println(upper) // ['HELLO', 'WORLD']
// map can also accept anonymous functions
upper_fn := words.map(fn (w string) string {
	return w.to_upper()
})
println(upper_fn) // ['HELLO', 'WORLD']
```

`it` is a builtin variable which refers to element currently being processed in filter/map methods.

Additionally, `.any()` and `.all()` can be used to conveniently test
for elements that satisfy a condition.

```v
nums := [1, 2, 3]
println(nums.any(it == 2)) // true
println(nums.all(it >= 2)) // false
```

There are further built in methods for arrays:
* `b := a.repeat(n)` concatenate `n` times the elements of `a`
* `a.insert(i, val)` insert new element `val` at index `i` and move all following elements upwards
* `a.insert(i, [3, 4, 5])` insert several elements
* `a.prepend(val)` insert value at beginning, equivalent to `a.insert(0, val)`
* `a.prepend(arr)` insert elements of array `arr` at beginning
* `a.trim(new_len)` truncate the length (if `new_length < a.len`, otherwise do nothing)
* `a.clear()` empty the array (without changing `cap`, equivalent to `a.trim(0)`)
* `v := a.first()` equivalent to `v := a[0]`
* `v := a.last()` equivalent to `v := a[a.len - 1]`
* `v := a.pop()` get last element and remove it from array
* `a.delete_last()` remove last element from array
* `b := a.reverse()` make `b` contain the elements of `a` in reversed order
* `a.reverse_in_place()` reverse the order of elements in `a`
* `a.join(joiner)` concatenate array of strings into a string using `joiner` string as a separator

