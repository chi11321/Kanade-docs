---
description: json序列化和反序列化。
---

# 🔓 json

## Functions:

#### parse

**`json.parse(json_text: string):`** <mark style="color:purple;">`table`</mark>

| 参数         | 类型     | 描述 |
| ---------- | ------ | -- |
| json\_text | string |    |

```lua

local raw = [[
{
        "name": "vuln scan",
        "available":    true
}]]
local j_meta = raw:json()                -- 通过string:json()元方法调用
local j = json.parse(raw)
for k, v in pairs(j_meta)do
        print(k, v)
end
```

反序列化json格式数据。

#### stringify

**`json.stringify(data: any):`** <mark style="color:purple;">`string`</mark>

| 参数   | 类型    | 描述 |
| ---- | ----- | -- |
| data | table |    |

```lua
print(json.stringify({name = "vuln scan", available = true}))
```

将table以yaml格式序列化。
