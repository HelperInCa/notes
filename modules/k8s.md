# 组件

API SERVER：所有服务访问统一入口
CrontrollerManager：维持副本期望数目
Scheduler：：负责介绍任务，选择合适的节点进行分配任务
ETCD：键值对数据库  储存K8S集群所有重要信息（持久化）
Kubelet：直接跟容器引擎交互实现容器的生命周期管理
Kube-proxy：负责写入规则至 IPTABLES、IPVS 实现服务映射访问
CoreDNS：可以为集群中的SVC创建一个域名IP的对应关系解析
Dashboard：给 K8S 集群提供一个 B/S 结构访问体系
Ingress Controller：官方只能实现四层代理，INGRESS 可以实现七层代理
Federation：提供一个可以跨集群中心多K8S统一管理功能
Prometheus：提供K8S集群的监控能力
ELK：提供 K8S 集群日志统一分析介入平台
	

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
  - Deployments
  - DaemonSet
  - Jobs CronJob
  - StatefulSet

- Service

  - Ingress
  
- Volumes

    - configMap
    
    - Secret
    
        Opaque
    
    - PersistentVolume & PersistentVolumeClaim
