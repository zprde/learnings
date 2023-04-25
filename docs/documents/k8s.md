# KUBERNETES

> What's this?

----

## How we deploy our services

---

### Traditionally

![Physical](https://img.zprde.cn/images/2022/11/02/66269a550e38604e2acc85db50a026ad.png)

---

### Virtualization

![img](https://img.zprde.cn/images/2022/11/02/3b58bbdf271c5222f2f0a2edb3014cd7.png)

---

### Docker

![img](https://img.zprde.cn/images/2022/11/02/05170cee177746f977a84ba6caf3c4f8.png)

---

### K8s

![img](https://img.zprde.cn/images/2022/11/02/bab28d2e8476868fb808483ea2ddbd65.png)

----

## What k8s can do

* Service discovery and load balancing
* Storage orchestration
* Automated rollouts and rollbacks
* Automatic bin packing
* Self-healing
* Secret and configuration management

---

### How k8s implement that

![Kubernetes 的组件](https://d33wubrfki0l68.cloudfront.net/2475489eaf20163ec0f54ddc1d92aa8d4c87c96b/e7c81/images/docs/components-of-kubernetes.svg)

----

## K8S Components

> What we have for k8s.

---

### Pod

> *Pods* are the smallest deployable units of computing that you can create and manage in Kubernetes.

* logical host
* shared volumes and network
* a group of container

---

![image-20221103222243631](https://img.zprde.cn/images/2022/11/03/image-20221103222243631.png)

---

### Deployment

> A *Deployment* provides declarative updates for [Pods](https://kubernetes.io/docs/concepts/workloads/pods/) and [ReplicaSets](https://kubernetes.io/docs/concepts/workloads/controllers/replicaset/).

---

![Deployment](https://img.zprde.cn/images/2022/11/03/k8s-deployment.png)

---

### Job && CronJob

> Start a group of pods to finish some work by one time or scheduled.



---

### Service

> An abstract way to expose an application running on a set of [Pods](https://kubernetes.io/docs/concepts/workloads/pods/) as a network service.

---

![img](https://img.zprde.cn/images/2022/11/03/1tnK94zrEwyNe1hL-PhJXOA.png)

---



### Volumes

> Kubernetes supports many types of volumes.

---

![Exploring Kubernetes Volumes](https://img.zprde.cn/images/2022/11/04/volumes-1.png)

---

### ConfigMap && Secret

![Kubernetes Connector and ConfigSeeder](https://img.zprde.cn/images/2022/11/03/Features_K8sConnector_Setup.png)



---

### CRD(Custom Resource Definitions)

> Why don't create a new component you want.

----

## How to

----

## Links

* [Kubernetes Docs](https://kubernetes.io/docs/home/)

---