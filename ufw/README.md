# 使用筆記

### 安裝指令

```bash
sudo apt-get install ufw
```

### 狀態查詢

```bash
sudo ufw status
```

### 允許或封鎖任一段 Port

```bash
sudo ufw allow 80            # 允許 80 port
sudo ufw allow 7001:7006/tcp # 允許 TCP 7001~7006
sudo ufw deny 80             # 封鎖 80 port
```

<br/>

# Reference

1. [UFW 簡易防火牆設置](https://noob.tw/ufw/)