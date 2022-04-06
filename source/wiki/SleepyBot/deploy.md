---
layout: wiki
wiki: SleepyBot
title: Deployment
order: 1
---

目前只支持直接从工程部署/打包之后运行,毕竟也就只有我自己需要部署啦……

## Prerequisite

- 一个运行并登录了QQ帐号的[Mirai](https://github.com/mamoe/mirai)实例并安装[Mirai-Api-Http](https://github.com/project-mirai/mirai-api-http)
- 一个[Redis](https://redis.io/)数据库，如果是Windows环境使用平替[Memurai](https://www.memurai.com/)

## Deploy

在项目中创建一个新的`Secret.cs`，把`Program.cs`下面的Secret部分复制进去Uncomment然后填好，需要填的内容有：

|Key|Value|
|---|-----|
|VerifyKey|Mirai的Verify key|
|BotId|用作机器人的QQ号|
|MiraiHost|部署了Mirai的服务器IP地址|
|MiraiPort|Mirai-Api-Http监听的Http&WebSocket端口|
|RedisEndpoint|Redis接入终端，`ip:port`|
|RedisAuthKey|Redis密码|
|DevId|开发者（Admin）的QQ号，只有这个QQ号才能使用测试指令|

## Initialisation

在机器人第一次启动后，可以运行一些管理员指令进行初始化或缓存，提高使用时的响应速度。
例如`Test:DBConnection`可以先将机器人连接到Redis，如果Redis也是第一次使用可以先用一些Crawler指令缓存数据，之后收到指令就不需要现爬。
