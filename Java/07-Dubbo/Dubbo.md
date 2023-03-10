# Dubbo

> 是一种服务框架



# 分布式系统的相关概念



## 大型互联网项目架构目标



传统项目和互联网项目：

* 传统项目：OA、HR、CRM等
* 互联网项目：QQ、微信、淘宝、百度等



区别在于：

用户群体：

* 传统项目为企业员工
* 互联网项目为网民

用户数量：并发量



用户体验：美观（UI的事），功能（产品经理的事），速度，稳定性（这两个和我这个Java后端程序员有关）



互联网项目特点：

* 用户多
* 流量大，并发高
* 海量数据
* 易受攻击
* 功能繁琐
* 变更快



大型互联网项目架构目标：

1、高性能：快速的访问体验

衡量网站的性能指标：

* 响应时间：执行一个请求从开始到结束收到响应花费的总体时间
* 并发数：系统同时能处理的请求数量
  * 并发连接数：指的是客户端向服务器发起请求，并建立了TCP连接，每秒钟服务器连接的总TCP数量
  * 请求数：也称为QPS（Query Per Second）每秒多少请求
  * 并发用户数：单位时间有多少用户
* 吞吐量：单位时间内系统能处理的请求数量
  * QPS：每秒查询数
  * TPS：Transactions Per Second 每秒事务数
    * 一个事务指的是一个客户机向服务器发送请求然后服务器做出反应的过程。客户机在发送请求时开始计时，收到服务器响应后结束计时，以此计算使用的时间和完成的事务个数
    * 一个页面的一次访问，只会形成一个TPS，但一次页面请求，可能会产生多次对服务器的请求，就会有多个QPS
    * QPS >= 并发连接数 >= TPS



2、高可用：网站服务可以一直正常访问

3、可伸缩：通过硬件增加/减少，提高/降低处理能力

4、高可扩展：系统间耦合性低，方便的通过新增/移除方式，增加/减少新的功能/模块

5、安全性：提供网站安全访问和数据加密，安全存储等策略

6、敏捷性：随需应变，快速响应







## 集群和分布式



集群：很多”人“一起干一样的事

* 一个业务模块，部署在多台服务器上

分布式：很多“人“一起干不一样的事，这些不一样的事，合起来是一件大事

* 一个大的业务系统，拆分为小的业务模块，分别部署在不同的机器上







## 架构演进



单体架构 -> 垂直架构 -> 分布式架构 -> SOA架构 -> 微服务架构



1、单体架构：

优点：

* 简单，开发部署很方便，小型项目的首选

缺点：

* 项目启动慢
* 可靠性差
* 可伸缩性差
* 扩展性和可维护性差
* 性能低



2、垂直架构

也就是将单体架构中的多个模块拆分为多个独立的项目，形成多个独立的单体架构

各个独立的单体架构之间没有交互

解决了单体架构的一些问题，但是每个独立的单体架构也存在一些缺点

缺点：

* 重复功能多



3、分布式架构

在垂直架构的基础上，将公共的业务模块抽取出来，作为独立的服务（也就成了一个服务提供者），供其他调用者消费，以实现服务的共享和重用

**RPC**：Remote Procedure Call **远程过程调用**，有非常多的协议和技术来实现了RPC，比如：HTTP，REST，JavaRMI规范，WebService，SOAP协议，Hession等

缺点：

* 服务的提供方一旦变更，所有的消费方都需要变更
* 交叉调用多



4、SOA架构

SOA：Service-Oriented Architecture 面向服务的架构，是一个组件模型，将应用程序的不同功能单元（称为服务）进行拆分，并通过这些服务之间定义良好的接口和契约联系起来

ESB：Enterparise Service Bus 企业服务总线，服务中介，主要提供了一个服务于服务之间的交互，ESB包含的功能有：负载均衡，流量控制，加密处理，服务的监控，异常处理，监控告急等



5、微服务架构

也就是在SOA架构的基础上的升华，微服务架构强调的一个重点是"业务需要彻底的组件化和服务化"，原有的单个业务系统会拆分为多个可以独立开发，设计，运行的小应用，这些小应用之间通过服务完成交互和集成

* 微服务架构 = 80%的SOA服务架构思想 + 100%的组件化架构思想 + 80%的领域建模思想
* 特点：
  * 服务实现组件化：开发者可以自由的选择开发技术，也不需要协调其他团队
  * 服务之间交互一般使用REST API
  * 去中心化：每个微服务都有自己的私有的数据库持久化业务数据
  * 自动化部署：把应用拆分为一个一个独立的单个服务，方便自动化部署，测试，运维





Dubbo是SOA时代的产物

SpringCloud是微服务时代的产物







# Dubbo概述



## Dubbo概念



Dubbo是阿里巴巴公司开源的一个高性能、轻量级的Java RPC框架

如今已被Apache收录

致力于提供高性能和透明化的RPC远程服务调用方案，以及SOA服务治理方案

[Dubbo下载](http://dubbo.apache.org)





## Dubbo架构

![arch-service-discovery](https://dubbo.apache.org/imgs/architecture.png)

Provider：暴露服务的服务提供方

Container：服务运行容器

Consumer：调用远程服务的服务消费方

Register：服务注册与发现的注册中心

Monitor：统计服务的调用次数和调用时间的监控中心









# Dubbo快速入门



## Zookeeper安装



Dubbo官方推荐使用Zookeeper作为注册中心（Register）

我们需要在Linux环境下上传并启动，这里用Windows代替使用学习是一样的，没有区别。







## Dubbo入门



入门程序

实现步骤：

1. 创建服务提供者Provider模块
2. 创建服务消费者Consumer模块
3. 在服务提供者模块编写UserServiceImpl提供服务
4. 在服务消费者模块编写UserController远程调用UserServiceImpl提供的服务
5. 分别启动这两个模块，测试功能



服务提供者：

改为一个web项目，要拥有Dubbo的起步依赖，Zookeeper的客户端实现依赖

然后@Service注解改为用dubbo提供的

拥有Dubbo的起步依赖，Zookeeper的客户端实现依赖

Web项目要拥有Webapp目录和web.xml文件，web.xml文件中配置Spring

详情请见IDEA的**Dubbo项目**下的**Dubbo-Service模块**



服务消费者：

一个web项目，拥有Dubbo的起步依赖，Zookeeper的客户端实现依赖

拥有Dubbo的起步依赖，Zookeeper的客户端实现依赖

UserController内注入UserService的注解由@Autowired（本地注入）变为@Reference（远程注入）

```java
/*  远程注入的执行
 * 1.从zookeeper注册中心获取UserService的访问url
 * 2.进行远程调用RPC
 * 3.将结果封装为一个代理对象，给注入的对象赋值
 */
```

详情请见IDEA的**Dubbo项目**下的**Dubbo-Web模块**



要成功的远程注入UserService，需要服务提供者模块和服务消费者模块都拥有UserService接口，且内置方法一致，但一般不这样用，而是重新创建一个公共服务接口模块



公共服务接口：

**只提供接口与方法声明，接口的实现在服务提供者**

**其他两个模块都要依赖这个模块**

详情请见IDEA的**Dubbo项目**下的**Dubbo-Interface模块**



根据maven的特性，依赖项需要先install一下







# Dubbo高级特性



## Dubbo-admin管理平台

> 是个图形化服务管理页面工具 用于替换Dubbo架构中的Monitor



下载与配置：详情请见[dubbo-admin安装.md](./dubbo-admin安装.md)



是从注册中心中获取到所有的提供者/消费者进行配置管理

路由规则 动态配置 服务降级 访问控制 权重调整 负载均衡



耗时三天，终于成功启动并能使用dubbo-admin了：

1. 启动时，zookeeper的zkServer.sh需要启动

2. dubbo-admin可以在IDEA中启动，需要从外部导入dubbo-admin模块

3. 在dubbo-admin模块的配置文件application.properties中，修改服务端口为7001不然启动会报8080端口占用

   ```properties
   server.port=7001
   ```

4. 在dubbo-admin-ui模块下的config/index.js文件中，修改配置

   ```js
   proxyTable: {
         '/': {
           target: 'http://localhost:7001/',//需要和dubbo-admin-server的application.properties中的端口一致
           changeOrigin: true,
           pathRewrite: {
             '^/': '/'
           }
         }
       },
   ```

5. 然后我们启动dubbo-admin-server的启动类

6. 然后在IDEA的终端内cd进入dubbo-admin-ui目录 输入npm run dev（cd D:\Dubbo-admin\dubbo-admin-develop\dubbo-admin-ui）

7. 最后访问`http://localhost:8081`





## Dubbo常用高级配置



### 序列化

用于两个机器之间传输java对象

对象需要实现可序列化接口：Serializable

dubbo内部已经封装好了序列化和反序列化

我们只需要在定义pojo类时要实现Serializable接口

一般会定义一个公共的POJO模块，让生产者和消费者都依赖这个模块



## 地址缓存

注册中心挂了，服务是否可以正常访问？

：可以，因为dubbo服务消费者在第一次调用是，会将服务提供方地址缓存到本地，以后在调用则不会访问注册中心。当服务提供者地址发生变化时，注册中心会通知服务消费者



## 超时与重试

服务消费者在调用服务提供者的时候发生了阻塞，等待等情形，这时候，服务消费者会一直等待下去

在某个时刻，大量的请求都在同时请求服务消费者，会造成线程的大量堆积，就会造成“**雪崩**”

dubbo利用超时的机制来解决这个问题没设置一个超时时间，在这个时间内，无法完成服务访问就会自动断开连接

* 使用timeout属性配置超时时间，默认为1000，单位为毫秒（超时时间一般配置在服务的提供方，因为它能知道一个业务的具体耗时）



如果出现了网络抖动，则一次请求就会失败

Dubbo利用重试机制来避免类似问题

* 使用retries属性配置重试次数，默认为2次



## 多版本

灰度发布：当出现新版本时，会让一部分用户先使用新功能，用户反馈没有问题时，再将所有用户迁移到新功能

dubbo中：

* 使用version属性设置和调用同一个接口的不同版本



## 负载均衡

是在多集群的环境下

**负载均衡（Load Balance），意思是将负载（工作任务，访问请求）进行平衡、分摊到多个操作单元（服务器，组件）上进行执行。是解决高性能，单点故障（高可用），扩展性（水平伸缩）的终极解决方案**

负载均衡策略：

* Random：按权重随机，为默认值
* RoundRobin：按权重轮询
* LeastActive：最少活跃数调用数，相同的活跃数就随机
* ConsistentHash：一致性Hash，相同参数的请求总是发到同一提供者

使用loadbalance属性设置负载均衡策略



## 集群容错

一般我们在微服务应用中都是多实例部署，也就是说同一份代码部署多台机器或容器中，这样做的好处是提高服务处理能力。

同时由于集群部署，所以整个集群也有容错的能力。那么什么是容错呢？其实可以这样简单的理解：当我们在调用集群中一个实例时出错，我们可以重试另外一个实例这样大大提高了应用的可靠性

集群容错模式：

* Failover Cluster：失败重试。为默认值。当出现失败时，重试其他服务器。默认重试两次，使用retries配置。一般用于读操作
* Failfast Cluster：快速失败。只发起一次调用，失败后就立即报错。通常用于写操作
* FailsafeCluster：失败安全。出现异常时，直接忽略，返回一个空结果
* Failback Cluster：失败自动恢复。后台记录失败请求，定时重发
* Forking Cluster：并行调用多个服务器，只要有一个成功就返回
* Broadcast Cluster：广播调用所有提供者，逐个调用，任意一个报错就报错失败，也就是必须全部成功才成功

使用cluster属性设置集群容错模式



## 服务降级

服务降级是指 当服务器压力剧增的情况下，根据实际业务情况及流量，对一些服务和页面有策略的不处理或换种简单的方式处理，从而释放服务器资源以保证核心业务正常运作或高效运作

服务降级方式：

* force:return null：表示消费方对该服务的方法调用都直接返回null值，不发起远程调用，用来屏蔽不重要服务不可用时对调用方的影响
* fail:return null：表示消费方对该服务的方法调用在失败后，返回null值。不会抛异常。用来容忍不重要服务不稳定时对调用方的影响





> ©iWyh2



