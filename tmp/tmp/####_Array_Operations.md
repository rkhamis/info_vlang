#### Array Operations

Elements can be appended to the end of an array using the push operator `<<`.
It can also append an entire array.

```v
mut nums := [1, 2, 3]
nums << 4
println(nums) // "[1, 2, 3, 4]"
// append array
nums << [5, 6, 7]
println(nums) // "[1, 2, 3, 4, 5, 6, 7]"
mut names := ['John']
names << 'Peter'
names << 'Sam'
// names << 10  <-- This will not compile. `names` is an array of strings.
```

`val in array` returns true if the array contains `val`. See [`in` operator](#in-operator).

```v
names := ['John', 'Peter', 'Sam']
println(names.len) // "3"
println('Alex' in names) // "false"
```


