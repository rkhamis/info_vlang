#### $if
```v
// Support for multiple conditions in one branch
$if ios || android {
	println('Running on a mobile device!')
}
$if linux && x64 {
	println('64-bit Linux.')
}
// Usage as expression
os := $if windows { 'Windows' } $else { 'UNIX' }
println('Using $os')
// $else-$if branches
$if tinyc {
	println('tinyc')
} $else $if clang {
	println('clang')
} $else $if gcc {
	println('gcc')
} $else {
	println('different compiler')
}
$if test {
	println('testing')
}
// v -cg ...
$if debug {
	println('debugging')
}
// v -prod ...
$if prod {
	println('production build')
}
// v -d option ...
$if option ? {
	println('custom option')
}
```

If you want an `if` to be evaluated at compile time it must be prefixed with a `$` sign.
Right now it can be used to detect an OS, compiler, platform or compilation options.
`$if debug` is a special option like `$if windows` or `$if x32`.
If you're using a custom ifdef, then you do need `$if option ? {}` and compile with`v -d option`.
Full list of builtin options:
| OS                            | Compilers         | Platforms             | Other                     |
| ---                           | ---               | ---                   | ---                       |
| `windows`, `linux`, `macos`   | `gcc`, `tinyc`    | `amd64`, `arm64`      | `debug`, `prod`, `test`   |
| `mac`, `darwin`, `ios`,       | `clang`, `mingw`  | `x64`, `x32`          | `js`, `glibc`, `prealloc` |
| `android`,`mach`, `dragonfly` | `msvc`            | `little_endian`       | `no_bounds_checking`, `freestanding`    |
| `gnu`, `hpux`, `haiku`, `qnx` | `cplusplus`       | `big_endian`          |
| `solaris` | | | |

