---
title: 通过Java API实现Kafka Consumer从最开始消费
categories:
  - Coding
  - Java
tags:
  - Kafka
  - Java
abbrlink: 14f63398
date: 2018-03-06 22:07:41
---

之前写项目的时候需要通过Java API实现Consumer每次都从最开始消费，也就是将Kafka topic下所有partition的offset重置到最初位置。

这个功能类似shell下的命令：

```shell
./kafka-console-consumer.sh --bootstrap-server serverip:9092 --topic topic --from-beginning
```

<!-- more -->

Kafka的JavaDoc中提到可以使用`seekToBeginning(Collection<TopicPartition>)`方法来实现`--from-beginning`的功能，但是文档中没有详细说明如何使用，只是提及这个方法“evaluates lazily”， 只有在调用`poll(long)`或`position(TopicPartition)`的时候才重置offset到开头。所以直接在`subscribe(Pattern pattern)`后调用是不起作用的。

正确的方法应该是在Partition分配后的回掉函数中重置offset，具体代码如下：

```java
consumer.subscribe(Collections.singletonList(topic), new ConsumerRebalanceListener() {
    @Override
    public void onPartitionsRevoked(Collection<TopicPartition> partitions) {
    }

    @Override
    public void onPartitionsAssigned(Collection<TopicPartition> partitions) {
        consumer.seekToBeginning(partitions);
    }
});
```
