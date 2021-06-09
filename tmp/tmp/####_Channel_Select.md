#### Channel Select

The `select` command allows monitoring several channels at the same time
without noticeable CPU load.  It consists of a list of possible transfers and associated branches
of statements - similar to the [match](#match) command:
```v
import time

fn main() {
	ch := chan f64{}
	ch2 := chan f64{}
	ch3 := chan f64{}
	mut b := 0.0
	c := 1.0
	// ... setup go threads that will send on ch/ch2
	go fn (the_channel chan f64) {
		time.sleep(5 * time.millisecond)
		the_channel <- 1.0
	}(ch)
	go fn (the_channel chan f64) {
		time.sleep(1 * time.millisecond)
		the_channel <- 1.0
	}(ch2)
	go fn (the_channel chan f64) {
		_ := <-the_channel
	}(ch3)
	//
	select {
		a := <-ch {
			// do something with `a`
			eprintln('> a: $a')
		}
		b = <-ch2 {
			// do something with predeclared variable `b`
			eprintln('> b: $b')
		}
		ch3 <- c {
			// do something if `c` was sent
			time.sleep(5 * time.millisecond)
			eprintln('> c: $c was send on channel ch3')
		}
		> 500 * time.millisecond {
			// do something if no channel has become ready within 0.5s
			eprintln('> more than 0.5s passed without a channel being ready')
		}
	}
	eprintln('> done')
}
```

The timeout branch is optional. If it is absent `select` waits for an unlimited amount of time.
It is also possible to proceed immediately if no channel is ready in the moment `select` is called
by adding an `else { ... }` branch. `else` and `> timeout` are mutually exclusive.

The `select` command can be used as an *expression* of type `bool`
that becomes `false` if all channels are closed:
```v wip
if select {
    ch <- a {
        // ...
    }
} {
    // channel was open
} else {
    // channel is closed
}
```

