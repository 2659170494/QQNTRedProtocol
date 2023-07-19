
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