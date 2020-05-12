# 使用筆記

### Proto

| 名稱 | 說明 |
| - | - |
| TCP | TCP 連線 |
| UDP | UDP 連線 |

### Recv-Q & Send-Q

指封包連線的接收隊列和發送隊列, 若不是 0 時表示封包正在隊列中堆積

### Local Address

本地 IP:Port

### Foreign Address

訪問的主機名稱和服務

### State

注意 UDP 是無狀態的, 所以這裡會是空白

| 名稱 | 說明 |
| - | - |
| LISTEN | 正在等待接收連接 |
| ESTABLISHED | 正處於活躍狀態的連接 |
| TIME_WAIT | 一個剛被中止的連接(持續時間約 1-2 分鐘後轉為 LISTEN) |

<br/>

# 情境範例

## 返回指定通道目前有多少正在進行中的連線數

```bash
netstat -a | grep ESTABLISHED | grep -c :{port}
```

## 取得有用的連接資訊

```bash
netstat -a
```

上面這個命令顯示出來的結果包含本地內部 Process 之間的連接資訊, 因此為了能正確顯示目前的網路連線資訊, 可以將命令改成如下：

```bash
netstat --inet -a
```

顯示出來的結果只會剩下目前正處於 `LISTEN` 與 `ESTABLISHED` 狀態的網路連線

<br/>

# Reference

1. [Linux netstat 命令](https://pxnet2768.pixnet.net/blog/post/64584717)