# 使用範例

檢視可用參數
```bash
ab -h
```

同時進行 10 個連線, 總共連續點擊 10000 次 (每個 Request 執行完畢後都會自動斷線, 然後在重新連線)
```bash
ab -n 10000 -c 10 http://www.example.com/index.aspx
```

<br/>

# 壓測結果說明

### 基本項目

| 名稱 | 說明 |
| - | - |
| Server Software | Web主機的作業系統與版本(若Web主機設定關閉此資訊則無) |
| Server Hostname | Web主機的IP位址(Hostname) |
| Server Port | Web主機的連接埠(Port) |
| Document Path | 測試網址的路徑部分 |
| Document Length | 測試網頁回應的網頁大小 |
| Concurrency Level | 同時進行壓力測試的人數 |
| Time taken for tests | 本次壓力測試所花費的總秒數 |
| Complete requests | 完成的要求數(Requests) |
| Failed requests | 失敗的要求數(Requests) |
| Non-2xx responses | |
| Total transferred | 本次壓力測試的總數據傳輸量(包括 HTTP Header 的資料也計算在內) |
| HTML transferred | 本次壓力測試的總數據傳輸量(僅計算回傳的 HTML 的資料) |
| Requests per second | 平均每秒可回應多少要求 |
| Time per request | 平均每個要求所花費的時間(單位: 豪秒) |
| Time per request | 平均每個要求所花費的時間，跨所有同時連線數的平均值(單位: 豪秒) |
| Transfer rate | 從 ab 到 Web Server 之間的網路傳輸速度 |

### Connection Times (ms) 壓力測試時的連線處理時間

橫軸
| 名稱 | 說明 |
| - | - |
| min | 最小值 |
| mean | 平均值(正、負標準差) |
| median | 平均值(中間值) |
| max | 最大值 |

縱軸
| 名稱 | 說明 |
| - | - |
| Connect | 從 ab 發出 TCP 要求到 Web 主機所花費的建立時間 |
| Processing | 從 TCP 連線建立後，直到 HTTP 回應(Response)的資料全部都收到所花的時間 |
| Waiting | 從發送 HTTP 要求完後，到 HTTP 回應(Response)第一個 Byte 所等待的時間 |
| Total | 於 Connect + Processing 的時間(因為 Waiting 包含在 Processing 時間內了) |

<br/>

# Reference

1. [使用 ApacheBench 進行網站壓力測試](https://blog.miniasp.com/post/2008/06/30/Using-ApacheBench-ab-to-to-Web-stress-test)