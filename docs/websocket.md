
### 包格式

```js
{
    type: 'meta::connect', // 包类型
    payload: { // 包载荷
      
    }
}
```

例如：当你想发送一个类型为 `meta::connect`，载荷为 `{ "token": "123456" }` 的包，你需要发送：
```typescript
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

```typescript
{
  token: "TOKEN"
}
```

-----------

#### `meta::connect` ⬆️
发回协议端信息

```typescript
{
    version: '1.0.0',
    name: 'red-protocol',
    authData: type.auth.AuthData
}
```

相关链接：

[type.auth](https://github.com/BetterQQNT/QQNTRedProtocol/blob/main/types/auth.d.ts)

-----------

#### `message::recv` ⬇️
接收消息

```typescript
type.message.Message
```

相关链接：

[type.message](https://github.com/BetterQQNT/QQNTRedProtocol/blob/main/types/message.d.ts)

-----------

#### `message::send` ⬆️
发送消息

```typescript
{
    peer: type.peer.Peer,
    elements: type.message.Element[]
}
```

相关链接：

[type.message](https://github.com/BetterQQNT/QQNTRedProtocol/blob/main/types/message.d.ts)

[type.peer](https://github.com/BetterQQNT/QQNTRedProtocol/blob/main/types/peer.d.ts)

使用例：[issue/1](https://github.com/BetterQQNT/QQNTRedProtocol/issues/1)