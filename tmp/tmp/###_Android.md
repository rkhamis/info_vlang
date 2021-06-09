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

