# Lib generate commands

## 1. Sort sample

```shell
cd MySort
gcc *.c
```

## 2. gcc with -D

```shell
cd gcc_about
gcc *.c -DDEBUG
```

## 3. Static lib and Shared lib

```shell
cd Calc/src
gcc -c -I../include *.c
ar rcs ../lib/libtest.a *.o
cd ..
gcc main.c lib/libtest.a -Iinclude
cd src
gcc -fPIC -c *.c -I../include
gcc -shared -o ../lib/libtest.so *.o
cd ..
gcc main.c -L./lib -ltest -Iinclude
ldd a.out
# /etc/ld.so.conf
# export LD_LIBRARY_PATH=/xxxx/xxx
```
