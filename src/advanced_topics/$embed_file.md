#### $embed_file

```v ignore
import os
fn main() {
	embedded_file := $embed_file('v.png')
	os.write_file('exported.png', embedded_file.to_string()) ?
}
```

V can embed arbitrary files into the executable with the `$embed_file(<path>)`
compile time call. Paths can be absolute or relative to the source file.

When you do not use `-prod`, the file will not be embedded. Instead, it will
be loaded *the first time* your program calls `f.data()` at runtime, making
it easier to change in external editor programs, without needing to recompile
your executable.

When you compile with `-prod`, the file *will be embedded inside* your
executable, increasing your binary size, but making it more self contained
and thus easier to distribute. In this case, `f.data()` will cause *no IO*,
and it will always return the same data.

