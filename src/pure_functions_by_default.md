### Pure functions by default

V functions are pure by default, meaning that their return values are a function of their
arguments only, and their evaluation has no side effects (besides I/O).

This is achieved by a lack of global variables and all function arguments being
immutable by default, even when [references](#references) are passed.

V is not a purely functional language however.

There is a compiler flag to enable global variables (`-enable-globals`), but this is
intended for low-level applications like kernels and drivers.

