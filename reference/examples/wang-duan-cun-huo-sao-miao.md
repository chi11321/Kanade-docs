# 网段存活扫描

```lua
local g = menu.create("扫描器", "存活扫描", "General")

local hosts = g:input("Hosts", "")
hosts:tooltip("CIDR格式:192.168.0.0/24")
local scan_btn = g:button("开始扫描")
local res = g:list("扫描结果", {"暂无结果"})
res:rows(16)

menu.set_icon("扫描器", {"fas", "code", "xs"})

scan_btn:set_callback(function()
    local alive = {}
    scan_btn:loading(true)
    res:loading(true)
    scan.alive(hosts:get(), function(err, host)
        print(err, host)
        if not err then
            table.insert(alive, host)
            res:set(alive)
        end
    end, function()
        scan_btn:loading(false)
        res:loading(false)
    end, 3000)
end)

```
