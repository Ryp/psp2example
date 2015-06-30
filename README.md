# PSP2 Homebrew example

Homebrew sample using cmake.

Dependencies:
* arm-none-gcc compiler (also found in devkitARM)
* psp2sdk [via cmake branch](https://github.com/psp2dev/psp2sdk/tree/cmake)
* [psp2lib](https://github.com/psp2dev/psp2lib)

## Compiling

```shell
$ mkdir build && cd build
$ cmake .. -DCMAKE_TOOLCHAIN_FILE=$PSP2SDK/cmake/toolchain-arm-none-eabi-psp2.cmake -DCMAKE_BUILD_TYPE=Debug
$ make
```

## Credits

Thanks to [xerpi](https://github.com/xerpi) for his vitahelloworld !
