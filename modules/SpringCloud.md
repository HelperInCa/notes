

# 服务注册, 发现

管理服务之间依赖关系

**Eureka**:

![image-20201021154007513](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20201021154007.png)

Eureka采用 CS架构, 系统中服务通过 Eureka 的 client 连到 Eureka server 并维持**心跳连接**, 这样就可以通过 Eureka server 来监控各服务时候正常运行

- 原理

    1. 启动注册中心
    2. 启动服务提供者
    3. 服务提供者会把自身信息(服务地址以别名的方式注册进 Eureka)
    4. 消费者在需要调用接口时, 使用服务别名去注册中心获取实际的地址
    5. 消费者获得服务地址后, 底层是利用 Httpclient 实现远程调用
    6. 消费者得到的服务地址会缓存在内存中, 默认每 30s 更新一次

- 集群构建原理: 相互注册

    如果有三台, 1 2 -> 3, 2 3 -> 1, 1 3 -> 2 

- 服务发现

    1. 服务提供者添加 DiscoveryCLient

        ![](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20201029151451.png)

        ![](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20201029152110.png)

    2. 主启动类添加`@EnableDiscoveryClient`

        ![](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20201029152201.png)

    访问/payment/discovery 即可

- 自我保护

    CAP理论中 保证AP

    自我保护模式中, 不在注销任何服务实例.

    它是一种针对网络异常的安全保护措施: 宁可同时保留所有微服务(健康/不健康), 也不盲目注销任何可能健康的微服务.

    - 关闭自我保护:

        1. server: ![image-20201029165458835](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20201029165459.png)

        2. client:![](https://ipic-1300911741.oss-cn-shanghai.aliyuncs.com/uPic/20201029164127.png)

            

# 服务降级 熔断

