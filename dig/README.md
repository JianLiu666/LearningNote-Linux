# 使用筆記

檢查是否是因為錯誤的解析導致無法訪問該域名

- 域名解析無結果 (可能是不存在或是被 HOLD(未實名認證))
- 域名解析到錯誤的 IP (可能是被阻斷、響應到錯誤結果, 需要對解析流程做判斷)
- 對應 CNAME 紀錄的值無法解析
- 部份解析異常  (配置多個域名伺服器時, 多個解析結果不一致, 需要確認是否在 DNS 伺服器上配置添加的解析紀錄一致)

### 示範解析百度搜尋引擎

```bash
dig www.baidu.com
```

### Dig 返回結果

```bash
# 顯示 Dig 命令的版本和輸入參數
; <<>> DiG 9.11.3-1ubuntu1.11-Ubuntu <<>> www.baidu.com
;; global options: +cmd

# 顯示服務返回的技術詳情, status 為 NOERROR 時表示本次查詢成功結束
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 1330
;; flags: qr rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 0, ADDITIONAL: 1

# 顯示查詢的域名
;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;www.baidu.com.         IN  A

# 顯示查詢結果
;; ANSWER SECTION:
www.baidu.com.    1200  IN  CNAME  www.a.shifen.com.
www.a.shifen.com.  299  IN  CNAME  www.wshifen.com.
www.wshifen.com.   299  IN  A      103.235.46.39

# 顯示本次查詢的統計訊息 (查詢耗時、DNS伺服器、查詢時間...)
;; Query time: 271 msec
;; SERVER: 127.0.0.53#53(127.0.0.53)
;; WHEN: Tue May 05 12:01:07 CST 2020
;; MSG SIZE  rcvd: 111
```

1. 由根域名伺服器找到負責解析 .com 的頂級域名伺服器
2. 由頂級域名伺服器找到 baidu.com 的二級域名伺服器
3. 由二級域名伺服器找到 www.baidu.com 對應一條 CNAME 紀錄 www.a.shifen.com
4. 再由 www.a.shifen.com 找到對應的 CNAME 紀錄 www.wshifen.com
5. 最後返回 A 紀錄對應的 IP 位置

## 補充: 手動設定網址與 IP 對應

Unix Like 系統在向 DNS 查詢網址與 IP 對應前, 會先查詢檔案 `/etc/hosts` 的內容
因此可以使用 Dig 解析出域名對應的 IP 位置後, 到該檔案手動綁定

<br/>

# Reference

1. [使用 Dig 命令查看 DNS 解析方法](https://kknews.cc/zh-tw/code/e62byx4.html)
2. [Dig 命令詳解](https://kknews.cc/zh-tw/code/8p9kp5q.html)