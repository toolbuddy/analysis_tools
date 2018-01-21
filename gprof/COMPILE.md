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

## 如何透過 flag 指定來做不同的操作

> 在使用 gprof 的這一步做 flag 加入：

* `-a`: 排除 static function 的 profiling: 

* `-b`: 只列印出基本的資訊（flat profile、 call graph）

* `-p`: 只印 flat profile
    * 而透過 `-p<function name>` 可以進一步只要求印出這個 function 在 flat profile 中的資訊（其餘的就跳過不印了）

* `-P`: 只印 call graph (換成大寫 P)    
    * 一樣可以透過 `-P<function name>` 來進一步只印出這個 function 在 call graph 中的資訊

* `-q`: 和 `-P` 的功能相同
    * 一樣支援 `-q<function name>` 的格式

* `-Q`: 和 `-p` 功能一樣（只印 flat profile）
