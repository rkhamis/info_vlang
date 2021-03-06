### Strings

```v
name := 'Bob'
println(name.len)
println(name[0]) // indexing gives a byte B
println(name[1..3]) // slicing gives a string 'ob'
windows_newline := '\r\n' // escape special characters like in C
assert windows_newline.len == 2
```

In V, a string is a read-only array of bytes. String data is encoded using UTF-8.
String values are immutable. You cannot mutate elements:

```v failcompile
mut s := 'hello 🌎'
s[0] = `H` // not allowed
```
> error: cannot assign to `s[i]` since V strings are immutable

Note that indexing a string will produce a `byte`, not a `rune`. Indexes correspond
to bytes in the string, not Unicode code points.

Character literals have type `rune`. To denote them, use `

```v
rocket := `🚀`
assert 'aloha!'[0] == `a`
```

Both single and double quotes can be used to denote strings. For consistency,
`vfmt` converts double quotes to single quotes unless the string contains a single quote character.

For raw strings, prepend `r`. Raw strings are not escaped:

```v
s := r'hello\nworld'
println(s) // "hello\nworld"
```

Strings can be easily converted to integers:

```v
s := '42'
n := s.int() // 42
```

