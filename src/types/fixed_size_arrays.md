### Fixed size arrays

V also supports arrays with fixed size. Unlike ordinary arrays, their
length is constant. You cannot append elements to them, nor shrink them.
You can only modify their elements in place.

However, access to the elements of fixed size arrays is more efficient,
they need less memory than ordinary arrays, and unlike ordinary arrays,
their data is on the stack, so you may want to use them as buffers if you
do not want additional heap allocations.

Most methods are defined to work on ordinary arrays, not on fixed size arrays.
You can convert a fixed size array to an ordinary array with slicing:
```v
mut fnums := [3]int{} // fnums is a fixed size array with 3 elements.
fnums[0] = 1
fnums[1] = 10
fnums[2] = 100
println(fnums) // => [1, 10, 100]
println(typeof(fnums).name) // => [3]int

fnums2 := [1, 10, 100]! // short init syntax that does the same (the syntax will probably change)

anums := fnums[0..fnums.len]
println(anums) // => [1, 10, 100]
println(typeof(anums).name) // => []int
```
Note that slicing will cause the data of the fixed size array to be copied to
the newly created ordinary array.

