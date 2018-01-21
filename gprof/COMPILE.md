# Compiling a Program for Profiling

在編譯時指定 `-pg` 的選項，讓 linker 可以知道在編譯時加入 gprof 的相關動作

* 使用
範例：
```bash
cc -g -c myprog.c utils.c -pg
cc -o myprog myprog.o utils.o -pg
```

也可以這樣:
```bash
cc -o myprog myprog.c utils.c -g -pg
```

* 直接透過 `ld` linker

```bash
ld -o myprog /lib/gcrt0.o myprog.o utils.o -lc_p
```

## 流程

* 執行編譯參數
