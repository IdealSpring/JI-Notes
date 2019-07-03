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
- [10.Spring事务的隔离级别？](#10Spring事务的隔离级别)
- [11.Spring默认事务类别？](#11Spring默认事务类别)
- [12.什么是MVC模式？](#12什么是MVC模式)
- [13.SpringMVC工作原理？](#13SpringMVC工作原理)
- [14.Spring用到的设计模式？](#14Spring用到的设计模式)
- [15.什么是Spring框架？](#15什么是Spring框架)
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

无

### 4.Spring Bean的生命周期？

- Bean容器找到配置文件中Spring bean定义；
- Bean容器利用反射创建一个bean实例；
- 如果涉及到一些属性值利用set()方法设置一些属性值；
- 如果实现BeanNameAware接口，调用setBeanName()方法设置Bean名字；
- 如果实现其他的Aware接口，调用相应的方法进行设置；
- 执行配置中bean初始化方法；
- 此时这个bean就可以使用了；
- 当他没用了需要被销毁时，执行bean中的destory()方法进行销毁。

### 5.Bean作用域及默认是那个？

singleton：唯一的bean对象，Spring中默认的，也就是单例。

prototype：每次请求都会创建一个新的bean实例。

request：每一次HTTP请求都会产生一个新bean，该bean实例仅在当前HTTP request中有效。

session：每一次HTTP请求都会产生一个新bean，该bean实例仅在当前HTTP session中有效。

### 6.说一下bean的四个注解，可以让对象注入的注解？

@Autowired注解自动装配bean；

在类上需要使用一下注解：@Component、@Service、@Controller。

### 7.Spring IOC如何实现(初始化过程等)？

IOC控制反转，将原本需要手动创建对象的控制权，交给Spring管理；由于不通过手动new的方式来创建对象，而是通过配置或者注解，在很大程度上降低了系统的耦合性。

IOC底层是通过反射的方式实现的。

### 8.Spring AOP如何实现？

AOP面向切面编程，能够将那些与业务无关，却为业务块所共同调用的代码或功能块（例如日志管理、权限管理、等）封装起来，动态的添加业务块前后；这样减少了系统的重复代码，降低模块之间的耦合度，有利于系统未来的扩展和维护。

AOP底层是基于动态代理实现的；如果代理接口，使用JDK提供的动态代理，去创建代理对象；如果是代理类，使用Cglib去实现动态代理，Cglib会创建代理对象的子类来作为代理类。

### 9.Spring事务实现方式？

两种实现方式：

1）编程式事务，在代码中硬编码；

2）声明式事务，在配置文件中配置；

声明式事务又分为两种：

1）基于xml的声明式事务；

2）基于注解的声明式事务；

- 配置事务管理器

    ```java
    <bean id="transactionManager class="org.springframework.jdbc.datasource.DataSourcTrproperty">
    	<property name="dataSource" ref="dataource"/>
    </bean>
    ```

- 开启事务注解

    ```java
    <tx:annotation-driven transaction-manager="transactionManager" />
    ```

- 在业务层上添加@TransactionManager注解

    ```java
    @Transaction
    ```

### 10.Spring事务的隔离级别？

事务的隔离级别一共有五种；默认的隔离级别是**后端数据库默认的事务隔离级别** 。

事务的传播行为一共有七种；默认的传播行为是**如果当前存在事务则加入该事物，如果没有则新建事务** 。

### 11.Spring默认事务类别？

见上面。

### 12.什么是MVC模式？

MVC中的，M是Model模型，V是View视图，C是Controller控制；SpringMVC框架以请求为驱动，围绕Servlet而设计的，将请求转发给控制器，然后通过模型对象，分派器来展示请求结果视图。

### 13.SpringMVC工作原理？

1）客户端浏览器发送请求，直接请求到前端控制器；

2）前端控制器根据请求信息调用处理器映射器；

3）处理器映射器根据请求的url找到具体的处理器，并生成处理器对象并返回给前端控制器；

4）前端控制器通过处理器适配器调用处理器；

5）处理器处理业务数据，处理完后会返回ModelAndView对象；

6）处理器适配器将ModelAndView对象返回给前端控制器；

7）前端控制器将ModelAndView传给视图解析器；

8）视图解析器解析后返回具体的View；

9）前端控制器对View进行视图渲染；

10）最后将渲染后的视图响应给客户端；

### 14.Spring用到的设计模式？

工厂模式：IOC工厂。

单例模式：Bean默认是单例。

模板方法模式：JDBCTemplate。

观察者模式：Spring 事件驱动模型就是观察者模式很经典的一个应用。

适配器模式：MVC中的适配器。

### 15.什么是Spring框架？

Spring是一种WEB开发框架，旨在提高开发人员的开发效率以及系统的可维护性。



