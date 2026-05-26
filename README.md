# llvm.nx
llvm toolchain for NintendoSwitch homebrew

在`llvmorg-22.1.5`应用了[patch](https://github.com/llvm/llvm-project/pull/130932)并修复了clang崩溃问题。该patch添加了`-mtp=soft`选项实现了与`devkitpro/devkitA64`提供的`gcc`工具链相同的功能，参考用法
```
clang/bin/clang++ -fuse-ld=lld --target=aarch64-none-elf -o main.elf main.cc -mtp=soft --sysroot=$DEVKITPRO/devkitA64/aarch64-none-elf -stdlib=libstdc++ -fPIE -ffunction-sections --gcc-toolchain=$DEVKITPRO/devkitA64 -L $DEVKITPRO/libnx/lib -T switch.ld -march="armv8-a+crc+crypto" -mtune=cortex-a57 -Wl,--gc-sections -nostdlib -lnx -lc -lstdc++ -fPIE -Wl,--pie
```
