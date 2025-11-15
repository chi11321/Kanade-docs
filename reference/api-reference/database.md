---
description: 通过统一接口异步访问各类数据库。
---

# 🗳️ database

### 此接口在Kanade Version>=0.0.6开放。

## Functions:

### mysql

**`database.mysql(url: string, callback: function):`**[<mark style="color:purple;">`Future`</mark>](future.md#future)

**参数:**

| 名称  | 类型     | 描述 |
| --- | ------ | -- |
| url | string |    |

```lua
database.mysql("mysql://root:123456@127.0.0.1:3306/mysql"):and_then(function (conn)
    local res = conn:query("SELECT version()"):await()
    for k, v in pairs(res[1]) do
        print(k, v)
    end

    conn:close()
end):map_err(function (e)
    print(e)
end)
```

mysql客户端。

### postgres

**`database.postgres(url: string, callback: function):`**[<mark style="color:purple;">`Future`</mark>](future.md#future)

**参数:**

| 名称  | 类型     | 描述 |
| --- | ------ | -- |
| url | string |    |

```lua
database.postgres("postgres://myuser:mypassword@127.0.0.1:5432/mydatabase"):and_then(function (conn)
    local res = conn:query("SELECT version()"):await()
    for k, v in pairs(res[1]) do
        print(k, v)
    end

    conn:close()
end):map_err(function (e)
    print(e)
end)
```

postgres客户端。

### mssql

**`database.mssql(url: string, callback: function):`**[<mark style="color:purple;">`Future`</mark>](future.md#future)

**参数:**

| 名称  | 类型     | 描述 |
| --- | ------ | -- |
| url | string |    |

```lua
database.mssql("mssql://sa:tachibana_kanade@127.0.0.1:1433/master"):and_then(function (conn)
    local res = conn:query("SELECT @@VERSION"):await()
    for k, v in pairs(res[1]) do
        print(k, v)
    end
    
    conn:close()
end):map_err(function (e)
    print(e)
end)
```

mssql客户端。

### redis

**`database.redis(url: string, callback: function):`**[<mark style="color:purple;">`Future`</mark>](future.md#future)

**参数:**

| 名称  | 类型     | 描述 |
| --- | ------ | -- |
| url | string |    |

```lua
-- 无认证
local redis = database.redis("redis://127.0.0.1:6379/")
-- 仅密码认证
local redis = database.redis("redis://:123@127.0.0.1:6379/")
-- 用户名密码认证
local redis = database.redis("redis://user:123@127.0.0.1:6379/")


redis:and_then(function(conn)
    local res = conn:query("INFO"):await()
    print(json.stringify(res))
end):map_err(function (e)
    print(e)
end)
```

redis客户端。

## 🔗 `DatabaseConnection`

### :query

**`dbc:read(query: string):`**[<mark style="color:purple;">`Future`</mark>](future.md#future)

**参数:**

| 名称    | 类型     | 描述      |
| ----- | ------ | ------- |
| query | string | 查询语句/命令 |

执行SQL查询或执行命令。

### :close

**`dbc:close()`**

关闭连接。连接的关闭是异步的，你不需要担心它何时能够关闭，只需继续执行你的脚本逻辑即可，当连接关闭处理完成后，你将无法再使用query方法。redis的连接无需手动关闭，由lua gc和rust所有权自动回收销毁，如果你想要立即标记对象可回收，将当前DatabaseConnection值设定为nil即可。

### :type

**`dbc:type():`**<mark style="color:purple;">`string`</mark>
