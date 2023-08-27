# Musializer-windows
This repository will only be releasing musializer compiled on Windows 10 x86-64.

# Compiling on Windows
1. Install MSYS2
2. Install `clang` `mingw-w64-x86_64-raylib` `mingw-w64-x86_64-glfw` and `pkg-config`
3. Set the `PKG_CONFIG_PATH` to find the `/mingw64/lib/pkgconfig` by running this command `PKG_CONFIG_PATH=$PKG_CONFIG_PATH:/mingw64/lib/pkgconfig/`
4. Compile the program with `./build.sh`
5. Copy both shaders folder and fonts folder to the path where executable was built.
6. Copy these dlls from `/mingw64/bin` to the path where executable was built.
   1. `glfw3.dll`
   2. `libgcc_s_seh-1.dll`
   3. `libraylib.dll`
   4. `libwinpthread-1.dll`
7. Copy `msys-2.0.dll` from `/usr/bin` to the path where executable was built.
8. Enter the path where executable was built, then make a new copy of `libgcc_s_seh-1.dll`, after that then rename that new `libgcc_s_seh-1.dll` to `msys-gcc_s-seh-1.dll`
9. Enjoy!
