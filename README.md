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

见 (WebSocket 部分)[./websocket.md]

## 3. HTTP API

见 (HTTP 部分)[./http.md]
