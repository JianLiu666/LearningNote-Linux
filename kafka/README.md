# 理解筆記

是一種基於 zookeeper, 支持 partition、replica 的分散式消息系統, 同時具備：

- 高吞吐量、低延遲：每個 topic 可以分成多個 partition、consumer group 對 partition 進行 consume 操作
- 可擴展性：kafka 群集支持熱擴展
- 持久性：資料會同步落地到硬碟
- 容錯性：允許群集中最多 n-1 個節點失敗
- 高併發：就是高併發

### 檢查 Kafka 版本

```bash
find ./ -name \*kafka_\* | head -1 | grep -o '\kafka[^\n]*'
```

<br/>

# Reference

1. [Kafka 原理總結](https://zhuanlan.zhihu.com/p/79579389)
2. [Kafka 中文文檔](http://kafka.apachecn.org/)
3. [Kafka Docker](https://github.com/wurstmeister/kafka-docker/blob/master/README.md)
4. [Using Apache Kafka Command-line Tools](https://docs.cloudera.com/documentation/kafka/latest/topics/kafka_command_line.html)