### C Declarations

C identifiers are accessed with the `C` prefix similarly to how module-specific
identifiers are accessed. Functions must be redeclared in V before they can be used.
Any C types may be used behind the `C` prefix, but types must be redeclared in V in
order to access type members.

To redeclare complex types, such as in the following C code:

```c
struct SomeCStruct {
	uint8_t implTraits;
	uint16_t memPoolData;
	union {
		struct {
			void* data;
			size_t size;
		};

		DataView view;
	};
};
```

members of sub-data-structures may be directly declared in the containing struct as below:

```v
struct C.SomeCStruct {
	implTraits  byte
	memPoolData u16
	// These members are part of sub data structures that can't currently be represented in V.
	// Declaring them directly like this is sufficient for access.
	// union {
	// struct {
	data voidptr
	size size_t
	// }
	view C.DataView
	// }
}
```

The existence of the data members is made known to V, and they may be used without
re-creating the original structure exactly.

Alternatively, you may [embed](#embedded-structs) the sub-data-structures to maintain
a parallel code structure.

