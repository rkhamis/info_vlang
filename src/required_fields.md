### Required fields

```v
struct Foo {
	n int [required]
}
```

You can mark a struct field with the `[required]` attribute, to tell V that
that field must be initialized when creating an instance of that struct.

This example will not compile, since the field `n` isn't explicitly initialized:
```v failcompile
_ = Foo{}
```

<a id='short-struct-initialization-syntax' />

