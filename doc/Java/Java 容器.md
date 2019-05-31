## 目录

- [1.List, Set 和 Map 区别及联系？](#1List-Set-和-Map-区别及联系)
- [2.equals 和 hashCode 联系？](#2equals-和-hashCode-联系)
- [3.ArrayList 与 Vector 区别？](#3ArrayList-与-Vector-区别)
- [4.ArrayList 与 LinkedList 区别？](#4ArrayList-与-LinkedList-区别)
- [5.RandomAccess接口？](#5RandomAccess接口)
- [6.ArrayList 扩容机制？](#6ArrayList-扩容机制)
- [7.HashMap 与 HashTable 区别？](#7HashMap-与-HashTable-区别)
- [8.HashMap 与 HashSet 区别？](#8HashMap-与-HashSet-区别)
- [9.HashMap 与 ConcurrentHashMap 区别？](#9HashMap-与-ConcurrentHashMap-区别)
- [10.HashMap 的长度为什么是2的幂次方？](#10HashMap-的长度为什么是2的幂次方)
- [11.多线程情况下 HashMap 死循环问题？](#11多线程情况下-HashMap-死循环问题)
- [12.ConcurrentHashMap 工作原理？如何统计元素个数？](#12ConcurrentHashMap-工作原理如何统计元素个数)
- [13.Comparable 和 Comparator 区别？](#13Comparable-和-Comparator-区别)
- [14.如何选用集合？](#14如何选用集合)

---

### 1.List, Set 和 Map 区别及联系？

List和Set属于Collection集合体系，最顶层是Iterable接口，它定义迭代器，Collection接口是Iterable接口的子接口，它定义了集合操作基本的增删改查行为。List和Set都是Collection接口的子接口，List是线性，添加顺序和迭代顺序一致有序集合，它允许出现重复元素；而Set是添加顺序和迭代顺序不一致的有序集合，它不允许有重复元素。Map集合体系是键值对集合，它主要实现子类有HashMap、TreeMap和LindedHashMap；Set集合实现类底层是使用Map的实现类实现的，HashSet使用HashMap实现，TreeSet使用TreeMap实现。

### 2.equals 和 hashCode 联系？

在集合操作中，重写equals方法，就必须要重写hashCode方法。

因为，在散列操作中，如HashMap中，比较两个元素是否相等，首先先通过元素的hashCode得到元素的存储位置，如果该位置上有元素，也就是hash冲突，之后再通过equals方法比较key的值是否相等。

### 3.ArrayList 与 Vector 区别？

底层实现：底层都是使用Object数组，动态扩容存储元素。

线程安全性：ArrayList是线程不安全的，Vector是线程安全的，它使用synchronized对每个方法加锁保证安全。

使用选择上：Vector不会被使用，如果想要保证线程安全，使用CopyonWriteArrayList代替它。

### 4.ArrayList 与 LinkedList 区别？

底层实现：Arraylist使用数组动态扩容存储元素，LinkedList底层使用双向链表存储元素。

操作效率：ArrayList适合多读场景，LinkidList适合多写场景；因为数组查询快，增删慢，链表增删快，查询慢。

结构上：他俩都是线性集合存储结构，List的具体实现类。

线程安全性：他俩都是线程不安全的集合。

### 5.RandomAccess接口？

这个接口中没有需要实现的方法，它只是起到标识的作用；标识这个接口实现类可以随机访问。

### 6.ArrayList 扩容机制？

当调用ArrayList的add方法时，在这个方法中，进行添加之前，首先要进行容量检查，如果新的长度大于原数组的最大长度进行扩容操作，调用Arrays的copyOf方法进行扩容，这个方法底层实际上是调用System的arraycopy方法，扩容大小为原来容量的1.5倍。

### 7.HashMap 与 HashTable 区别？

底层实现：在JDK8中，HashMap底层使用数组和链表或红黑树实现，使用拉链法解决hash冲突，当拉链长度到达					8时，会被转化成红黑树；HashTable底层使用数组和链表实现，同样使用拉链法解决hash冲突。

初始大小：HashMap初始大小是16，HashTable初始大小是11。

线程安全：HashMap是线程不安全的，HashTable是线程安全的。但是HashTable实现线程安全的方式是在每个					方法上使用synchronized方法。由于所有线程竞争同一把锁，所以效率低下，现在基本不会是用它，					而是使用ConcurrentHashMap代替它。

对null值的支持：HashMap允许空键，而HashTable不允许使用空键。

### 8.HashMap 与 HashSet 区别？

HashSet底层是基于HashSet实现的，它的内部只使用HashMap的键存储数据，所有元素的值都是用同一个Object对象；HashSet增删改查操作都是调用HashMap的，在他的源码中代码量特别少。

### 9.HashMap 与 ConcurrentHashMap 区别？

底层实现：都使用数组加链表或红黑树实现。使用拉链法或红黑树解决哈希冲突，当链表长度到达8，会转换成红					黑是。

线程安全性：HashMap是线程不安全的，ConcurrentHashMap是线程安全的。jdk8之前使用的分段锁，对整个					桶数组进行分段加锁每一把锁只锁一段数据，多线程环境下，访问不同的段就不会发生竞争而等待。					jdk8中对每个桶数组也就是每个冲突链或红黑树使用锁，每个桶数组使用一个锁，这个更细粒度降低					多线程环境的冲突概率，提高并发访问效率。

### 10.HashMap 的长度为什么是2的幂次方？

HashMap默认长度为16，也就是2的2次幂，hash % length == hash & (length - 1)，由于用与运算代替模加快计算效率。


### 11.多线程情况下 HashMap 死循环问题？

在多线程条件下使用HashMap，当两个线程同时操作它，并同对其进行扩容操作，一个线程使用头插法将原来拉链的元素移动到新拉链的头部，此时如果cpu时间片用完，这个线程处于挂起状态。这个时候另一个线程同样这样操作，这个时候可能会产生循环拉链。当下次调用get方法时触发，这个时候便产生了死循环，使cpu使用率达到100%。

### 12.ConcurrentHashMap 工作原理？如何统计元素个数？

1.8 中的 ConcurrentHashMap 数据结构和实现与 1.7 还是有着明显的差异。

其中抛弃了原有的 Segment 分段锁，而采用了 CAS + synchronized 来保证并发安全性。

### 13.Comparable 和 Comparator 区别？

Comparable在java.lang包下，有个compareTo方法。

Comparator在java.util包下，有个compare方法。

一般使用集合排序时需要自己实现这两个接口。

### 14.如何选用集合？

主要根据集合的特点来选用，比如我们需要根据键值获取到元素值时就选用Map接口下的集合，需要排序时选择TreeMap,不需要排序时就选择HashMap,需要保证线程安全就选用ConcurrentHashMap.当我们只需要存放元素值时，就选择实现Collection接口的集合，需要保证元素唯一时选择实现Set接口的集合比如TreeSet或HashSet，不需要就选择实现List接口的比如ArrayList或LinkedList，然后再根据实现这些接口的集合的特点来选用。