### Including C code

You can also include C code directly in your V module.
For example, let's say that your C code is located in a folder named 'c' inside your module folder.
Then:

* Put a v.mod file inside the toplevel folder of your module (if you
created your module with `v new` you already have v.mod file). For
example:
```v ignore
Module {
	name: 'mymodule',
	description: 'My nice module wraps a simple C library.',
	version: '0.0.1'
	dependencies: []
}
```


* Add these lines to the top of your module:
```v oksyntax
#flag -I @VMODROOT/c
#flag @VMODROOT/c/implementation.o
#include "header.h"
```
NB: @VMODROOT will be replaced by V with the *nearest parent folder, where there is a v.mod file*.
Any .v file beside or below the folder where the v.mod file is,
can use `#flag @VMODROOT/abc` to refer to this folder.
The @VMODROOT folder is also *prepended* to the module lookup path,
so you can *import* other modules under your @VMODROOT, by just naming them.

The instructions above will make V look for an compiled .o file in
your module `folder/c/implementation.o`.
If V finds it, the .o file will get linked to the main executable, that used the module.
If it does not find it, V assumes that there is a `@VMODROOT/c/implementation.c` file,
and tries to compile it to a .o file, then will use that.

This allows you to have C code, that is contained in a V module, so that its distribution is easier.
You can see a complete minimal example for using C code in a V wrapper module here:
[project_with_c_code](https://github.com/vlang/v/tree/master/vlib/v/tests/project_with_c_code).
Another example, demonstrating passing structs from C to V and back again:
[interoperate between C to V to C](https://github.com/vlang/v/tree/master/vlib/v/tests/project_with_c_code_2).

