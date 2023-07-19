# RedProtocol

此仓库阐明了关于 BetterQQNT 功能 RedProtocol 的协议细则。

## 1. 基本

RedProtocol 提供方会提供一个 WebSocket 和 HTTP 合并的服务，当前默认打开在本机端口 16530，你也可以通过指定 `--red-protocol-port` 参数来更改端口号。

RedProtocol 使用数字 ID（Uin）。

WebSocket 部分：`ws://localhost:16530/`
HTTP 部分：`http://localhost:16530/api/`

### 1.1 认证
TOKEN 被默认存储在 `%AppData%/BetterUniverse/QQNT/RED_PROTOCOL_TOKEN` 或 `~/BetterUniverse/QQNT/RED_PROTOCOL_TOKEN`，若无 TOKEN ，在启用 RedProtocol 时将会自动生成。

WebSocket:

  [`meta::connect` 包](https://github.com/BetterQQNT/RedProtocol/#metaconnect-%EF%B8%8F)
  
HTTP:

  在每次请求时候，在 HEADER 内携带 `Authorization` ： `Bearer TOKEN`
  

## 2. WebSocket 包

### 包格式

```js
{
    type: 'meta::connect', // 包类型
    payload: { // 包载荷
      
    }
}
```

例如：当你想发送一个类型为 `meta::connect`，载荷为 `{ "token": "123456" }` 的包，你需要发送：
```ts
{
    "type": "meta::connect",
    "payload": { 
       "token": "123456"
    }
}
```

### 包类型

> 以下 ⬇️ 表示 提供方 下发到 客户端 的包，⬆️ 表示 客户端 上发到 提供方 的包。
>
> type.filename.interface 表示为此部分的定义存在于 `filename` 文件内的对应 `interface` 中。

#### `meta::connect` ⬇️
连接到 WebSocket 客户端

```ts
{
  token: "TOKEN"
}
```

#### `meta::connect` ⬆️
协议端信息

```ts
{
    version: '1.0.0',
    name: 'red-protocol',
    authData: type.auth.AuthData
}
```

#### `group::mute` ⬆️
设置禁言

```ts
{
    "group": "群ID",
    "memList": [
        {
            "uin": "10086"
            "uid": "u_ki2jd_LWVRwFCrxEVKD8hQ", // uin/uid 二选一
            "timeStamp": 60 // 以秒为单位的时间
        }, ...others
    ]
}
```

## 3. HTTP API

### 设置全体禁言
POST /api/group/muteEveryone
```ts
{
    group: uin,
    enable: true // 是否开启
}
```

### 踢人
POST /api/group/kick
```ts
{
    uidList: [1234567],
    group: 233333,
    refuseForever: false, // 永踢
    reason: ' 原因 '
}
```

### 撤回
POST /api/message/recall
```ts
{
    msgIds: ['7251111111111122069'], // 依然不建议一次传太多 还是会失败的
    peer: 一般 Peer 格式
}
```
