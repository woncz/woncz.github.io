---
layout:     post
title:      "Netty ChannelOption"
subtitle:   "ChannelOption"
date:       2019-06-27
author:     "Woncz"
header-img: "img/post-bg-os-metro.jpg"
catalog: true
tags:
  - Netty
  - ChannelOption
---

### SO_BACKLOG
```
对应于TCP/IP协议listen函数中的backlog参数，函数listen(int socketfd, int backlog)
用来初始化服务端可连接队列，服务端处理客户端连接请求是顺序处理的，所以同一时间只能处理
一个客户端连接，多个客户端来的时候，服务端将不能处理的客户端连接请求放在队列中等待处理，
backlog参数指定了队列的大小
```

### SO_REUSEADDR
```
表示允许重复使用本地地址和端口
```

### SO_KEEPALIVE
```
对应于套接字选项中的SO_KEEPALIVE，该参数用于设置TCP连接，当设置该选项后，连接会测试
链接的状态，这个选项用于可能长时间没有数据交流的连接。当设置该选项后，如果在两小时内没有
数据的通信是，TCP会自动发送一个活动探测数据报文。
```

### SO_SNDBUF & SO_RCVBUF
```
SO_SNDBUF对应于套接字选项中的SO_SNDBUF，SO_RCVBUF对应于套接字选项中的SO_RCVBUF，
这两个参数用于操作接收缓冲区和发送缓冲区的大小，接收缓冲区用于保存网络协议站内收到的
数据，直到应用程序读取成功，发送缓冲区用于保存发送数据，直到发送成功。
```

### SO_LINGER
```
对应于套接字选项中的SO_LINGER，Linux内核默认的处理方式时当用户调用close()方法的时候，
函数返回，在可能的情况下，尽量发送数据，不一定保证会发生剩余的数据，
造成了数据的不确定性，使用SO_LINGER可以阻塞close()的调用时间，直到数据完全发送。
```

### TCP_NODELAY & TCP_CORK
```
对应于套接字选项中的TCP_NODELAY，该参数的使用与Nagle算法有关，Nagle算法是将小的数据包
组装为更大的帧然后进行发送，而不是输入一次发送一次，因此在数据包不足的时候会等待其他数据
的到达，组装成大的数据包进行发送，虽然该方式有效提高网络的有效负载，但是却造成了延时，
而改参数的作用就是禁止使用Nagle算法，使用于小数据即时传输，与TCP_NODELAY相对应的是
TCP_CORK，该选项是需要等到发送的数据量最大的时候，一次性发送数据，适用于文件传输。
```

### IP_TOS
```
IP参数，设置IP头部的Type-of-Service字段，用于描述IP包的优先级和QoS选项。
```

### ALLOW_HALF_CLOSURE
```
Netty参数，一个连接的远端关闭时本地端是否关闭，默认值为False。值为False时，连接自动
关闭；为True时，触发ChannelInboundHandler的userEventTriggered()方法，事件为
ChannelInputShutdownEvent。
```
