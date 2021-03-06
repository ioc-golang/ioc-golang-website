---
title: "自动装载模型"
date: 2017-01-05
weight: 2
---

### 概念

自动装载(Autowire)模型封装了一类对象的装载方式，是本框架对装载过程抽象出的概念和接口。

用户需要定义的结构千变万化，如果每个结构描述符都要提供完整的装载过程信息，将是一件很麻烦的事情。我们可以将一类相似的结构抽象出一个自动装载模型，选择注册在该模型的所有对象都需要遵循该模型的加载策略，这大大降低了用户提供的结构描述符数据量，提高开发效率。

框架内置了两个基础自动装载模型：单例模型（singleton），多例模型（normal）

框架提供了两个扩展的自动装载模型：配置（config），gRPC 客户端（grpc）。其中配置模型是多例模型的扩展，gRPC 客户端是单例模型的扩展。框架内置了基于“配置自动装载模型”的多个结构。例如，用户可以用几行代码将 “gRPC 客户端存根”注册在 “grpc 装载模型” 之上[【示例】](/cn/docs/examples/grpc),方便地从配置文件中的指定位置读入下游主机名、从标签读入客户端名称，注入客户端单例指针。

