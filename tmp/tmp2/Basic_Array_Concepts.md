#### Basic Array Concepts
Arrays are collections of data elements of the same type. They can be represented by
a list of elements surrounded by brackets. The elements can be accessed by appending
an *index* (starting with `0`) in brackets to the array variable:
```v
mut nums := [1, 2, 3]
println(nums) // `[1, 2, 3]`
println(nums[0]) // `1`
println(nums[1]) // `2`
nums[1] = 5
println(nums) // `[1, 5, 3]`
```
