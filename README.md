# Dragonball

---

### 编译boost

1. 编译x86 平台

```
./bootstrap.sh --prefix=dir_xxx
./b2 install --prefix=dir_xxx link=static variant=release
```

2. 编译arm64平台

```
./bootstrap.sh --prefix=dir_xxx
```

修改project-config.jam，把using gcc 修改为 
```
using gcc : mib3 : /opt/gcc-linaro-6.3.1-2017.05-x86_64_aarch64-linux-gnu/bin/aarch64-linux-gnu-g++ ;
```

```
./b2 install --prefix=dir_xxx link=static variant=release
```

---

### 编译openssl

1. 编译x86 平台

```
./config no-asm no-shared --prefix=dir_xxx
make -j?
make install
```

2. 编译arm64平台
```
CC=/opt/gcc-linaro-6.3.1-2017.05-x86_64_aarch64-linux-gnu/bin/aarch64-linux-gnu-gcc ./config no-asm no-shared --prefix=/home/huangqin/project/Zues/aarch64

删除 Makefile 中的 -m64

make -j?
make install
```

