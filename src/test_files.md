### Test files

```v
// hello.v
module main

fn hello() string {
	return 'Hello world'
}

fn main() {
	println(hello())
}
```

```v failcompile
module main

// hello_test.v
fn test_hello() {
	assert hello() == 'Hello world'
}
```
To run the test above, use `v hello_test.v`. This will check that the function `hello` is
producing the correct output. V executes all test functions in the file.

* All test functions have to be inside a test file whose name ends in `_test.v`.
* Test function names must begin with `test_` to mark them for execution.
* Normal functions can also be defined in test files, and should be called manually. Other
  symbols can also be defined in test files e.g. types.
* There are two kinds of tests: external and internal.
* Internal tests must *declare* their module, just like all other .v
files from the same module. Internal tests can even call private functions in
the same module.
* External tests must *import* the modules which they test. They do not
have access to the private functions/types of the modules. They can test only
the external/public API that a module provides.

In the example above, `test_hello` is an internal test, that can call
the private function `hello()` because `hello_test.v` has `module main`,
just like `hello.v`, i.e. both are part of the same module. Note also that
since `module main` is a regular module like the others, internal tests can
be used to test private functions in your main program .v files too.

You can also define special test functions in a test file:
* `testsuite_begin` which will be run *before* all other test functions.
* `testsuite_end` which will be run *after* all other test functions.

If a test function has an error return type, any propagated errors will fail the test:

```
import strconv

fn test_atoi() ? {
	assert strconv.atoi('1') ? == 1
	assert strconv.atoi('one') ? == 1 // test will fail
}
```

