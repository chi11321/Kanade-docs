# 插件

```lua
-- 通过事件触发处理函数，每次事件被触发时会调用所有已注册回调函数
local handle = function(host, port, finger)
    if finger == "http" then
        network.request("http://"..host..":"..port, function(err, res)
            if err then
                print(res)
                return
            end
            print(res.status)
            print(res.body)
            for k, v in pairs(res.headers) do
                print(k, v)
            end
        end)
    end
end

events.set("finger_scanned", handle)
events.set("unload", function()            -- 卸载插件
    events.unset("finger_scanned", handle)
end)
```
