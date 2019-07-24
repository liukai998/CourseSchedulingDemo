# 排课系统设计报告

<!-- - 本报告由markdown语法写成，为了获得更好的阅读体验，请打开[github链接](https://github.com/AzureXH/CourseSchedulingDemo) -->

## 目录

<!-- TOC -->

- [排课系统设计报告](#%e6%8e%92%e8%af%be%e7%b3%bb%e7%bb%9f%e8%ae%be%e8%ae%a1%e6%8a%a5%e5%91%8a)
  - [目录](#%e7%9b%ae%e5%bd%95)
  - [设计背景](#%e8%ae%be%e8%ae%a1%e8%83%8c%e6%99%af)
  - [技术栈](#%e6%8a%80%e6%9c%af%e6%a0%88)
  - [主要](#%e4%b8%bb%e8%a6%81)
    - [前端](#%e5%89%8d%e7%ab%af)
    - [后端](#%e5%90%8e%e7%ab%af)
  - [技术栈介绍](#%e6%8a%80%e6%9c%af%e6%a0%88%e4%bb%8b%e7%bb%8d)
    - [vue](#vue)
    - [vue-router](#vue-router)
    - [element-ui](#element-ui)
    - [axios](#axios)
    - [Springboot](#springboot)
    - [MongoDB](#mongodb)
  - [使用这套技术栈的原因](#%e4%bd%bf%e7%94%a8%e8%bf%99%e5%a5%97%e6%8a%80%e6%9c%af%e6%a0%88%e7%9a%84%e5%8e%9f%e5%9b%a0)
  - [开发工具](#%e5%bc%80%e5%8f%91%e5%b7%a5%e5%85%b7)
  - [体系架构](#%e4%bd%93%e7%b3%bb%e6%9e%b6%e6%9e%84)

<!-- /TOC -->

## 设计背景

1. 自学web项目开发所做的一个项目
2. 管理信息系统作业

<!-- ## 必要说明

- 首先这只是一个用于学习的项目
  - 其次由于我的css基础比较差，而且为了赶时间
    - 所以这个项目只实现基本的功能，不考虑界面是否好看
- 因为非关系型数据库的数据结构可以嵌套
  - 而且数据量不大
    - 所以我并不打算对数据库进行优化，只求功能实现
- 这个报告注重的是实现而不是设计，毕竟设计一个系统从来就不是一个人的事，但是不会写代码就连设计的资格都没有 -->

## 技术栈

## 主要

- vue + Springboot + MongoDB

### 前端

- vue
- vue-router
- element-ui
- axios

### 后端

- Springboot
- MongoDB

## 技术栈介绍

### vue

- 一种网页的开发框架
- 使用组件化开发的理念，将每个页面当做组件，每个页面中还可以放入小的组件，这样可以减少重复代码

### vue-router

- 网页开发的路由管理器，具体就是将**每个组件**与**用户浏览网页时的地址**进行映射
- 通过vue-router可以实现嵌套路由，在一个主路由下，增加子路由，实现上文所说的减少重复代码

### element-ui

- 由饿了么开发团队所开发的一套基于vue的网页组件库
- 作为一个初学者，直接使用这样的组件库可以减少很多开发时间

### axios

- 一种基于promise(不懂)的HTTP库，用于客户端(即浏览器)向服务器发送请求，并得到服务器响应后对页面进行处理

### Springboot

- 一个后端的开发框架，将服务器处理请求的逻辑封装
- 只需要在该框架中定义控制器，将客户端发出的请求中的地址(即url)写在控制器的映射中，就可以找到相对应的方法。

### MongoDB

- 一种NoSql数据库
- NoSql的意思是(Not Only Sql)
- 它是一种非关系型的数据库，存储数据的方式是文档类型的
- 例如

``` json
{
    "username": "teacher",
    "password": "teacher123",
    "address":{
        "province": "广东省",
        "city": "珠海市"
    }
}
```

- 可以看到，这种类型的数据库不像关系型数据库只有固定的变量
- NoSQL的变量是可以嵌套的
- 相对应的

    |        SQL         |      NoSQL       |
    | :----------------: | :--------------: |
    |    数据表(Table    | 集合(Collection) |
    | 记录(表中的某一行) |  文档(Document)  |
    | 字段(表中的某一列) |    域(Field)     |
- 相比关系型数据库，NoSQL这类数据库存储数据更加的灵活
  - 关系型数据库的结构是定死的
  - 但是非关系型数据库没有那么多的规定，NoSQL中的每一个记录都可以不一样
  - 例如

  ```json
  {
    "name": "Foo"
  },
  {
    "name": "Bar",
    "age": 15
  }
  ```

  - 可以看到两个记录有着不一样的数据格式，这样便增加了更多的灵活性。

## 使用这套技术栈的原因

1. 这学期软工大作业的前端用的是bootstrap+jquery，可能是自己弱，感觉十分的麻烦，所以打算学习一套比较新的前端框架
2. Springboot作为后端框架比较好用，而且这个学期一直在用
3. 一直学关系型数据库感觉比较脱离实际，所以想要学一下非关系型数据库，于是就从MongoDB入手了

## 开发工具

- VSCode
  - VSCode作为一个编辑器，有着丰富的插件，内置终端(也就是控制台)，用于开发前端非常的方便
- IntelliJ IDEA
  - 一个JAVA的IDE

## 体系架构

- 整个项目用的是分层的架构
- 客户端发出请求由最上层开始调用至最底层
- 服务器响应请求由最底层返回给最上层
- 前端
  - vue框架下的展示层界面
  - axios库发送请求给后端控制器层(Controller)
  - axios发送请求时所带的请求体称为VO(View Object)
- 后端
  - 控制器层(Controller)
  - 业务逻辑层(BusinessLogic)
    - 业务逻辑层接口(Service)
    - 业务逻辑的具体实现(ServiceImpl)
  - 数据层(Data)
- 结构图如图所示