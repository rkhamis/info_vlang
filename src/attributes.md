## Attributes

V has several attributes that modify the behavior of functions and structs.

An attribute is a compiler instruction specified inside `[]` right before a
function/struct/enum declaration and applies only to the following declaration.

```v
// Calling this function will result in a deprecation warning
[deprecated]
fn old_function() {
}

// It can also display a custom deprecation message
[deprecated: 'use new_function() instead']
fn legacy_function() {}

// This function's calls will be inlined.
[inline]
fn inlined_function() {
}

// The following struct must be allocated on the heap. Therefore, it can only be used as a
// reference (`&Window`) or inside another reference (`&OuterStruct{ Window{...} }`).
[heap]
struct Window {
}

// V will not generate this function and all its calls if the provided flag is false.
// To use a flag, use `v -d flag`
[if debug]
fn foo() {
}

fn bar() {
	foo() // will not be called if `-d debug` is not passed
}

// The memory pointed to by the pointer arguments of this function will not be
// freed by the garbage collector (if in use) before the function returns
[keep_args_alive]
fn C.my_external_function(voidptr, int, voidptr) int

// Calls to following function must be in unsafe{} blocks.
// Note that the code in the body of `risky_business()` will still be
// checked, unless you also wrap it in `unsafe {}` blocks.
// This is usefull, when you want to have an `[unsafe]` function that
// has checks before/after a certain unsafe operation, that will still
// benefit from V's safety features.
[unsafe]
fn risky_business() {
	// code that will be checked, perhaps checking pre conditions
	unsafe {
		// code that *will not be* checked, like pointer arithmetic,
		// accessing union fields, calling other `[unsafe]` fns, etc...
		// Usually, it is a good idea to try minimizing code wrapped
		// in unsafe{} as much as possible.
		// See also [Memory-unsafe code](#memory-unsafe-code)
	}
	// code that will be checked, perhaps checking post conditions and/or
	// keeping invariants
}

// V's autofree engine will not take care of memory management in this function.
// You will have the responsibility to free memory manually yourself in it.
[manualfree]
fn custom_allocations() {
}

// For C interop only, tells V that the following struct is defined with `typedef struct` in C
[typedef]
struct C.Foo {
}

// Used in Win32 API code when you need to pass callback function
[windows_stdcall]
fn C.DefWindowProc(hwnd int, msg int, lparam int, wparam int)

// Windows only:
// If a default graphics library is imported (ex. gg, ui), then the graphical window takes
// priority and no console window is created, effectively disabling println() statements.
// Use to explicity create console window. Valid before main() only.
[console]
fn main() {
}
```

