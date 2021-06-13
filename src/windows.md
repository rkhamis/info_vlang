### Windows:
You need `git`, and a C compiler like `tcc`, `gcc`, `clang` or `msvc`:
```bash
git clone https://github.com/vlang/v
cd v
make.bat -tcc
```
NB: You can also pass one of `-gcc`, `-msvc`, `-clang` to `make.bat` instead,
if you do prefer to use a different C compiler, but -tcc is small, fast, and
easy to install (V will download a prebuilt binary automatically).

It is recommended to add this folder to the PATH of your environment variables.
This can be done with the command `v.exe symlink`.

