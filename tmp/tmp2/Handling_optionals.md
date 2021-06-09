### Handling optionals

There are four ways of handling an optional. The first method is to
propagate the error:

```v
import net.http

fn f(url string) ?string {
	resp := http.get(url) ?
	return resp.text
}
```

`http.get` returns `?http.Response`. Because `?` follows the call, the
error will be propagated to the caller of `f`. When using `?` after a
function call producing an optional, the enclosing function must return
an optional as well. If error propagation is used in the `main()`
function it will `panic` instead, since the error cannot be propagated
any further.

The body of `f` is essentially a condensed version of:

```v ignore
    resp := http.get(url) or { return err }
    return resp.text
```

---
The second method is to break from execution early:

```v oksyntax
user := repo.find_user_by_id(7) or { return }
```

Here, you can either call `panic()` or `exit()`, which will stop the execution of the
entire program, or use a control flow statement (`return`, `break`, `continue`, etc)
to break from the current block.
Note that `break` and `continue` can only be used inside a `for` loop.

V does not have a way to forcibly "unwrap" an optional (as other languages do,
for instance Rust's `unwrap()` or Swift's `!`). To do this, use `or { panic(err.msg) }` instead.

---
The third method is to provide a default value at the end of the `or` block.
In case of an error, that value would be assigned instead,
so it must have the same type as the content of the `Option` being handled.

```v
fn do_something(s string) ?string {
	if s == 'foo' {
		return 'foo'
	}
	return error('invalid string') // Could be `return none` as well
}

a := do_something('foo') or { 'default' } // a will be 'foo'
b := do_something('bar') or { 'default' } // b will be 'default'
println(a)
println(b)
```

---
The fourth method is to use `if` unwrapping:

```v
import net.http

if resp := http.get('https://google.com') {
	println(resp.text) // resp is a http.Response, not an optional
} else {
	println(err)
}
```
Above, `http.get` returns a `?http.Response`. `resp` is only in scope for the first
`if` branch. `err` is only in scope for the `else` branch.

