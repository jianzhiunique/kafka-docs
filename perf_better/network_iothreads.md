# 网络和I/O线程调优

Kafka使用网络线程池来处理客户端请求。请求进入一个请求队列，I/O线程会从中取出并进行处理。

当请求被处理完成后，响应会被放到内部的响应队列中，网络线程会从中收集，并发送响应给客户端。

#### num.network.threads
这是一个重要的集群层面的配置，控制处理网络请求的线程的数量，包括接收请求和发送响应。

应该按照生产者、消费者、副本拉取器的数量来决定。

#### queued.max.requests
控制在开始阻塞网络线程之前，最多允许请求队列中有多少请求。

#### num.io.threads
控制代理处理请求队列中的请求时，线程数量，这可能包含磁盘I/O。