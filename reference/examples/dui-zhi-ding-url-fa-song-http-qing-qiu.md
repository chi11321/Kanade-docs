# 对指定URL发送HTTP请求

```lua
local example = menu.create("Example", "Example", "Example")
local url_item = example:input("键入URL", "")
example:button("发送一个GET请求"):set_callback(function()
    network.http(url_item:get(), function(err, res)
        if err then return end
        print(res.status, json.stringify(res.headers), res.body)
    end)
end)
```
