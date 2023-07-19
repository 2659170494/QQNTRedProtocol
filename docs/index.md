# RedProtocol

此仓库阐明了关于 BetterQQNT 功能 RedProtocol 的协议细则。

## 1. 基本

RedProtocol 提供方会提供一个 WebSocket 和 HTTP 合并的服务，当前默认打开在本机端口 16530，你也可以通过指定 `--red-protocol-port` 参数来更改端口号。

RedProtocol 使用数字 ID（Uin）。

WebSocket 部分：`ws://localhost:16530/`
HTTP 部分：`http://localhost:16530/api/`

### 1.1 认证

TOKEN 被默认存储在 `%AppData%/BetterUniverse/QQNT/RED_PROTOCOL_TOKEN` 或 `~/BetterUniverse/QQNT/RED_PROTOCOL_TOKEN`。

若无 TOKEN ，在启用 RedProtocol 时将会自动生成。

认证方式：

WebSocket:

  [`meta::connect` 包](https://betterqqnt.github.io/RedProtocol/websocket/#metaconnect)
  
HTTP:

  每次请求时，在 HEADER 内携带 `Authorization`： `Bearer TOKEN`

## 2. WebSocket 包

> 注意：此部分使用的 JSON 都为类 TypeScript 的简写，请传入正确的 JSON 而不是此类简写

见 [WebSocket 部分](https://betterqqnt.github.io/RedProtocol/websocket)

## 3. HTTP API

> 注意：此部分使用的 JSON 都为类 TypeScript 的简写，请传入正确的 JSON 而不是此类简写

见 [HTTP 部分](https://betterqqnt.github.io/RedProtocol/http)
