### `init` functions

If you want a module to automatically call some setup/initialization code when it is imported,
you can use a module `init` function:

```v
fn init() {
	// your setup code here ...
}
```

The `init` function cannot be public - it will be called automatically. This feature is
particularly useful for initializing a C library.

