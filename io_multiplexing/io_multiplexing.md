# Epoll

epoll 沒有 fd 數量的限制, 他可以開啟的數量等同於 Linux 限制一個 Process 可以同時開啟 fd 的最大值。

epoll 使用一個 fd 來管理多個 fd, 將用戶關係的 fd 事件存放到 kernel 的一個事件表中, 這樣用戶和 kernel 之間只需要 copy 一次。