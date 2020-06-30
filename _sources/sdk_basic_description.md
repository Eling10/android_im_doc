# SDK基本说明

## 核心类介绍

| 类 | 介绍 | 功能 |
| :-----| :----- | :----- |
|ELClient |	客户端 |	单例对象，负责整个SDK的初始化及IM相关的配置 |
|ELUserManager |	用户管理类 |	管理当前登录的用户信息 |
|ELLoginManager |	登录管理类 |	负责IM的注册、登录、登出相关的操作 |
|ELChatManager|管理 |	负责聊天相关的操作，支持单聊和群聊 |
|ELGroupManager |	群组管理类 |	管理与群相关的业务逻辑（查询、创建、解散、修等）|
|ELContactManager |	联系人管理类 |	负责好友的查询、添加、删除等相关的逻辑 |
|ELCallManager |	音视频通话管理类 |	可以进行1v1的音视频通话 |

