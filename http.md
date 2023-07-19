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
