#### Condition `for`

```v
mut sum := 0
mut i := 0
for i <= 100 {
	sum += i
	i++
}
println(sum) // "5050"
```

This form of the loop is similar to `while` loops in other languages.
The loop will stop iterating once the boolean condition evaluates to false.
Again, there are no parentheses surrounding the condition, and the braces are always required.

