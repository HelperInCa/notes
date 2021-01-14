<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Contents**

- [组件](#%E7%BB%84%E4%BB%B6)
- [v1.13-1.18](#v113-118)
  - [1.13 -> 1.16](#113---116)
  - [1.16](#116)
  - [1.17](#117)
  - [1.18](#118)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

**是什么**? 

自动化运维管理容器化程序集群

# 组件

![image-20201012140205562](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20201230101055.png)

**Master:**

*API server*：所有服务访问统一入口（来自 UI / CLI）
*CrontrollerManager*：Node 监控器. 调整Node 上服务的状态(比如维持副本数量). 有很多具体的 Controller.
*Scheduler*：Node调度器，选择合适的节点进行分配任务
*etcd*：储存K8S集群所有重要配置. k8s中仅API SERVER才有读写权限. 键值对数据库 

**Node:**

*Kubelet*：直接跟容器引擎交互实现容器的生命周期管理
*Kube-proxy*：负责 Node 在 K8S 的网络通讯、以及对外部网络流量的负载均衡。
*Container Runtime*: 即安装了容器化所需的软件环境确保容器化程序能够跑起来，比如 Docker Engine。就是帮忙装好了 Docker 运行环境。

ADD-ons:

​	CoreDNS：可以为集群中的SVC创建一个域名IP的对应关系解析
​	Dashboard：给 K8S 集群提供一个 B/S 结构访问体系
​	Ingress Controller：官方只能实现四层代理，INGRESS 可以实现七层代理
​	Federation：提供一个可以跨集群中心多K8S统一管理功能
​	Prometheus：提供K8S集群的监控能力
​	ELK：提供 K8S 集群日志统一分析介入平台
​	

![image-20200815165917932](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200815165918.png)

![image-20200815165944302](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200815165944.png)

![image-20200815170106438](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200815170106.png)

- 网络通讯

  ![image-20200816130722043](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200816130722.png)

  1. 同一个Pod内部通讯:同一个Pod共享同一个网络命名空间,共享同一个 Linux协议栈
  2. Pod1至Pod2

  - Pod1与Pod2不在同一台主机,Pod的地址 doc是与0在同一个网段的,但 docker00网段与宿主机网卡是两个完
    全不同的IP网段,并且不同Node之间的通信只能通过宿主机的物理网卡进行。将Pod的P和所在node的I关联起来,通过
    这个关联让Pod可以互相访问

  - pod1与Pod2在同一台机器,由 Docker0网桥直接转发请求至Pod2,不需要经过 Flannel1演示

  3. Pod至 Service的网络:目前基于性能考虑全部为LVS维护和转发
  4. Pod到外网:Pod向外网发送请求,查找路由表,转发数据包到宿主机的网卡,宿主网卡完成路由选择后, iptables执行 Masquerade,把源IP更改为宿主网卡的IP,然后向外网服务器发送请求
  5. 外网访问Pod: Service
  
- 资源清单

- 生命周期

  ![image-20200817165938167](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20200817165938.png)

  - 探针 probe
  
- 控制器

  - ReplicaSet
  - Deployment: 常用. 管理 ReplicaSet(RS)
  - DaemonSet
  - Jobs CronJob
  - StatefulSet

- Service: 是 K8S 服务的核心，屏蔽了服务细节，统一对外暴露服务接口，真正做到了“微服务”

  - Ingress: Ingress 是整个 K8S 集群的接入层，负责集群内外通讯
  
      ![图片](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20201230110142.png)
  
- Volumes

    - configMap
    
    - Secret
    
        Opaque
    
    - PersistentVolume & PersistentVolumeClaim

![11-Pod](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20201014140415.png)

- 问题排查

    - K8S 上部署服务失败了怎么排查？

    请一定记住这个命令：`kubectl describe ${RESOURCE} ${NAME}`。比如刚刚的 Pod 服务 memory-demo，我们来看：

    ![图片](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20201230111809.png)

    拉到最后看到`Events`部分，会显示出 K8S 在部署这个服务过程的关键日志。这里我们可以看到是拉取镜像失败了

    一般来说，通过`kubectl describe pod ${POD_NAME}`已经能定位绝大部分部署失败的问题了

    - K8S 上部署的服务不正常怎么排查？

    如果服务部署成功了，且状态为`running`，那么就需要进入 Pod 内部的容器去查看自己的服务日志了：

    - 查看 Pod 内部某个 container 打印的日志：`kubectl log ${POD_NAME} -c ${CONTAINER_NAME}`。
    - 进入 Pod 内部某个 container：`kubectl exec -it [options] ${POD_NAME} -c ${CONTAINER_NAME} [args]`，嗯，这个命令的作用是通过 kubectl 执行了`docker exec xxx`进入到容器实例内部。之后，就是用户检查自己服务的日志来定位问题。 





# v1.13-1.18

## 1.13 -> 1.16

fabric8升版

fabric8: 开源微服务管理平台

`public IngressBackend(serviceName, servicePort)` 两个参数顺序调换

----

Deployment in the **extensions/v1beta1**, **apps/v1beta1**, and **apps/v1beta2** API versions is no longer served

use the **apps/v1** 

- `spec.selector` is now required and immutable after creation; use the existing template labels as the selector for seamless upgrades

---

StatefulSet in the **apps/v1beta1** and **apps/v1beta2** API versions is no longer served

- Migrate to use the **apps/v1** API version

- Notable changes:
    `spec.selector` is now required and immutable after creation; use the existing template labels as the selector for seamless upgrades

    > selector定义一个`Service`指向一组 pods 
    >
    > ```yaml
    > selector:
    > 	app: eureka-server
    > ```
    >
    > 对于[`Job`](https://kubernetes.io/zh/docs/concepts/workloads/controllers/job/)、 [`Deployment`](https://kubernetes.io/zh/docs/concepts/workloads/controllers/deployment/)、 [`Replica Set`](https://kubernetes.io/zh/docs/concepts/workloads/controllers/replicaset/) 和 [`DaemonSet`](https://kubernetes.io/zh/docs/concepts/workloads/controllers/daemonset/) ,支持基于集合
    >
    > ```yaml
    > selector:
    > 	matchLabels:
    > 		app: bdp-spring-cloud-config-server
    > ```

## 1.16

- 旧API 废弃

- 双栈

    IPv4 和 IPv6 地址分配给 Pods 和service

    1.17 设置 IPv6 网络掩码

    1.18 对 ipv6 的支持升至 beta

- 调度框架

    1.15alpha 向现有的调度器增加了一组新的“插件” API, 解决定制化调度需求

- Windows 节点生产可用

## 1.17

- 卷快照升至 beta 版本

    快照表示卷的时间点副本。快照可用于设置新卷（预填充快照数据）或将现有卷还原到先前状态（由快照表示）

- CSI迁移升至 Beta 版本

    CSI:容器存储接口

    k8s 本身提供了 存储卷in-tree插件, 因此要随核心Kubernetes二进制代码一同发布. CSI接口降低k8s 维护人员和厂商沟通的成本以及安全的隐患

    CSI迁移，用于辅助使用CSI方式替代现有的In-tree存储插件

- 条件化的污点升至正式版

    控制器自动根据条件为节点创建对应的污点。调度器则不去检查 Node conditions，而是检查节点的污点

## 1.18

- 配置HPA速率

    Horizontal Pod Autoscaler（HPA）可以使你的Kubernetes集群对高/低流量自动伸缩. 目前该功能仅在集群级别可以配置.

    ![img](https://pic4.zhimg.com/80/v2-fb22646abd2dc8c31eeb9670f16ea5c3_720w.jpg)

    例子:

    在典型的微服务应用程序中，你经常拥有一些比其他服务更重要的服务。假设你在Kubernetes上托管一个Web应用程序，该程序执行以下任务：

    

    1. 响应最终客户的请求（前端）
    2. 处理客户端提供的数据（包括执行大量CPU操作，例如map-reduce）。
    3. 处理不太重要的数据（例如，存档、清理等）

    

    从上述内容明显看出，任务1要求pod更快地扩展，以便应用程序可以快速有效地处理增加的客户端流量。此外，它们应该非常缓慢地缩小规模，以防再次出现流量高峰。

    

    任务2需要pod也可以非常快地扩展以响应增加的数据量。在关键任务应用程序中，不应延迟数据处理。但是，它们也应该非常迅速地缩减规模，因为一旦不再需要，它们会消耗大量地资源，而无法将这些资源用于其他服务。

    

    由于它们的重要性，我们可以在一定程度上容忍属于任务1和2的pod对误报做出响应。毕竟，浪费一些资源比失去客户要更好。

    

    服务于任务3的pod不需要特别地安排，因为它们按照常规的方式扩展和缩小即可。

- `Kubectl alpha debug`提供更多故障排除功能

    以前: 查看正在运行的Pod时, `kubectl exec`

    新: 将临时容器部署到正在运行的Pod。临时容器声明周期短，它们通常包含必要的调试工具。由于它们是在同一Pod中启动的，因此它们可以访问具有相同网络和文件系统的其他容器。这在极大程度上可以帮助你解决问题或跟踪问题。

- 增加Secret和ConfigMap不可变属性

    保护集群不受意外的坏更新的影响，Kubelet也不用定期检查更新.

    以前当对ConfigMap或Secret进行更改时，此更改将会立刻传递到安装了该配置文件的所有pod. 而一旦资源被标记为不可变，就无法恢复更改。只能删除和重建Secret/ConfigMaps，并且需要重建使用已删除Secret/ConfigMaps的pod

    > 使用ConfigMap来将配置数据注入到我们的容器中。如果数据十分敏感，那么则会使用Secret。将数据呈现给容器最常见的方式是通过挂载一个包含数据的文件

- OIDC发现

    将Service Account Token作为通用身份验证方法

    使API server提供OpenID Connect发现文档，该文档包含Token的公共密钥以及其他元数据。OIDC身份验证器可以使用此数据对token进行身份验证，而不必先引用API server。

- 在同一集群中支持RuntimeClass和多个Windows版本的标签

    允许在同一集群上混合Windows和Linux工作负载

**有些是Alpha 版本** 