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

线程是任务调度的基本单位，进程是资源划分的基本单位；

### 2.线程与进程关系及区别？
当启动一个程序，在任务管理器中查看，会发现，一个程序就是一个进程；而无数个线程构成了一个进程。

### 3.并发和并行的区别？

并发：指在同一时间段，执行多个线程。

并行：指在同一时刻，执行多个线程，只有多核CPU才能做到。

### 4.为什么使用多线程？

提高CPU使用率。

提供程序的执行效率和运行速度。

提高系统并发能力以及性能。

### 5.多线程可能带来的问题？

死锁。

内存泄漏。

频繁上下文切换，损耗系统性能等。

### 6.线程的生命周期和状态？

新建、就绪、运行、阻塞、死亡。



新建：线程创建后尚未运行；new Thread()。(调用Thread.start()方法后分配资源，并进入就绪状态)

就绪：线程已经获取到所有运行所需要的资源，唯独没有CPU执行权。(获取的执行权后进入运行状态)

运行：就绪的线程获取到CPU执行权，并运行，处于运行状态。(sleep、wait、join等进入阻塞状态)

阻塞：执行过程中失去执行权的线程。(苏醒、notify等进入运行状态)

死亡：可以是程序运行完毕后自己结束，或者产生异常结束。


### 7.什么是上线文切换？

一个正在执行的线程，当其CPU时间片用完，系统会保存这个线程所运行的状态信息，以便下次获取到CPU执行权时恢复上次所执行的状态，这个过程就是上下文切换。

### 8.什么是线程死锁？如何避免死锁？

线程1，所占用资源A；线程2，所占用资源B。

线程1、2都出于等待状态，线程1等待线程2的B资源，线程2等待线程1的A资源；两个线程相互等待，这个就造成了死锁。



**造成死锁的条件有一下几个，只要破坏其中一个条件即可：**

资源独占：也就是互斥条件，这个没有办法破坏，因为锁本身就是想让他们互斥。

破坏不可剥夺：因外申请不到资源而等待的线程，如果申请不到资源，可以主动释放自己所占有的资源。

破坏保持申请：线程因外申请不到资源而不断申请；可以一次性申请所有所需资源。

破坏循环等待：进程循环等待序列，p1等待p2，p2等待p3，p3等待p1；可以按照申请顺序执行并释放资源。

### 9.线程间通信方式？

**等待通知机制：**

1）wait()、notify()方法。

2）join()方法。

**volatile共享变量**

3）通过volitale关键字声明一个全局变量，一个线程改变这个变量的状态，另一个能即受到改变，从而达到进程通信的目的。

**工具类：**

4）使用CountDownLatch类。

5）使用CyclicBarrier类。

### 10.创建线程三种方式？

实现Runable接口。

继承Thread类。

实现Callable接口。

### 11.接口实现多线程与实现Thread比较？

Java是单继承语言，如果实现Thread类，那么这个实现类就不能再继承其他的类，这显然是不可取的。

而接口可以多实现。就不会出现上面的局限性。

### 12.sleep方法和wait方法区别和共同点？

最重要的区别在于：wait方法会释放锁，sleep方法不会释放锁。

他俩都用于暂停一个正在运行的线程；wait方法主要用于等待通知中，和notify方法一起使用，sleep方法用于使线程睡眠一定时间。

### 13.为什么调用start方法会执行run方法？为什么不直接调用run方法？

Thread是Java中的线程类，new一个Thread，会新建一个线程，此时线程处于新建状态；调用start方法，这个线程会进行相应的准备工作和获取相应的运行资源，并进入就去状态；当获取到CPU时间片或执行权限，线程就开始运行，并自动执行run方法；这个run方法是在新的线程执行的，所以它是多线工作的。而使用main方法直接调用run方法，这个方法是在main线程中执行的，而不是在新线程中，所以不是多线程工作。

### 14.重入锁的概念，重入锁为什么可以防止死锁？

可重入：一个线程获取一个锁后，自己可以再次获取自己内部的锁。



**重入锁防止死锁，请看下面代码：**

```java
public class Animal {
	public synchronized void doSomething() {
        // TODO do something
    }
}

public class Cat extends Animal {
    public synchronized void doSomething() {
        super.doSomething();
    }
}
```

如果synchronized不是可重入锁，那么当调用Cat类的doSomething方法是会产生死锁。因为子类重写了父类的doSomething方法，当实例方法调用时，虚拟机会在运行时期动态绑定，运行期的Cat类会变成：

```java
public class Cat extends Animal {
    public synchronized void Animal.doSomething() {
        // TODO do something
    }
    
    public synchronized void doSomething() {
        super.doSomething();
    }
}
```

此时，调用Cat类的doSomething方法是，synchronized使用的是this(本类对象实例)锁，方法中又调用Animal.doSomething方法，而这个方法使用的锁也是this，子类没有释放锁，父类等待这个锁，相互都能带，从而死锁。所以，可重入锁能防止死锁。

### 15.偏向锁、轻量级锁、重量级锁、自旋锁的概念？

jdk1.6之后，对synchronized进行了优化。

锁一共分为四中状态：无锁状态、偏向锁、轻量级锁、重量级锁。

使用synchronized加锁时，锁不会直接就是重量级锁，而是从无锁状态，根据竞争的激烈程度而升级锁，直至到重量级锁。

偏向锁：偏心的偏，一个线程首先获取到锁，这个锁会偏向它；如果此后没有线程去获取这个锁，那么持有这个锁的线程就不需要同步，因为不存在多线程竞争的情况。

轻量级锁：加锁和释放锁主要使用CAS机制。

### 16.说一下对synchronized了解？

synchronized关键字是java解决的是多线程访问资源的同步性；它属于互斥锁。

**它可以修饰：**

实例方法：锁是任意对象。

静态方法：锁是Class对象。

代码块：所是任意对象。



synchronized底层实现是JVM层面上的，当修饰代码块时，代码块开始使用的monitorenter字节码命令，代码块结束使用的是monitorexit字节码命令；当修饰实例方法或静态方法时，是在方法上使用ACC_SYNCHRONIZED标识。

它时可重入锁，在jdk1.6之后，java对其进行了很多的优化，引入了各种锁……

### 17.synchronized和ReentrantLock区别？

1）都是可重入锁。

2）底层依赖不同；synchronized依赖JVM，ReentrantLock依赖api。

3）ReentrantLock比synchronized多更过的功能，如等待可中断。

4）性能已经不是选择的标准。

### 18.volatile内存模型？

Java程序在运行时，会把主存的数据读取到工作，然后在工作内存中进行读写，由于没有及时将更改的数据及时写入主存，读取数据时没有从主存中更新数据到工作内存，这就可能造成数据的不一致性。

volatile关键字，它指示JVM这个变量是不稳定的，要求线程每次都要到主存中进行读，写时，将数据及时写会主存。

volatile关键字的作用是保证变量的可见性和指令重排。

### 19.volatile和synchronized区别？

volatile只能用来修饰变量，synchronized用来修饰方法和代码块。

volatile比synchronized更加轻量级。

volatile只能保证变量的可见性，不能保证原子性；synchronized既能保证可见性，又能原子性。

volatile主要用于多线程之间的数据可见性，synchronized主要用于多线程访问资源的数据同步性。

### 20.join方法作用？

一个线程中调用另一个线程的join方法，当前线程会处于等待状态，直到另一个线程执行完毕。

### 21.为什么使用线程池？

重复使用线程，避免频繁创建和销毁线程消耗系统资源，降低系统资源消耗。

可以提高系统的相应速度。

可以对线程统一管理。

### 22.如何创建线程池？

**Executors工具类的静态方法：**

​	1）newCachedThreadPool()：创建一个无限大小的线程池。

​	2）newFixedThreadPool(int size)：创建一个固定大小的线程池。

​	3）等……；**它们底层调用的都是ThreadPoolExecutor类的构造方法。**

**通过ThreadPoolExecutor类构造方法**

### 23.说一下线程池核心的几个参数？

public ThreadPoolExecutor(int corePoolSize, int maximumPoolSize, long keepAliveTime, TimeUnit unit, BlockingQueue<Runnable> workQueue)

corePoolSize：核心线程数量，也就是刚创建线程池时线程的数量，线程池最小线程数量。

maximumPoolSize：线程池最大线程数量。

keepAliveTime：存活时间，多余核心线程数量部分线程的存活时间。

unit：时间单位。

workQueue：工作队列，如果线程池没有可使用的线程，但还是有请求，就把这些请求放到阻塞队列中。

### 24.Runnable和Callable区别？

它俩最主要区别在于Rnnable无返回值，而Callable有返回值。

### 25.execute方法和submit方法区别？

execute用于提交没有返回值的任务。

submit用于提交有返回值的任务，线程池会返回Future对象，从这个对象中可以获取返回值。

### 26.介绍一下Atomic原子类？

基本类型：

​	AtomicInteger

​	AtomicLong

​	AtomicBoolean

数组类型：

​	AtomicIntegerArray

​	AtomicLongArray

​	AtomicReferenceArray

引用类型：

​	AtomicReference

​	AtomicStampedReference

​	AtomicMarkableReference

对象属性修改类型：

​	AtomicIntegerFieldUpdater

​	AtomicLongFieldUpdater

​	AtomicReferenceFieldUpdater

### 27.JUC包中原子类有那四种？

基本类型、数组类型、引用类型、更改器。

### 28.讲讲AtomicInteger使用？

记不住，用的时候查api或idea有方法提示。

### 29.AtomicInteger原理？

底层使用CAS原理，Compare And Swap，比较和设置。它是计算机底层指令，有三个操作数，内存中的值V，预期旧值A，和新值B，如果 A等于V，那么将V的值改为B。

### 30.CopyOnWriteArrayList底层原理？只有写写互斥原理？

底层使用数组去实现，他能实现读写互不影响，不互斥。只有写写操作才互斥。

copy on write从这个名字中不难理解，读操作在原来数组上进行，进行写操作时，将原来数组拷贝一份副本，对这个副本加锁，在这个副本上进行写操作，只允许一个线程进行写操作。而原有数组不加锁，所有线程都可以读，不互斥。

### 31.非阻塞队列ConcurrentLinkedQueue？

底层是使用链表实现的，它是非阻塞队列。

### 32.阻塞队列ArrayBlockingQueue原理？

数组实现的阻塞队列，底层数据结构是数组，一旦创建，容量不可以改变。当这个队列已满时，再往其中添加元素，这个添加元素的线程会被阻塞，直至队列有空间可以添加元素；如果队列中没有元素，如果线程想从中取出元素，这个线程会被阻塞，直至队列中有元素。

#### 33.阻塞队列LinkedBlockingQueue原理？

链表实现的阻塞队列，底层数据结构使用的数组，这个队列的大小没有限制，最大是2的31次幂减一，原理同上。

### 34.什么是乐观锁和悲观锁以及使用场景？

乐观锁：类比现实中乐观的人，总是想着往事情好的方向发展；总是假设最好情景，每次拿数据时认为别人不会修改，所以不会上锁，但是在更新数据时，会判断数据有没有被别人修改，如果修改了就重试。

悲观锁：类比现实中悲观的人，总是想着事情往不好的方向发展；总是假设最坏情景，每次拿数据时认为别人会修改，所以加锁。

乐观锁适合用在多读的场景，balabala说一堆。悲观锁适合用在多写的情景，balabala说一堆。

### 35.乐观锁两种实现方式？

CAS机制，和版本号机制。balabala说一堆。

### 36.乐观锁缺点？ABA解决方式？

只能保证一个变量的原子性。

ABA问题。

可能会带来很长的循环开销。



ABA问题，使用JUC包下的AtomicStampedReference类和AtomicMarkableReference类。

### 37.CAS与synchronized的使用情景？

cas使用在单个变量，synchronized就比较灵活了。

### 38.介绍一下AQS及其原理？

AbstractQueueSynchronizer，这个抽象类是用来构建并发锁和同步器的框架，内部维护一个int类state计数器，用来控制同步状态，内部使用模板方法模式，如果想要自己实现锁，只需要重写其中个几个固定方法即可。ReentrantLock等。

### 39.CountDownLatch原理及使用场景？

一个线程或多个线程一直等待，直到其他线程执行完毕后在执行。

内部是维护一个计数器，初始化时会给计数器一个初始值，当线程调用countDown方法时，计数器值减一，直到减为0，那些因为调用await方法而等待线程被唤醒。这个计数器只能用一次。

使用场景：

一个线程等待n个线程执行完毕后再执行，如启动一个服务时，这个服务需要等待多个组件加载完毕。

### 40.CyclicBarrier原理及使用场景？

使多个线程相互等待，之后一起执行。

与CountDownLatch相似，内部也是维护一个计数器，当调用await方法时，计数器减一，当计数器为0时，因调用await方法被阻塞的线程同时被唤醒。这个计数器可以被重置。

使用场景：

用与多线程同步计算，最后将最终的计算结果汇总。

### 41.CountDownLatch和CyclicBarrier区别？

CountDownLatch是计数器，只能使用一次，而CyclicBarrier的计数器提供reset功能，可以多次使用。

balabala一堆。

### 42.Semaphore原理及使用场景？

使用就想操作系统中的信号量。
