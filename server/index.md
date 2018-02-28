# gRPC服务器端源码

### Grpc大概流程

![](/assets/liucheng.png)

Transport做流控。Stream提供单个请求的抽象。写和读的动作抽象成Frame。

Server里面通过调用ServerCall来与Transport沟通。

而Netty提供Handler。与NettyServerHandler和NettyClientHandler做真正的流层控制

