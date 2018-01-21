# analysis_tools
Learning how to use analysis tools, like gprof, perf, valgrind, ...

主要學習如何使用這些分析工具

## Gprof

The GNU profiler, 用來找出程式中`執行`時***熱點***所在（消耗最多資源、時間的地方）

3個步驟來完成:

1. Compiling a Program for Profiling (compile & link 自己的程式，使得程式能夠啟用 profiling 機制)
2. Executing the Program to generate Profile Data (執行這支程式並產生 profile 用的相關檔案)
3. Using `gprof` command (透過 gprof 的指令來分析產生出的這些 profile 相關檔案)

其中產生的分析結果有兩種：

* **flat profile**
    * 指出在程式執行中，花費在每個 function 所耗費的`時間`，以及該程式在該次執行中`呼叫多少次該 function`
* **call graph**
    * 分析每個 function 被哪些 function 呼叫、呼叫了哪些 function，並紀錄這些 function call 的次數
    * 也評估了每個 function 花費在其 subroutines 上面的時間
    * 很適合用在花費大量時間的程式上，找出熱點並分析改善之（`更換演算法`, `修改資料結構`等等）

> 參考資料來源 [1] ：http://www.math.utah.edu/docs/info/gprof_toc.html