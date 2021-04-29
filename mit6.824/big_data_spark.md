# 参考资料
+ 视频: [B站](https://www.bilibili.com/video/BV1R7411t71W?p=15)
+ 课前预习 Preparation:
  + [Read Spark (2012)](https://pdos.csail.mit.edu/6.824/papers/zaharia-spark.pdf)
  + [FAQ](https://pdos.csail.mit.edu/6.824/papers/spark-faq.txt)
  + [Question](https://pdos.csail.mit.edu/6.824/questions.html?q=q-spark&lec=16)

# 笔记

## FAQ

1. RDD 的思想有在其他系统上的实现?

RDD 的特点主要有 2 点:
+ deterministic, lineage-based re-execution, 确定的基于血缘可重新执行. 即节点失败后, 可以通过数据血缘关系重新执行数据.
+ the collections-oriented  API. 面向集合的  API.

面向集合的 API, 类似的实现: DryadLINQ, FlumeJava, and Cloud Dataflow

确定的基于血缘可重新执行, 类似的实现: Dryad and Ciel systems

2. 使用 Scala 语言实现的优越性?
+ 可以共享内存.
+ 可以使用闭包捕获所有内置变量. (没有 runtime 的语言很难做到这点, 比如 Go)
