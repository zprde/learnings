# [凤凰架构](http://icyfenix.cn/architecture/architect-history/)

> [A server should be like a phoenix, regularly rising from the ashes.](https://martinfowler.com/bliki/PhoenixServer.html)

----

## 架构演进

> 持续演进

Note: 这里可以写笔记

---

### 原始分布式时代

> Unix设计哲学: Worse is Better

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

---

----

## 架构师的视角
分布式服务间的通信与管理

---

