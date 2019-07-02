## 目录

- [1.Servlet生命周期？](#1Servlet生命周期)
- [2.转发和重定向区别？](#2转发和重定向区别)
- [3.BeanFactory和ApplicationContext 有什么区别？](#3BeanFactory和ApplicationContext-有什么区别)
- [4.Spring Bean的生命周期？](#4Spring-Bean的生命周期)
- [5.Bean作用域及默认是那个？](#5Bean作用域及默认是那个)
- [6.说一下bean的四个注解，可以让对象注入的注解？](#6说一下bean的四个注解-可以让对象注入的注解)
- [7.Spring IOC如何实现(初始化过程等)？](#7Spring-IOC如何实现初始化过程等)
- [8.Spring AOP如何实现？](#8Spring-AOP如何实现)
- [9.Spring事务实现方式？](#9Spring事务实现方式)
- [10.Spring事务的传播机制？](#10Spring事务的传播机制)
- [11.Spring默认事务类别？](#11Spring默认事务类别)
- [12.什么是MVC模式？](#12什么是MVC模式)
- [13.SpringMVC工作原理？](#13SpringMVC工作原理)
- [14.Spring用到的设计模式？](#14Spring用到的设计模式)
- [15.什么是Spring框架？](#15什么是Spring框架)
- [16.将一个类声明为Spring的 bean 的注解有哪些?](#16将一个类声明为Spring的 bean 的注解有哪些)
---

### 1.Servlet生命周期？

**1）加载和实例化：** 当Servlet容器启动时，或者容器检测到需要这个Servlet响应第一个请求时，容器加载并实例化Servlet实例。

**2）初始化：** 在Servlet实例化之后，容器将调用Servlet的init()方法初始化这个对象。

**3）处理请求：** Servlet容器调用Servlet的service()方法队请求进行处理。

**4）Servlet销毁：** 容器会调用Servlet的destor()去销毁Servlet实例。

### 2.转发和重定向区别？

1）地址栏：转发地址栏不发生变化，重定向后会显示重定向后的网址；

2）请求次数：转发请求一次，重定向请求两次；

3）数据：转发时，request中的数据不会丢失，可以在多个页面中实现请求数据共享；而重定向会丢失request中数据。

4）原理：转发是服务器端行为，重定向是客户端行为。

### 3.BeanFactory和ApplicationContext 有什么区别？



### 4.Spring Bean的生命周期？



### 5.Bean作用域及默认是那个？



### 6.说一下bean的四个注解，可以让对象注入的注解？



### 7.Spring IOC如何实现(初始化过程等)？



### 8.Spring AOP如何实现？



### 9.Spring事务实现方式？



### 10.Spring事务的传播机制？



### 11.Spring默认事务类别？



### 12.什么是MVC模式？



### 13.SpringMVC工作原理？



### 14.Spring用到的设计模式？



### 15.什么是Spring框架？



### 16.将一个类声明为Spring的 bean 的注解有哪些



