## Install from source
The major way to get the latest and greatest V, is to __install it from source__.
It is __easy__, and it usually takes __only a few seconds__.


### Linux, macOS, FreeBSD, etc:
You need `git`, and a C compiler like `tcc`, `gcc` or `clang`, and `make`:
```bash
git clone https://github.com/vlang/v
cd v
make
```

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

### Android
Running V graphical apps on Android is also possible via [vab](https://github.com/vlang/vab).

V Android dependencies: **V**, **Java JDK** >= 8, Android **SDK + NDK**.

  1. Install dependencies (see [vab](https://github.com/vlang/vab))
  2. Connect your Android device
  3. Run:
  ```bash
  git clone https://github.com/vlang/vab && cd vab && v vab.v
  ./vab --device auto run /path/to/v/examples/sokol/particles
  ```


For more details and troubleshooting, please visit the [vab GitHub repository](https://github.com/vlang/vab).


