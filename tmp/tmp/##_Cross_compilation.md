## Cross compilation

To cross compile your project simply run

```shell
v -os windows .
```

or

```shell
v -os linux .
```

(Cross compiling for macOS is temporarily not possible.)

If you don't have any C dependencies, that's all you need to do. This works even
when compiling GUI apps using the `ui` module or graphical apps using `gg`.

You will need to install Clang, LLD linker, and download a zip file with
libraries and include files for Windows and Linux. V will provide you with a link.

