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
  + 注意: 这里说的闭包不是指写代码时的闭包函数而是 "One good reason is that Scala provides the ability to serialize and ship user-defined code ("closures") as discussed"

3. Spark 是如何容错的(fault tolerance)?

RDD 在一些机器上保存了副本, 当某些节点失败时 Spark 根据 RDD 的血缘关系重新计算对应的部分.

4. 应用程序是如何知道 RDD 的位置的?

RDD 的位置信息保存在它的元数据部分. sheduler 就是用这部分元数据进行调度的.

一个 RDD 可能被多个节点产生, 但是每个节点上只能该 RDD 的不同部分.

5. 为什么 RDD 是不变可的?

因为 transform 等操作会产生新的 RDD. 并且 RDD 的运算是 lazy 的, 一般情况下 transform 等操作只是会形成的新的数据血缘图, RDD 并不会真正去进行计算.





