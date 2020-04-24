# 心得筆記

## 概念

I/O 多路複用的本質是透過一種機制, 讓單個 Process 可以監視多個 fd, 一個某個 fd 就緒(讀或寫就緒), 就能通知 Process 執行相對應的操作。

Linux 中基於 socket 的通信本質也是一種 I/O, 使用 socket() 函數產生的的 socket 預設都是阻塞的, 這表示 socket API 在調用時不能立即完成, thread 必須一直等待直到任務完成或是超時出錯, 下面是常見的阻塞情境：

1. 輸入操作: recv()、recvfrom()

 - 如果 buffer 內沒有資料可讀, 則會阻塞直到有新的資料抵達。

2. 輸出操作: send()、sendto()

 - 如果 buffer 內的空間已滿, 則會阻塞直到有空間可以寫入。

3. 接受連接: accept()

 - 等待接受對方的連線請求, 如果沒有連線請求則會一直阻塞直到超時。

4. 發起連接: connect()

 - 向對方發起連線請求, 在沒有得到對方接受以前, 不會返回。

上述問題可以採用多執行緒的方式來解決, 但是當連線數增加時每次新增的 fd 也會將記憶體塞滿, 且還需要考慮到執行緒在 context switch 上的成本。

## 常見的 I/O 模式

 - 阻塞 I/O (blocking I/O)
 - 非阻塞 I/O (nonblocking I/O)
 - I/O 多路複用 (I/O multiplexing)
 - 異步 I/O (asynchronous I/O)

<br/>

# Reference

1. [Linux 下 I/O 多路複用系統調用介紹](https://blog.csdn.net/pange1991/article/details/86310926)

2. [Linux I/O 模式與 select、poll、epoll 詳解](https://segmentfault.com/a/1190000003063859)