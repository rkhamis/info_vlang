#### Array Properties
There are two properties that control the "size" of an array:
* `len`: *length* - the number of defined elements of the array
* `cap`: *capacity* - the number of elements for which memory space has been reserved. The array can
grow up to this size without being reallocated. Usually, V takes care of
this property automatically but there are cases where the user may want to do manual
optimizations (see [below](#array-initialization)).

```v
mut nums := [1, 2, 3]
println(nums.len) // "3"
println(nums.cap) // "3" or greater
nums = [] // The array is now empty
println(nums.len) // "0"
```

Note that the properties are read-only fields and can't be modified by the user.

