## Bot 信息
### 自身信息
GET /api/getSelfProfile


### 好友列表
GET /api/bot/friends

Response: type.info.User[]

相关链接：

[type.info](https://github.com/BetterQQNT/QQNTRedProtocol/blob/main/types/info.d.ts)

### 群列表
GET /api/bot/groups

Response: type.info.Group[]

相关链接：

[type.info](https://github.com/BetterQQNT/QQNTRedProtocol/blob/main/types/info.d.ts)

## 群组相关

### 设置全体禁言
POST /api/group/muteEveryone
```typescript
{
    group: 233333, // 群号
    enable: true // 是否开启
}
```

### 踢人
POST /api/group/kick
```typescript
{
    uidList: [1234567],
    group: 233333, // 群号
    refuseForever: false, // 永踢
    reason: '原因'
}
```

### 获取群公告
POST /api/group/getAnnouncements
```typescript
{
    group: 233333, // 群号
}
```

### 获取成员列表
POST /api/group/getMemberList
```typescript
{
    group: 233333, // 群号
    size: 20 // 个数
}
```

## 消息相关

### 拉取富媒体消息内容
POST /api/message/fetchRichMedia
```typescript
{
    "msgId": "7253238687216318972", // 消息 ID
    "chatType": 2, // Peer 类型
    "peerUid": "390197947", // Peer ID
    "elementId": "7253238687216318971", // 富媒体消息元素 ID
    "thumbSize": 0, // 照传即可
    "downloadType": 2 // 照传即可
}
```

Response: 直接返回对应消息元素对应的二进制；如：图片即返回图片二进制

### 上传富媒体消息内容
POST /api/upload

body: FormData file=[文件]

Response: 发送富媒体消息所需的所有信息，在 `message::send` 包中合并到 payload.elements 即可。

### 撤回
POST /api/message/recall
```typescript
{
    msgIds: ['7251111111111122069'], // 依然不建议一次传太多 还是会失败的
    peer: type.peer.Peer
}
```

相关链接：

[type.peer](https://github.com/BetterQQNT/QQNTRedProtocol/blob/main/types/peer.d.ts)

### 获取历史消息
POST /api/message/getHistory

```typescript
{
    peer: type.peer.Peer,
    offsetMsgId?: number, // 偏移，从哪条开始
    count: 100 // 数量
}
```
相关链接：

[type.peer](https://github.com/BetterQQNT/QQNTRedProtocol/blob/main/types/peer.d.ts)
