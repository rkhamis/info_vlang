#### $env

```v
module main

fn main() {
	compile_time_env := $env('ENV_VAR')
	println(compile_time_env)
}
```

V can bring in values at compile time from environment variables.
`$env('ENV_VAR')` can also be used in top-level `#flag` and `#include` statements:
`#flag linux -I $env('JAVA_HOME')/include`.

