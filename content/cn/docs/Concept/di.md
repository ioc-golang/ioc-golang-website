---
title: "依赖注入"
date: 2017-01-05
weight: 1
---

### 概念

依赖注入是指开发人员无需显式地创建对象，而是通过标签的方式声明字段，由框架负责将实例化对象写入该字段。

### 优点

依赖注入可以降低代码的耦合度，减少冗余代码量，优化代码逻辑。帮助开发人员面向对象编程，面向接口编程。

### IOC-Golang 的依赖注入能力

本框架从两个角度实现依赖注入：

- 结构如何被提供

  开发人员需要准备好需要被注入的结构，将它注册到框架。注册到框架的代码可以由开发人员手动编写，开发人员也可以通过使用[注解](../annotation)标记结构，使用 [ioc-go-cli](http://localhost:1313/cn/docs/reference/ioc-go-cli/#%E7%BB%93%E6%9E%84%E6%B3%A8%E8%A7%A3) 的代码生成能力自动生成注册代码，从而减少工作量。

  一个带有[注解](../annotation)的结构

  ```go
  // +ioc:autowire=true
  // +ioc:autowire:type=singleton
  
  type App struct {}
  ```

  由 ioc-go-cli 工具生成，或用户手动编写的注册代码。

  ```go
  func init() {
  	singleton.RegisterStructDescriptor(&autowire.StructDescriptor{
  		Interface: &App{},
  		Factory: func() interface{} {
  			return &App{}
  		},
  	})
  }
  ```

- 结构如何被使用

  - 通过标签注入

    开发人员需要通过标签来标记需要注入的结构字段。

    需要通过标签注入依赖的结构，其本身必须也注册在框架上。

    ```go
    // +ioc:autowire=true
    // +ioc:autowire:type=singleton
    
    type App struct {
    	MySubService Service `singleton:"ServiceImpl1"` 
    }
    ```

    

  - 通过 API 获取，入参为 [结构描述 ID](/cn/docs/concept/sd/#%E7%BB%93%E6%9E%84%E6%8F%8F%E8%BF%B0id) ，即可获取对象。

    ```go
    appInterface, err := singleton.GetImpl("App-App")
    	if err != nil {
    		panic(err)
    	}
    	app := appInterface.(*App)
    ```

    
