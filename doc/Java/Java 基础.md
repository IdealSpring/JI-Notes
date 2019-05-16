## 目录

-  [ 1.八种基本数据类型？](#1八种基本数据类型)
-  [2.面向对象的特征？](#2面向对象的特征)
-  [3.面向对象和面向过程区别？](#3面向对象和面向过程区别)
-  [4.final, finally, finalize 区别？](#4final-finally-finalize-区别)
-  [5.Error, Exception, RuntimeException 区别？](#5Error-Exception-RuntimeException-区别)
-  [6.5种常见的RuntimeExcetpion？](#65种常见的RuntimeExcetpion)
-  [7.int 和 Integer 区别？ Integer 缓存范围？](#7int-和-Integer-区别-Integer-缓存范围)
-  [8.包装类, 装箱, 拆箱？](#8包装类-装箱-拆箱)
-  [9.String, StringBuilder, StringBuffer 异同？](#9String-StringBuilder-StringBuffer-异同)
-  [10.String 不可变的好处？](#10String-不可变的好处)
-  [11.new String("abc"); 创建几个对象？](#11new-Stringabc-创建几个对象)
-  [12.重载和重写区别？](#12重载和重写区别)
-  [13.抽象类和接口区别？](#13抽象类和接口区别)
-  [14.反射的用途及实现？](#14反射的用途及实现)
-  [15.equals 和 == 区别？](#15equals-和--区别)
-  [16.hashCode 和 equals 区别和联系？](#16hashCode-和-equals-区别和联系)
-  [17.Java 的序列化和反序列化？](#17Java-的序列化和反序列化)
-  [18.为什么 wait() 和 notify() 属于 Object类？](#18为什么-wait-和-notify-属于-Object类)
-  [19.JDK, JRE, JVM 区别与联系？](#19JDK-JRE-JVM-区别与联系)
-  [20.浅拷贝和深拷贝区别？](#20浅拷贝和深拷贝区别)
-  [21.静态变量, 静态代码块,  实例变量, 普通代码块, 构造方法初始化顺序和继承情况下顺序？](#21静态变量-静态代码块-实例变量-普通代码块-构造方法初始化顺序和继承情况下顺序)
-  [22.无参构造函数作用？](#22无参构造函数作用)
-  [23.成员变量和局部变量区别？](#23成员变量和局部变量区别)
-  [24.构造方法特性？](#24构造方法特性)
-  [25.禁止序列化关键字？](#25禁止序列化关键字)
-  [26.Java 平台无关性如何体现出来？](#26Java-平台无关性如何体现出来)

------

### 1.八种基本数据类型？

- byte -- 1 bit；short -- 2 bit；int -- 4 bit；long -- 8 bit

- boolean -- 无；char -- 2 bit

- float -- 4 bit；double -- 8 bit


### 2.面向对象的特征？

面向对象三大特性：继承、封装、多态。

继承：是指子类继承父类的功能和方法，复用父类的代码。

封装：将一个对象的属性私有化，对外界提供访问属性访问方法。

多态：在程序中声明变量，变量指向其类型的子类或者实现类，在编译器不知道具体实现对象，只有在运行期知道具体实现类。

### 3.面向对象和面向过程区别？

面向过程关注的是"具体怎么做"，而面向对象关注是“让谁去做“，而这个谁就是指对象，不具体关注被调用者怎么去实现，许多对象共同完成一个功能点。

### 4.final, finally, finalize 区别？

final：用来修饰类、常量、方法，修饰类则不能被继承、修饰常量则初次赋值后则不能改变、修饰方法则方法不能被子类继承重写。

finally：用在catch代码块后面，无论程序是否抛出异常都会执行该代码块。

finalize：是Object类中的一个方法名，Java允许程序中调用此方法进行该对象的回收，但是不代表调用就会立即执行，只有当垃圾收集器空闲时且确定该对象可被回收时才会回收。

### 5.Error, Exception, RuntimeException 区别？

他们都继承自Throwable类，Throwable子类分为两大类，一类是Error代表JVM无法处理的错误，如OutOfMemoryError内存溢出和StackOverFlowError栈溢出，另一类是Exception异常；而Exception又分为两类，一类是可捕获异常，例如IOException，另一类是RuntimeException运行时异常，也就是不可捕获异常，例如空指针异常和数组下标越界异常。

### 6.5种常见的RuntimeExcetpion?

- 空指针异常：NullPointerException
- 字符串索引越界异常：StringIndexOutOfBoundsException
- 数组索引越界异常：ArrayIndexOutOfBoundsException
- 强制类型转换异常：ClassCastException
- 找不到类异常：ClassNotFoundException

### 7.int 和 Integer 区别？ Integer 缓存范围？

int是基本数据类型，Integer是int的包装类类型。Integer封装了许多操作int的方法。Integer在使用时需要去创建对象才可以使用。

Integer缓存范围为-128~127。

### 8.包装类, 装箱, 拆箱？

8种基本数据类型都有对应的包装类类型，除int的包装类为Integer和char的包装类为Character外，其他6种基本数据类型的包装类为将其首字母大写。

自动装箱：是在JDK5之后，程序中无需手动调用方法实现类型转换，而是自动转换，通过反编译工具查看源码底层设计上是调用封装类的valueOf方法。

自动拆箱：底层实际上是调用封装类的xxxValue方法。

### 9.String, StringBuilder, StringBuffer 异同？



### 10.String 不可变的好处？



### 11.new String("abc"); 创建几个对象？



### 12.重载和重写区别？



### 13.抽象类和接口区别？



### 14.反射的用途及实现？



### 15.equals 和 == 区别？



### 16.hashCode 和 equals 区别和联系？



### 17.Java 的序列化和反序列化？



### 18.为什么 wait() 和 notify() 属于 Object类？



### 19.JDK, JRE, JVM 区别与联系？



### 20.浅拷贝和深拷贝区别？



### 21.静态变量, 静态代码块, 实例变量, 普通代码块, 构造方法初始化顺序和继承情况下顺序？



### 22.无参构造函数作用？



### 23.成员变量和局部变量区别？



### 24.构造方法特性？



### 25.禁止序列化关键字？



### 26.Java 平台无关性如何体现出来？





