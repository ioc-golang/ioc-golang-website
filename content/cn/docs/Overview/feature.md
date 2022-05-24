---
title: "功能"
date: 2017-01-05
weight: 4
description: >
  IOC-Golang 框架提供的能力
---

- [依赖注入](/cn/docs/getting-started/tutorial/)

  支持任何结构、接口的依赖注入。

- 完善的对象生命周期管理机制。

  可以接管对象的创建、参数注入、工厂方法。可定制化对象参数来源。

- [代码调试能力](/cn/docs/examples/debug/)

  基于 AOP 的思路，为由框架接管的对象方法提供运行时监控、调试能力。

- [结构注册代码生成能力](/cn/docs/reference/iocli/#结构注解与sdcndocsconceptsd代码生成)

  我们提供了代码生成工具，开发者可以通过注解的方式标注结构，从而便捷地生成结构注册代码。

- [可扩展能力](/cn/docs/developer/)

  支持被注入结构的扩展、自动装载模型的扩展、调试 AOP 层的扩展。

- [完备的预制组件](/cn/docs/examples/)

  提供覆盖主流中间件的预制对象，方便直接注入使用。