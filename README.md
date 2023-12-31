# xun
### 数据集使用HDFS和BGL公开数据集，大致解释如下：

####  HDFS数据集

  HDFS数据和BGL数据，它们适合评估现有的异常检测方法。这两个数据集都是从生产系统中收集的，总共有15,923,592条日志消息和365,298个异常样本，由原始领域专家手动标记。我们将这些标签(异常与否)作为准确性评估的基础真理。
  HDFS数据包含11175629条日志，这些日志来自Amazon EC2平台。HDFS日志为每个block操作(如分配、写入、复制、删除)记录一个唯一的block ID。因此，会话窗口可以更自然地捕获日志中的操作，如III-B中所介绍的，因为可以利用每个唯一的块ID将日志切片为一组日志序列。然后从这些日志序列中提取特征向量，生成575,061个事件计数向量。其中16,838个样本被标记为异常。

#### BGL数据集

  BGL数据包含4,747,963条日志信息，这些信息由劳伦斯利弗莫尔国家实验室超级计算机系统记录。与HDFS数据不同，BGL日志没有记录每个作业执行的标识符。因此，我们必须使用固定窗口或滑动窗口将日志切片为日志序列，然后提取相应的事件计数向量。但是窗口的数量取决于所选择的窗口大小(和步长)。在BGL数据中，有348,460条日志消息被标记为失败，如果该日志序列中存在任何失败日志，则该日志序列被标记为异常。
