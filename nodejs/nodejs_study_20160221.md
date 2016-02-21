### Node.js学习笔记 2016-02-21
##### Node.js的特点
- 事件驱动
- 非阻塞I/O
- 轻量、可伸缩
- 单线程

##### Node.js的优点
- 事件驱动、非阻塞决定了可以处理高并发
- 事件驱动其中使用了`libeio`模块决定了-可以处理IO密集型操作，还是用了另一个异步操作的模块`libev`
- 单线程 - 这就避免了和多线程切换上下文而消耗内存的缺点，但是单线程难道就对多核cpu使用不充分么？对多核机器存在浪费使用么？答案：错误，Node.js为了处理这个问题提供了`cluster`模块,当然还有其他的现成的包 pm2 或者 forever

##### Node.js的缺点
- 不适合cpu密集型算法

##### Node.js常用的框架

- express (时下很流行)
- koajs (下一代nodejs的框架)
- sails (和rails差不多)

##### Node.js远程部署

- Capistrano
- pm2
- mina

##### Node.js常用的包
- supervisor - 方便测试的包，自动重启的包
- pm2 - 部署的包
- forever - 部署的包
- grunt - 任务管理的包
- gulp - 基于流的任务管理的包
- eventproxy - 处理异步的包
- async - 也是处理异步的包
- log4js - 处理日志的包
- tracer - 处理日志的包
- redis - redis
- monogoose - mongodb数据库的module
- socket.io - websocket
- request - http请求的包
- cron - 定时任务的包
- underscore - js工具库
- moment - 日期工具库
- mocha - 单元测试
- coffee-script - 使用coffee 语法来开发
- amqplib - 使用rabbit-mq的包

##### 小结
总体使用node.js个人感觉非常好玩，也非常易于开发



