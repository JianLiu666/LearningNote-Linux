# 使用筆記

可以針對當前的 Shell 調整資源限制, 且不會影響到其他的 Shell

### 檢視目前 Shell 的所有資源限制

```
ulimit -a
```

### 紀錄一些使用過的配置

```
ulimit -n size
```
調整可以同時打開的 fd(註1) 最大值

```
ulimit -u size
```
調整可以同時打開的 Process 最大值


<br/>

# Reference

1. [檔案描述符 File Discriptor](https://www.itread01.com/p/128784.html)

 - 當程式開啟一個現有檔案或者建立一個新檔案時,核心向程序返回一個檔案描述符。在程式設計中,一些涉及底層的程式編寫往往會圍繞著檔案描述符展開。
 - e.g. 每次嘗試建立一條新連線時都一定會建立一個 fd, 所以如果 fd 的資源限制過小的話, 很容易就會造成連線數量的瓶頸。

2. [Linux ulimit 命令](https://q248269673.pixnet.net/blog/post/66596238)
