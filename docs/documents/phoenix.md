# [凤凰架构](http://icyfenix.cn/architecture/architect-history/)

> [A server should be like a phoenix, regularly rising from the ashes.](https://martinfowler.com/bliki/PhoenixServer.html)

----

## 架构演进

> 持续演进

Note: 这里可以写笔记

---

### 原始分布式时代

> Unix设计哲学（之一）: Worse is Better

在Unix早期，OSF(Open Software Foundation)进行了许多关于分布式相关的实践。

---

- DCE(Distributed Computing Environment) <!-- .element: class="fragment" -->
- RPC(Remote Procedure Call) <!-- .element: class="fragment" -->
- DFS(Distributed File System) <!-- .element: class="fragment" -->
- Kerberos服务认证规范、时间服务、命名、目录服务、UUID <!-- .element: class="fragment" -->

Note: 在Unix上进行的不算成功的分布式尝试，主要受限于当时的硬件环境。但是探索出了相当多的分布式相关的理论。

---

### 单体系统时代
> “单体”只是表明系统中主要的过程调用都是进程内调用，不会发生进程间通信，仅此而已。

---

#### 无用巨石？

- 易于开发、测试、部署 <!-- .element: class="fragment" -->
- 不会发生进程间调用，流程效率高 <!-- .element: class="fragment" -->
- 依然可拆分：纵向分层、横向分模块 <!-- .element: class="fragment" -->
- 集群部署 <!-- .element: class="fragment" -->

---

#### 一些缺陷

- 局部缺陷影响整个系统（内存泄漏、线程爆炸、阻塞、死循环等） <!-- .element: class="fragment" -->
- 很难局部更新功能，不易维护 <!-- .element: class="fragment" -->
- 难以异构 <!-- .element: class="fragment" -->


---

### SOA 时代(Service-Oriented Architecture)
> 面向服务的架构是一次具体地、系统性地成功解决分布式服务主要问题的架构模式。

成功但不完全成功

---

### 一些架构演变

> 为了对大型的单体系统进行拆分，让每一个子系统都能独立地部署、运行、更新，开发者们曾经尝试过多种方案

- [烟囱式架构](https://en.wikipedia.org/wiki/Information_silo)（Information Silo Architecture）
- [微内核架构](https://en.wikipedia.org/wiki/Microkernel)（Microkernel Architecture）
- [事件驱动架构](https://en.wikipedia.org/wiki/Event-driven_architecture)（Event-Driven Architecture）

---

### SOAP和WSDL

![图 2 说明了 SOAP、UDDI、WSIL 与 WSDL 之间的关系。](http://img.zprde.cn/images/2023/05/06/soapudws-20230506000021621.gif)

Note: SOAP（简单对象访问协议）和WSDL（Web服务描述语言）是两个互相关联的技术，通常用于构建分布式应用程序中的Web服务。

SOAP是一种基于XML的协议，用于在不同的应用程序之间传输消息。它提供了一种标准化的方式来定义消息的格式和交换协议。SOAP消息通常在HTTP、SMTP等传输协议上进行传输。

WSDL是一种XML格式的文档，用于描述Web服务的接口和操作。它定义了Web服务的输入和输出参数以及消息格式，并描述了如何与Web服务进行通信。WSDL可以被认为是Web服务的“使用手册”，客户端通过它来了解如何访问和使用Web服务。

因此，SOAP和WSDL是密切相关的，因为SOAP用于定义Web服务消息的格式和交换协议，而WSDL用于定义Web服务的接口和操作。在使用SOAP协议的Web服务中，WSDL文件通常用于描述Web服务的操作和消息格式，以便客户端可以正确地构造SOAP消息并与Web服务进行交互。

---

## 微服务(Microservices)

> [martinfowler.com](https://martinfowler.com/articles/microservices.html#MicroservicesAndSoa)
>
> http://icyfenix.cn/architecture/architect-history/microservices.html

---

## 后微服务时代（Cloud Native）

> 从软件层面独力应对微服务架构问题，发展到软、硬一体，合力应对架构问题的时代，此即为“后微服务时代”。

- 虚拟化 <!-- .element: class="fragment" -->
- 容器化 <!-- .element: class="fragment" -->
- Kubernate <!-- .element: class="fragment" -->
- 服务网格（Service Mesh） <!-- .element: class="fragment" -->

---

## 无服务时代（Serverless）

---

## AI Generated时代？

> 小chat小chat，帮我创建一个购物网站？

----

# 架构师的视角
> 分布式服务间的通信与管理

---

## 访问远程的服务

- 远程服务调用
- REST 设计风格

---

### 远程服务调用（Remote Procedure Call，RPC）

>像调用本地方法一样调用远程方法

---

#### 进程间通信（（Inter-Process Communication））

> 不同进程间的调用

- 管道（Pipe） <!-- .element: class="fragment" -->
- 信号（Signal）  <!-- .element: class="fragment" -->
- 信号量（Semaphore）  <!-- .element: class="fragment" -->
- 消息队列（Message Queue）  <!-- .element: class="fragment" -->
- 共享内存（Shared Memory）  <!-- .element: class="fragment" -->
- 套接字接口（Socket）  <!-- .element: class="fragment" -->

---

## 通信的成本

- 两个进程通信，谁作为服务端，谁作为客户端？  <!-- .element: class="fragment" -->
- 怎样进行异常处理？异常该如何让调用者获知？  <!-- .element: class="fragment" -->
- 服务端出现多线程竞争之后怎么办？  <!-- .element: class="fragment" -->
- 如何提高网络利用的效率，譬如连接是否可被多个请求复用以减少开销？是否支持多播？  <!-- .element: class="fragment" -->
- 参数、返回值如何表示？应该有怎样的字节序？  <!-- .element: class="fragment" -->
- 如何保证网络的可靠性？譬如调用期间某个链接忽然断开了怎么办？  <!-- .element: class="fragment" -->
- 发送的请求服务端收不到回复该怎么办？  <!-- .element: class="fragment" -->

---

#### 八宗罪

1. The network is reliable —— 网络是可靠的。  <!-- .element: class="fragment" -->
2. Latency is zero —— 延迟是不存在的。  <!-- .element: class="fragment" -->
3. Bandwidth is infinite —— 带宽是无限的。  <!-- .element: class="fragment" -->
4. The network is secure —— 网络是安全的。  <!-- .element: class="fragment" -->
5. Topology doesn't change —— 拓扑结构是一成不变的。  <!-- .element: class="fragment" -->
6. There is one administrator —— 总会有一个管理员。  <!-- .element: class="fragment" -->
7. Transport cost is zero —— 不必考虑传输成本。  <!-- .element: class="fragment" -->
8. The network is homogeneous —— 网络是同质化的。  <!-- .element: class="fragment" -->





