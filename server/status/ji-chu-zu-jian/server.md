### Server

总体控制处理请求

![](/assets/static.png)

### ServerImpl

Server主要是要拿到相应的Transport\(Transport是针对流的抽象层\)

而认真处理请求的在ServerListener中的ServerTransportListener

在Start中初始化和拿到ServerListener。在ServerListener的transportCreated中初始化ServerTransportListenerImpl

SeverListener

![](/assets/serverlistener.png)

ServerTransportListener

![](/assets/transportListener)

而当StreamCreated被调用的时候就是一个GRPC请求创建的。当请求创建后。

这时候就是创建一个ServerStreamListener的对象。这个对象会在StreamTransport中的几个环节中调用。

但实际上是新开了一个进程。



在JumpApplicationListener里会新开进程。然后在执行整整的CallImplListener这个是在StreamCreated里面的代码。有一个StreamCreated的ContextRunable对象开新的进程![](/assets/StreamCreated.jpg)

真正的ServerStreamListener是下代码。找到Stream（Grpc流请求，方法名字，定义，头，上下文，统计等信息）

![](/assets/ServerStreamListener2.png)

ServerStreamListener有完整的Stream实现。这个时候反向把自身相光信息绑定到Listener上面。等待调用。







