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
# WARNING
If you trying to rebuild again with your own modification, you may see error:
```c
$ ./build.sh
++ pkg-config --cflags raylib
+ CFLAGS='-Wall -Wextra -ggdb -I/mingw64/include'
++ pkg-config --libs raylib
++ pkg-config --libs glfw3
+ LIBS='-L/mingw64/lib -lraylib -L/mingw64/lib -lglfw3 -lm -ldl -lpthread'
+ mkdir -p ./build/
+ '[' '!' -z '' ']'
+ clang -Wall -Wextra -ggdb -I/mingw64/include -o ./build/musializer ./src/plug.c ./src/musializer.c -L/mingw64/lib -lraylib -L/mingw64/lib -lglfw3 -lm -ldl -lpthread -L./build/
/usr/lib/gcc/x86_64-pc-msys/11.3.0/../../../../x86_64-pc-msys/bin/ld: /usr/lib/gcc/x86_64-pc-msys/11.3.0/../../../../lib/crt0.o: in function `mainCRTStartup':
/c/S/B/src/msys2-runtime/winsup/cygwin/crt0.c:22:(.text+0xc): undefined reference to `msys_crt0'
/usr/lib/gcc/x86_64-pc-msys/11.3.0/../../../../x86_64-pc-msys/bin/ld: /c/S/B/src/msys2-runtime/winsup/cygwin/crt0.c:30:(.text+0x18): undefined reference to `cygwin_premain0'
/usr/lib/gcc/x86_64-pc-msys/11.3.0/../../../../x86_64-pc-msys/bin/ld: /c/S/B/src/msys2-runtime/winsup/cygwin/crt0.c:31:(.text+0x24): undefined reference to `cygwin_premain1'
/usr/lib/gcc/x86_64-pc-msys/11.3.0/../../../../x86_64-pc-msys/bin/ld: /c/S/B/src/msys2-runtime/winsup/cygwin/crt0.c:32:(.text+0x30): undefined reference to `cygwin_premain2'
/usr/lib/gcc/x86_64-pc-msys/11.3.0/../../../../x86_64-pc-msys/bin/ld: /c/S/B/src/msys2-runtime/winsup/cygwin/crt0.c:33:(.text+0x40): undefined reference to `cygwin_premain3'
collect2: error: ld returned 1 exit status
clang: error: linker (via gcc) command failed with exit code 1 (use -v to see invocation)
```
I actually don't know why but removing DLL from the path where the executable was built fixed it.
