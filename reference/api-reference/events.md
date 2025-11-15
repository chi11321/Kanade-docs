---
description: 脚本间的通信。
---

# 📳 events

## Functions:

### set

**`events.set(name: string, hook: function):` **<mark style="color:purple;">`table`</mark>

| 参数   | 类型       | 描述   |
| ---- | -------- | ---- |
| name | string   | 事件名称 |
| hook | function | 回调函数 |

```lua
events.set("event1", function(msg)
    print("event1 has been called")
    
    msg = "modified"
    return msg
end)
```

在指定事件上注册钩子函数。

### call

**`events.call(name: string[, payload: any]):` **<mark style="color:purple;">`table`</mark>

| 参数      | 类型     | 描述      |
| ------- | ------ | ------- |
| name    | string | 事件名称    |
| payload | any    | 调用时携带参数 |

```lua
local cb = function(msg)
    print("msg from event1:"..msg)
    events.unset(cb)
end
events.set("event1", cb)
events.call("event1", "???")
```

在指定事件上链式调用所有钩子函数，过程应是无序的，通过HashMap实现。

### unset

**`events.unset(name: string, hook: function):` **<mark style="color:purple;">`table`</mark>

| 参数   | 类型       | 描述   |
| ---- | -------- | ---- |
| name | string   | 事件名称 |
| hook | function | 回调函数 |

```lua
local cb = function()
    print("called on event1")
    events.unset(cb)
end
events.set("event1", cb)
```

在指定事件上注销钩子函数。当前脚本已注册函数将在脚本卸载时自动注销。

## 🔗 `内置事件`

| 名称                | 描述                 | 参数                                                                                                                                                                               |
| ----------------- | ------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| unload            | 当前脚本卸载时触发（仅当前脚本触发） |                                                                                                                                                                                  |
| port\_scanned     | 端口扫描返回结果时触发钩子函数    | (host: <mark style="color:purple;">`string`</mark> ,port: <mark style="color:purple;">`number`</mark>)                                                                           |
| alive\_scanned    | 存活扫描返回结果时触发钩子函数    | (host: <mark style="color:purple;">`string`</mark>)                                                                                                                              |
| protocol\_scanned | 协议扫描返回结果时触发钩子函数    | (host: <mark style="color:purple;">`string`</mark>, port: <mark style="color:purple;">`number`</mark>,matchx: [<mark style="color:purple;">`IMatchX`</mark>](events.md#imatchx)) |
| vuln\_scanned     | 漏洞扫描返回结果时触发钩子函数    | (url: <mark style="color:purple;">`string`</mark>, vuln: <mark style="color:purple;">`string`</mark>)                                                                            |

在钩子函数上你可以修改原始返回值。

```lua
events.set("protocol_scanned", function(host, port, matchx)
    print(host, port, matchx and json.stringify(matchx) or "")
    -- 这会使所有被识别的协议都被修改为 kanade
    if matchx then matchx.data.service = "kanade" end 
    return host, port, matchx
end)
```
