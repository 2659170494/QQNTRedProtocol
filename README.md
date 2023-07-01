# RedProtocol

此仓库阐明了关于 BetterQQNT 功能 RedProtocol 的协议细则。

## 1. 基本

RedProtocol 提供方会提供一个 WebSocket 和 HTTP 合并的服务，当前默认打开在本机端口 16530。

WebSocket 部分：`ws://localhost:16530/`
HTTP 部分：`http://localhost:16530/api/`

### 1.1 认证
WebSocket:

  `meta::connect` 包
  
HTTP:

  HEADER 内 `Authorization` 项： `Bearer TOKEN`
  

## 2. WebSocket 包

### 包格式

```js
{
    type: 'meta::connect', // 包类型
    payload: { // 包载荷
      
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



