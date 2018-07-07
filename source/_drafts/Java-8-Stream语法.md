---
title: Java 8 Stream语法
categories:
  - Development
  - Code
tags:
  - Java
abbrlink: 57e4d917
---

# 概述

Java 8的一个重要新特性就是Stream。Stream是用函数式编程方式在集合类上进行复杂操作的工具，其集成了Java 8中的众多新特性之一的聚合操作，开发者可以更容易地使用Lambda表达式，并且更方便地实现对集合的查找、遍历、过滤以及常见计算等。

# 何为Stream？

聚合操作是Java 8针对集合类，使编程更为便利的方式，可以与Lambda表达式一起使用，达到更加简洁的目的。对聚合操作的使用可以归结为3个部分：

1. 创建Stream：通过`stream()`方法，取得集合对象的数据集。
2. Intermediate：通过一系列中间（Intermediate）方法，对数据集进行过滤、检索等数据集的再次处理。如使用`filter()`方法来对数据集进行过滤。
3. Terminal：通过最终（Terminal）方法完成对数据集中元素的处理。如使用`forEach()`完成对过滤后元素的打印。

在一次聚合操作中，可以有多个Intermediate，但是有且只有一个Terminal。也就是说，在对一个Stream可以进行多次转换操作，并不是每次都对Stream的每个元素执行转换。并不像`for`循环中，循环N次，其时间复杂度就是N。转换操作是lazy（惰性求值）的，只有在Terminal操作执行时，才会一次性执行。可以这么认为，Stream里有个操作函数的集合，每次转换操作就是把转换函数放入这个集合中，在Terminal操作的时候循环Stream对应的集合，然后对每个元素执行所有的函数。

# Stream的操作分类

刚才提到的Stream的操作有Intermediate、Terminal和Short-circuiting：

- Intermediate: map (mapToInt, flatMap, etc.), filter, distinct, sorted, peek, skip, parallel, sequential, unordered
- Terminal: forEach, forEachOrdered, toArray, reduce, collect, min, max, count, iterator
- Short-circuiting: anyMatch, allMatch, noneMatch, findFirst, findAny, limit

## 惰性求值和及早求值方法

像`filter`这样只描述Stream，最终不产生新集合的方法叫作惰性求值方法；而像`count`这样最终会从Stream产生值的方法叫作及早求值方法。

```java
long count = allArtists.stream()
    .filter(artist -> {
        System.out.println(artist.getName());
            return artist.isFrom("London");
        })
    .count();
```

如何判断一个操作是惰性求值还是及早求值，其实很简单，只需要看其返回值即可：如果返回值是Stream，那么就是惰性求值；如果返回值不是Stream或者是void，那么就是及早求值。上面的示例中，只是包含两步：一个惰性求值--`filter`和一个及早求值--`count`。在一个Stream操作中，可以有多次惰性求值，但有且仅有一次及早求值。

# 创建Stream

## 静态工厂方法

### of

`of`方法，其生成的Stream是有限长度的，Stream的长度为其内的元素个数。

```
- of(T... values)：返回含有多个T元素的Stream
- of(T t)：返回含有一个T元素的Stream
```

示例：

```java
Stream<Integer> integerStream = Stream.of(1, 2, 3);
Stream<String> stringStream = Stream.of("A");
```

### generator

`generator`方法，返回一个无限长度的Stream，其元素由Supplier接口的提供。在Supplier是一个函数接口，只封装了一个`get()`方法，其用来返回任何泛型的值，该结果在不同的时间内，返回的可能相同也可能不相同，没有特殊的要求。

```
- generate(Supplier<T> s)：返回一个无限长度的Stream
```

> 1. 这种情形通常用于随机数、常量的Stream，或者需要前后元素间维持着某种状态信息的Stream。
> 2. 把Supplier实例传递给`Stream.generate()`生成的Stream，默认是串行（相对parallel而言）但无序的（相对ordered而言）。

示例：

```java
Stream<Double> generateA = Stream.generate(new Supplier<Double>() {
    @Override
    public Double get() {
        return java.lang.Math.random();
    }
});
Stream<Double> generateB = Stream.generate(()-> java.lang.Math.random());
Stream<Double> generateC = Stream.generate(java.lang.Math::random);
```

以上三种形式达到的效果是一样的，只不过是下面的两个采用了Lambda表达式，简化了代码，其实际效果就是返回一个随机值。一般无限长度的Stream会与`filter`、`limit`等配合使用，否则Stream会无限制的执行下去，后果可想而知。

### iterate

`iterate`方法，其返回的也是一个无限长度的Stream，与`generate`方法不同的是，其是通过函数`f`迭代对给指定的元素种子而产生无限连续有序Stream，其中包含的元素可以认为是：`seed`, `f(seed)`, `f(f(seed))`无限循环。

```
- iterate(T seed, UnaryOperator<T> f)
```

示例：

```java
Stream.iterate(1, item -> item + 1)
        .limit(10)
        .forEach(System.out::println);
        // 打印结果：1, 2, 3, 4, 5, 6, 7, 8, 9, 10
```

上面示例，种子为1，也可认为该Stream的第一个元素，通过f函数来产生第二个元素。接着，第二个元素，作为产生第三个元素的种子，从而产生了第三个元素，以此类推下去。需要主要的是，该Stream也是无限长度的，应该使用`filter`、`limit`等来截取Stream，否则会一直循环下去。

### empty

`empty`方法返回一个空的顺序Stream，该Stream里面不包含元素项。

## Collection接口和数组的默认方法

在Collection接口中，定义了一个默认方法`stream()`，用来生成一个Stream。

示例：

```java
int ids[] = new int[]{1, 2, 3, 4};
Arrays.stream(ids)
        .forEach(System.out::println);
```

## 其他

- Random.ints()
- BitSet.stream()
- Pattern.splitAsStream(java.lang.CharSequence)
- JarFile.stream()

# Intermediate

> 参考文献
> Java 8系列之Stream的基本语法详解 https://blog.csdn.net/IO_Field/article/details/54971761
> Java 8系列之Stream的强大工具Collector https://blog.csdn.net/IO_Field/article/details/54971608
> Java 8系列之重构和定制收集器 https://blog.csdn.net/io_field/article/details/54971555
> Java 8系列之Stream中万能的reduce https://blog.csdn.net/IO_Field/article/details/54971679
