#### Syntax and Usage
Channels have the type `chan objtype`. An optional buffer length can specified as the `cap` property
in the declaration:

```v
ch := chan int{} // unbuffered - "synchronous"
ch2 := chan f64{cap: 100} // buffer length 100
```

Channels do not have to be declared as `mut`. The buffer length is not part of the type but
a property of the individual channel object. Channels can be passed to coroutines like normal
variables:

```v
fn f(ch chan int) {
	// ...
}

fn main() {
	ch := chan int{}
	go f(ch)
	// ...
}
```

Objects can be pushed to channels using the arrow operator. The same operator can be used to
pop objects from the other end:

```v
// make buffered channels so pushing does not block (if there is room in the buffer)
ch := chan int{cap: 1}
ch2 := chan f64{cap: 1}
n := 5
// push
ch <- n
ch2 <- 7.3
mut y := f64(0.0)
m := <-ch // pop creating new variable
y = <-ch2 // pop into existing variable
```

A channel can be closed to indicate that no further objects can be pushed. Any attempt
to do so will then result in a runtime panic (with the exception of `select` and
`try_push()` - see below). Attempts to pop will return immediately if the
associated channel has been closed and the buffer is empty. This situation can be
handled using an or branch (see [Handling Optionals](#handling-optionals)).

```v wip
ch := chan int{}
ch2 := chan f64{}
// ...
ch.close()
// ...
m := <-ch or {
    println('channel has been closed')
}

// propagate error
y := <-ch2 ?
```

