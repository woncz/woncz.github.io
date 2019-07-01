---
layout:     post
title:      "Netty reading_notes"
subtitle:   "Netty in Action"
date:       2019-07-01
author:     "Woncz"
header-img: "img/post-bg-universe.jpg"
catalog: true
tags:
  - Netty
  - reading_notes
---

### Netty概念和体系架构

- BIO -> NIO -> AIO 演化过程

- Future & Callback & ChannelHandler

- Selector & Event & EventLoop

### Netty Demo

- EchoServer & EchoClient

### Netty的组件和设计

- Channel & EventLoop & ChannelFuture

- ChannelHandler & ChannelPipeline

### 传输

- epoll

### ByteBuf

- ByteBuffer vs ByteBuf

- BytyBufHolder

- 池化 vs 非池化, 引用计数

### ChannelHandler和ChannelPipeline

- ChannelHandler lifestyle, inbound vs outbound

- ChannelPipeline 

- ChannelHandlerContext

- Exception process

### EventLoop和Reactor线程模型

- Reactor 

- EventLoop

- 任务调度

### BootStrap

- Bootstrap

- ServerBootStrap

### Unit Test

- EmbeddedChannel

- inbound & outbound test

### 编解码

- ByteToMessageDecoder & ReplayingDecoder & MessageToMessageDecoder & TooLongFrameException

- MessageToByteEncoder & MessageToMessageEncoder

- ByteToMessageCodec & MessageToMessageCodec & CombinedChannelDuplexHandler

### 预置的ChannelHandler和编解码器

- SSL/TSL

- HTTP/HTTPS & WebSocket on Netty

- 序列化

### WebSocket

- [WebSocket RFC](https://tools.ietf.org/html/rfc6455)

### 使用UDP广播事件

- UDP & Broadcast & local net

### Case
