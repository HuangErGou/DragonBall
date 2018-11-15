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
./config no-asm no-shared no-threads --prefix=/home/huangqin/project/Zues/x86
make -j?
make install
```

2. 编译arm64平台
```
CC=/opt/gcc-linaro-6.3.1-2017.05-x86_64_aarch64-linux-gnu/bin/aarch64-linux-gnu-gcc ./config no-asm no-shared no-threads --prefix=/home/huangqin/project/Zues/aarch64

删除 Makefile 中的 -m64

make -j?
make install
```

### 编译 libwebsocket

1. 编译x86 平台

```
mkdir build
cd build

cmake .. -DCMAKE_INSTALL_PREFIX=/home/huangqin/project/Zues/x86 -DLWS_WITH_SSL=0 -DLWS_WITHOUT_TESTAPPS=ON -DLWS_WITH_SHARED=OFF 

make -j?

make install
```

2. 编译arm64平台
```
mkdir build
cd build

export PATH=$PATH:/opt/gcc-linaro-6.3.1-2017.05-x86_64_aarch64-linux-gnu/bin/

cmake .. -DCMAKE_INSTALL_PREFIX=/home/huangqin/tmp/install -DCMAKE_TOOLCHAIN_FILE=../contrib/cross-aarch64.cmake -DLWS_WITH_SSL=0 -DLWS_WITHOUT_TESTAPPS=ON -DLWS_WITH_SHARED=OFF 

make -j?

make install
```

---

### 编译 libcure

1. 编译x86 平台

```
./configure --prefix=/home/huangqin/project/Zues/x86 --enable-shared=no --enable-static=yes --with-ssl=/home/huangqin/project/Zues/x86 --without-zlib --without-librtmp --disable-ldap --disable-ldaps --disable-rtsp --disable-pthreads --disable-threaded-resolver

make -j?

make install
```

2. 编译arm64平台
```

./configure CC=/opt/gcc-linaro-6.3.1-2017.05-x86_64_aarch64-linux-gnu/bin/aarch64-linux-gnu-gcc CXX=/opt/gcc-linaro-6.3.1-2017.05-x86_64_aarch64-linux-gnu/bin/aarch64-linux-gnu-g++ --prefix=/home/huangqin/tmp/curl/aarch64 --enable-shared=no --enable-static=yes --host=aarch64 --with-ssl=/home/huangqin/project/Zues/aarch64 --without-zlib --without-librtmp --disable-ldap --disable-ldaps --disable-rtsp --disable-pthreads --disable-threaded-resolver

make -j?

make install
```

---

### 编译 thrift

1. 编译x86 平台 

```
./configure --prefix=/home/huangqin/tmp/ti/x86 --enable-shared=no --enable-static=yes  --with-boost=no --with-libevent=no --with-zlib=no --with-qt4=no --with-qt5=no --with-openssl=/home/huangqin/project/Zues/x86 --with-csharp=no --with-java=no --with-erlang=no --with-nodejs=no --with-lua=no --with-python=yes --with-py3=no --with-perl=no --with-php=no --with-php_extension=no --with-dart=no --with-ruby=no --with-haskell=no --with-go=no --with-rs=no --with-cl=no --with-haxe=no --with-dotnetcore=no --with-d=no

make -j?

make install
```

2. 编译arm64平台
```
nop
```

