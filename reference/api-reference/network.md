---
description: 发送异步网络请求。
---

# ☁️ network

## Functions:

### http

**`network.http(url: string[, params: table]):`** [<mark style="color:purple;">`Future`</mark>](future.md#future)

| 参数   | 类型                                         | 描述     |
| ------ | -------------------------------------------- | -------- |
| url    | string                                       |          |
| params | table([HttpOptions](network.md#httpoptions)) | 请求参数 |

```lua
network.http("https://www.baidu.com/", {
    method = "post",			-- 允许 get/post/put/delete 方法		
    headers = {
    	["test-header"] = "1",
    	h2 = 2,
    	-- ["content-type"] = "application/json"	-- 手动设置content-type
    },
    -- body = "test-body",
    body = json.stringify({
    	test = 1
    })
}):and_then(function(res)
    print(res.status)
    print(res.body)
    for k, v in pairs(res.headers) do
        print(k, v)
    end
end):map_err(function(err)
    print(err)
end)
```

http(s)请求。

### proxy

**`network.proxy(url: string[, timeout: number]):`** <mark style="color:purple;">`Proxy`</mark>

| 参数    | 类型   | 描述                 |
| ------- | ------ | -------------------- |
| url     | string | socks4\|socks5\|http |
| timeout | number | 超时(毫秒)           |

```lua
local proxier = network.proxy("socks5://127.0.0.1:7897")

proxier:http("https://www.baidu.com/"):and_then(function(res)
	print(res.body)
end):map_err(function(e)
    print(e)
end)

proxier:websocket("wss://toolin.cn/echo"):and_then(function(ws)
	ws:listen(function(msg)
		print(msg.packet, msg.msg)
	end)
	ws:write("Test", 0)
	ws:write("Test2", 0)
	print("connected")

	ws:close()
end):map_err(function(err)
	print(err)
end)
```

代理客户端，继承所有network方法（除了自身和http\_client）。

### socket

**`network.socket(url: string[, timeout: number]):`** [<mark style="color:purple;">`Future`</mark>](future.md#future)

| 参数    | 类型   | 描述       |
| ------- | ------ | ---------- |
| url     | string |            |
| timeout | number | 超时(毫秒) |

socket tcp客户端。

### tls\_socket

**`network.tls_socket(url: string[, skip_verify: bool, timeout: number]):`** [<mark style="color:purple;">`Future`</mark>](future.md#future)

tls socket tcp客户端。

### http\_client

**`network.http_client([proxy: string, timeout: number]):`** [<mark style="color:purple;">`HttpClient`</mark>](network.md#httpclient)

创建一个干净的http客户端。

### websocket

**`network.websocket(url: string [, timeout: number]):`** [<mark style="color:purple;">`Future`</mark>](future.md#future)

| 参数    | 类型   | 描述       |
| ------- | ------ | ---------- |
| url     | string |            |
| timeout | number | 超时(毫秒) |

```lua
network.websocket("wss://toolin.cn/echo"):and_then(function(ws)
	ws:listen(function(msg)
		print(msg.packet, msg.msg)
	end)
	ws:write("Test", 0)
	ws:write("Test2", 0)
	print("connected")

	ws:close()
end):map_err(function(err)
	print(err)
end)
```

websocket客户端。

## Structs:

### 🔗 `HttpClient`

#### :request

**`client:request(url: string[, params: table]):`** [<mark style="color:purple;">`Future`</mark>](future.md#future)

### 🔗 `HttpOptions`

| 名称    | 类型        | 描述 |
| ------- | ----------- | ---- |
| method  | string\|nil |      |
| headers | table\|nil  |      |
| body    | string\|nil |      |
| timeout | number\|nil |      |

### 🔗 `SocketStream`

#### :read

**`socket:read(size: number):`** [<mark style="color:purple;">`Future`</mark>](future.md#future)

| 参数   | 类型     | 描述   |
| ---- | ------ | ---- |
| size | number | 读取长度 |

读取原始回复。

#### :write

**`ws:write(content: string):`** [<mark style="color:purple;">`Future`</mark>](future.md#future)

| 参数      | 类型     | 描述   |
| ------- | ------ | ---- |
| content | string | 发送内容 |

写入数据。

#### :close

**`socket:close()`**

关闭连接。

#### :write\_all

**`ws:write_all(content: string):`** [<mark style="color:purple;">`Future`</mark>](future.md#future)

| 参数      | 类型     | 描述   |
| ------- | ------ | ---- |
| content | string | 发送内容 |

写入所有数据。

#### :read\_to\_string

**`socket:read_to_string(size: number):`** [<mark style="color:purple;">`Future`</mark>](future.md#future)

| 参数   | 类型     | 描述   |
| ---- | ------ | ---- |
| size | number | 读取长度 |

读取字符串回复。

### 🔗 `WebSocketStream`

#### :read

**`ws:read():`** [<mark style="color:purple;">`Future`</mark>](future.md#future)

读取回复。

#### :write

**`socket:write(content: string, packet: e_WSmsgType):`** [<mark style="color:purple;">`Future`</mark>](future.md#future)

| 参数      | 类型                                | 描述   |
| ------- | --------------------------------- | ---- |
| content | string                            | 发送内容 |
| packet  | [WSmsgType](network.md#wsmsgtype) | 数据类型 |

写入数据。

#### :close

**`ws:close()`**

关闭连接。

#### :listen

**`socket:listen(callback: function)`**

| 参数       | 类型       | 描述 |
| -------- | -------- | -- |
| callback | function |    |

## Enumerates:

### 🔗 `WSmsgType`

| 值 | 描述     |
| - | ------ |
| 0 | text   |
| 1 | binary |
| 2 | ping   |
| 3 | pong   |
| 4 | close  |
| 5 | frame  |
