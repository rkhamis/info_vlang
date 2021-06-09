#### Running tests

To run test functions in an individual test file, use `v foo_test.v`.

To test an entire module, use `v test mymodule`. You can also use `v test .` to test
everything inside your current folder (and subfolders). You can pass the `-stats`
option to see more details about the individual tests run.

You can put additional test data, including .v source files in a folder, named
`testdata`, right next to your _test.v files. V's test framework will *ignore*
such folders, while scanning for tests to run. This is usefull, if you want to
put .v files with invalid V source code, or other tests, including known 
failing ones, that should be run in a specific way/options by a parent _test.v 
file.

NB: the path to the V compiler, is available through @VEXE, so a _test.v
file, can easily run *other* test files like this:
```v oksyntax
import os

fn test_subtest() {
	res := os.execute('${@VEXE} other_test.v')
	assert res.exit_code == 1
	assert res.output.contains('other_test.v does not exist')
}
```

