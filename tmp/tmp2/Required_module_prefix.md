### Required module prefix

When naming constants, `snake_case` must be used. In order to distinguish consts
from local variables, the full path to consts must be specified. For example,
to access the PI const, full `math.pi` name must be used both outside the `math`
module, and inside it. That restriction is relaxed only for the `main` module
(the one containing your `fn main()`), where you can use the unqualified name of
constants defined there, i.e. `numbers`, rather than `main.numbers`.

vfmt takes care of this rule, so you can type `println(pi)` inside the `math` module,
and vfmt will automatically update it to `println(math.pi)`.

<!--
Many people prefer all caps consts: `TOP_CITIES`. This wouldn't work
well in V, because consts are a lot more powerful than in other languages.
They can represent complex structures, and this is used quite often since there
are no globals:

```v oksyntax
println('Top cities: ${top_cities.filter(.usa)}')
```
-->

