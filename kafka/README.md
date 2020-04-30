# 理解筆記

是一種基於 zookeeper, 支持 partition、replica 的分散式消息系統, 同時具備：

- 高吞吐量、低延遲：每個 topic 可以分成多個 partition、consumer group 對 partition 進行 consume 操作
- 可擴展性：kafka 群集支持熱擴展
- 持久性：資料會同步落地到硬碟
- 容錯性：允許群集中最多 n-1 個節點失敗
- 高併發：就是高併發

<br/>

# Reference

1. [Kafka 原理總結](https://zhuanlan.zhihu.com/p/79579389)