<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Contents**

- [组件](#%E7%BB%84%E4%BB%B6)

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