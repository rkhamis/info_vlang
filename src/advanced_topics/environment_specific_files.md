### Environment specific files

If a file has an environment-specific suffix, it will only be compiled for that environment.

- `.js.v` => will be used only by the JS backend. These files can contain JS. code.
- `.c.v` => will be used only by the C backend. These files can contain C. code.
- `.native.v` => will be used only by V's native backend.
- `_nix.c.v` => will be used only on Unix systems (non Windows).
- `_${os}.c.v` => will be used only on the specific `os` system.
For example, `_windows.c.v` will be used only when compiling on Windows, or with `-os windows`.
- `_default.c.v` => will be used only if there is NOT a more specific platform file.
For example, if you have both `file_linux.c.v` and `file_default.c.v`,
and you are compiling for linux, then only `file_linux.c.v` will be used,
and `file_default.c.v` will be ignored.

Here is a more complete example:
main.v:
```v ignore
module main
fn main() { println(message) }
```

main_default.c.v:
```v ignore
module main
const ( message = 'Hello world' )
```

main_linux.c.v:
```v ignore
module main
const ( message = 'Hello linux' )
```

main_windows.c.v:
```v ignore
module main
const ( message = 'Hello windows' )
```

With the example above:
- when you compile for windows, you will get 'Hello windows'
- when you compile for linux, you will get 'Hello linux'
- when you compile for any other platform, you will get the
non specific 'Hello world' message.

- `_d_customflag.v` => will be used *only* if you pass `-d customflag` to V.
That corresponds to `$if customflag ? {}`, but for a whole file, not just a
single block. `customflag` should be a snake_case identifier, it can not
contain arbitrary characters (only lower case latin letters + numbers + `_`).
NB: a combinatorial `_d_customflag_linux.c.v` postfix will not work.
If you do need a custom flag file, that has platform dependent code, use the
postfix `_d_customflag.v`, and then use plaftorm dependent compile time
conditional blocks inside it, i.e. `$if linux {}` etc.

- `_notd_customflag.v` => similar to _d_customflag.v, but will be used
*only* if you do NOT pass `-d customflag` to V.

