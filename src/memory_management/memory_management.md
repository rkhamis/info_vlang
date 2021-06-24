## Memory management

V avoids doing unnecessary allocations in the first place by using value types,
string buffers, promoting a simple abstraction-free code style.

Most objects (~90-100%) are freed by V's autofree engine: the compiler inserts
necessary free calls automatically during compilation. Remaining small percentage
of objects is freed via reference counting.

The developer doesn't need to change anything in their code. "It just works", like in
Python, Go, or Java, except there's no heavy GC tracing everything or expensive RC for
each object.

further reading:
- [Control](control)
    - [Examples](memory_management_examples)