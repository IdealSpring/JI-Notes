## 目录

- [1.什么是线程和进程？](#1什么是线程和进程)
- [2.线程与进程关系及区别？](#2线程与进程关系及区别)
- [3.并发和并行的区别？](#3并发和并行的区别)
- [4.为什么使用多线程？](#4为什么使用多线程)
- [5.多线程可能带来的问题？](#5多线程可能带来的问题)
- [6.线程的生命周期和状态？](#6线程的生命周期和状态)
- [7.什么是上线文切换？](#7什么是上线文切换)
- [8.什么是线程死锁？如何避免死锁？](#8什么是线程死锁如何避免死锁)
- [9.线程间通信方式？](#9线程间通信方式)
- [10.创建线程三种方式？](#10创建线程三种方式)
- [11.接口实现多线程与实现Thread比较？](#11接口实现多线程与实现Thread比较)
- [12.sleep方法和wait方法区别和共同点？](#12sleep方法和wait方法区别和共同点)
- [13.为什么调用start方法会执行run方法？为什么不直接调用run方法？](#13为什么调用start方法会执行run方法为什么不直接调用run方法)
- [14.重入锁的概念，重入锁为什么可以防止死锁？](#14重入锁的概念重入锁为什么可以防止死锁)
- [15.偏向锁、轻量级锁、重量级锁、自旋锁的概念？](#15偏向锁轻量级锁重量级锁自旋锁的概念)
- [16.说一下对synchronized了解？](#16说一下对synchronized了解)
- [17.synchronized和ReentrantLock区别？](#17synchronized和ReentrantLock区别)
- [18.volatile内存模型？](#18volatile内存模型)
- [19.volatile和synchronized区别？](#19volatile和synchronized区别)
- [20.join方法作用？](#19volatile和synchronized区别)
- [21.为什么使用线程池？](#21为什么使用线程池)
- [22.如何创建线程池？](#22如何创建线程池)
- [23.说一下线程池核心的几个参数？](#23说一下线程池核心的几个参数)
- [24.Runnable和Callable区别？](#24Runnable和Callable区别)
- [25.execute方法和submit方法区别？](#25execute方法和submit方法区别)
- [26.介绍一下Atomic原子类？](#26介绍一下Atomic原子类)
- [27.JUC包中原子类有那四种？](#27JUC包中原子类有那四种)
- [28.讲讲AtomicInteger使用？](#28讲讲AtomicInteger使用)
- [29.AtomicInteger原理？](#29AtomicInteger原理)
- [30.CopyOnWriteArrayList底层原理？只有写写互斥原理？](#30CopyOnWriteArrayList底层原理只有写写互斥原理)
- [31.非阻塞队列ConcurrentLinkedQueue？](#31非阻塞队列ConcurrentLinkedQueue)
- [32.阻塞队列ArrayBlockingQueue原理？](#32阻塞队列ArrayBlockingQueue原理)
- [33.阻塞队列LinkedBlockingQueue原理？](#33阻塞队列LinkedBlockingQueue原理)
- [34.什么是乐观锁和悲观锁以及使用场景？](#34什么是乐观锁和悲观锁以及使用场景)
- [35.乐观锁两种实现方式？](#35乐观锁两种实现方式)
- [36.乐观锁缺点？ABA解决方式？](#36乐观锁缺点ABA解决方式)
- [37.CAS与synchronized的使用情景?](#37CAS与synchronized的使用情景)
- [38.介绍一下AQS及其原理？](#38介绍一下AQS及其原理)
- [39.CountDownLatch原理及使用场景？](#39CountDownLatch原理及使用场景)
- [40.CyclicBarrier原理及使用场景？](#40CyclicBarrier原理及使用场景)
- [41.CountDownLatch和CyclicBarrier区别？](#41CountDownLatch和CyclicBarrier区别)
- [42.Semaphore原理及使用场景？](#42Semaphore原理及使用场景)

---

### 1.什么是线程和进程？



### 2.线程与进程关系及区别？


### 3.并发和并行的区别？



### 4.为什么使用多线程？



### 5.多线程可能带来的问题？



### 6.线程的生命周期和状态？



### 7.什么是上线文切换？



### 8.什么是线程死锁？如何避免死锁？



### 9.线程间通信方式？



### 10.创建线程三种方式？



### 11.接口实现多线程与实现Thread比较？



### 12.sleep方法和wait方法区别和共同点？



### 13.为什么调用start方法会执行run方法？为什么不直接调用run方法？



### 14.重入锁的概念，重入锁为什么可以防止死锁？



### 15.偏向锁、轻量级锁、重量级锁、自旋锁的概念？



### 16.说一下对synchronized了解？



### 17.synchronized和ReentrantLock区别？



### 18.volatile内存模型？



### 19.volatile和synchronized区别？



### 20.join方法作用？



### 21.为什么使用线程池？



### 22.如何创建线程池？



### 23.说一下线程池核心的几个参数？



### 24.Runnable和Callable区别？



### 25.execute方法和submit方法区别？



### 26.介绍一下Atomic原子类？



### 27.JUC包中原子类有那四种？



### 28.讲讲AtomicInteger使用？



### 29.AtomicInteger原理？



### 30.CopyOnWriteArrayList底层原理？只有写写互斥原理？



### 31.非阻塞队列ConcurrentLinkedQueue？



### 32.阻塞队列ArrayBlockingQueue原理？



#### 33.阻塞队列LinkedBlockingQueue原理？



### 34.什么是乐观锁和悲观锁以及使用场景？



### 35.乐观锁两种实现方式？



### 36.乐观锁缺点？ABA解决方式？



### 37.CAS与synchronized的使用情景？



### 38.介绍一下AQS及其原理？



### 39.CountDownLatch原理及使用场景？



### 40.CyclicBarrier原理及使用场景？



### 41.CountDownLatch和CyclicBarrier区别？



### 42.Semaphore原理及使用场景？





