# The Linux Programming Note

## 1. gcc编译器

### gcc编译的四个阶段(ESc)：

    hello.c  -------->   hello.i  -------->    hello.s  -------->    hello.o  ------->    hello.out
    预处理编译器（cpp）     编译器（gcc）          汇编器（as）           链接器（ld）
    gcc -E                gcc -S                gcc -c                gcc

### 编译工具链：

        预处理编译器：cpp     gcc -E hello.c -o hello.i   头文件展开，宏替换，注释去掉
             编译器：gcc     gcc -S hello.i -o hello.s   c文件变成汇编文件
             汇编器：as      gcc -c hello.s -o hello.o   汇编文件变成二进制文件
             链接器：ld      gcc hello.o -o hello        将函数库中相应的代码组合到目标文件中

### 编译时指定宏，通常用于调试代码-D

```gcc hello.c -D DEBUG```

    在需要打印日志的代码中加上下面的语句：
    #ifdef DEBUG
        printf("debug info");
    #endif

### 编译时对代码进行优化-O3

```gcc hello.c -o hello -O3```

    级别：
    0   没有优化
    1   缺省值
    3   优化级别最高

### 编译时显示告警信息-Wall

```gcc hello.c -o hello -Wall```

### 编译时包含调试信息-g（gdb）

```gcc hello.c -o hello -g```

## 2. 静态库的创建和使用

### 目录结构

    myCalc
    ├── include
    │   └── head.h
    ├── lib
    │   └── libMyCalc.a
    ├── main.c
    └── src
        ├── add.c
        ├── div.c
        ├── mul.c
        ├── sub.c

### 构建

``` shell
    gcc *.c -c -I ../include
    ar rcs libMyCalc.a *.o
    nm libMyCalc.a
    gcc main.c lib/libMyCalc.a -I include -o myapp
    gcc main.c -I include -L lib -l MyCalc -o myapp
```

## 3.动态库的创建和使用

### 目录结构

    myCalc
    ├── include
    │   └── head.h
    ├── lib
    │   └── libMyCalc.so
    ├── main.c
    └── src
        ├── add.c
        ├── div.c
        ├── mul.c
        ├── sub.c

### 构建

``` shell
    gcc -fPIC *.c -c -I ../include
    gcc -shared -o libMyCalc.so *.o -I ../include
    nm libMyCalc.so
    gcc main.c lib/libMyCalc.so -I include -o myapp
    gcc main.c -I include -L lib -l MyCalc -o myapp
    ldd myapp
    export LD_LIBRARY_PATH=./lib
    vi /etc/ld.so.conf
    ldconfig -v
```