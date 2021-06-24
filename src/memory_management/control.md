### Control

You can take advantage of V's autofree engine and define a `free()` method on custom
data types:

```v
struct MyType {}

[unsafe]
fn (data &MyType) free() {
	// ...
}
```

Just as the compiler frees C data types with C's `free()`, it will statically insert
`free()` calls for your data type at the end of each variable's lifetime.

For developers willing to have more low level control, autofree can be disabled with
`-manualfree`, or by adding a `[manualfree]` on each function that wants manage its
memory manually. (See [attributes](#attributes)).

_Note: right now autofree is hidden behind the -autofree flag. It will be enabled by
default in V 0.3. If autofree is not used, V programs will leak memory._

further reading:
- [Examples](memory_management_examples)