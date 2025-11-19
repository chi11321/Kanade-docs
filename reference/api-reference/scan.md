---
description: 高性能的存活检测，端口扫描和指纹识别接口。
---

# 📸 scan

## Functions:

### alive

**`scan.alive(hosts: string, [timeout: number]):`** [<mark style="color:purple;">`FutureStream`</mark>](future.md#futurestream)

| 参数    | 类型   | 描述                       |
| ------- | ------ | -------------------------- |
| hosts   | string | CIDR格式地址               |
| timeout | number | 超时时间（毫秒），默认5000 |

```lua
scan.alive("192.168.31.0/24"):listen(function(res)
    if res.details.ok then
        print("Alive:", res.details.host)
    end
end):map_err(function(e)
    print(e)
end):finally(function()
    print("Completed")
end)
```

ICMP存活扫描。

### port

**`scan.port(host: string, ports: table, [protocol_scan: bool, vuln_scanners: number, timeout: number]):`** [<mark style="color:purple;">`FutureStream`</mark>](future.md#futurestream)

| 参数           | 类型   | 描述                                                         |
| -------------- | ------ | ------------------------------------------------------------ |
| host           | string |                                                              |
| ports          | table  | 端口列表                                                     |
| protocol\_scan | bool   | 启用协议扫描                                                 |
| vuln\_scanners | number | 启用的漏洞扫描器，协议扫描未启用时不开启漏洞扫描。应根据[VulnScanType](scan.md#vulnscantype)相加获取最终值。 |
| timeout        | number | 超时时间（毫秒），默认5000                                   |

```lua
scan.port("192.168.31.1", scan.port.web, true, scan.vuln.ssh + scan.vuln.web):listen(function(res)
    print(json.stringify(res))
end):map_err(function(e)
    print(e)
end):finally(function()
    print("completed")
end)
```

端口扫描。

### vuln

**`scan.vuln(host: string, port: number(u16)[, scanners: number, timeout: number]):`** [<mark style="color:purple;">`Future`</mark>](future.md#future)

跳过协议扫描，强制使用指定的漏洞扫描器进行扫描。

### nuclei

**`scan.nuclei(cfg: table):`** [<mark style="color:purple;">`FutureStream`</mark>](future.md#futurestream)

| 参数 | 类型                                                | 描述 |
| ---- | --------------------------------------------------- | ---- |
| cfg  | table([NucleiScanConfig](scan.md#nucleiscanconfig)) |      |

nuclei模板扫描。nuclei扫描是非常消耗内存资源的操作，模板加载并不是复用的，应在单个扫描线程中选中更多扫描目标，而不是为少量目标单独创建多个扫描线程。

为[Kanade的nuclei运行时libnuclei](https://github.com/chi11321/nuclei/tree/main)贡献并发扫描代码，根据重要程度可以获得不同时长Kanade订阅。

### port\_range

**`scan.port(host: string, start: number(u16), end: number(u16), [protocol_scan: bool, vuln_scanners: number, timeout: number]):`** [<mark style="color:purple;">`FutureStream`</mark>](future.md#futurestream)

指定范围端口扫描。

## Variables:

### port

**`scan.port:`** [<mark style="color:purple;">`PortScanner`</mark>](scan.md#portscanner)

**`scan.vuln:`** [<mark style="color:purple;">`VulnScanner`</mark>](scan.md#vulnscanner)

## Structs:

### 🔗 `PortScanner`

| 名称         | 类型    | 描述   |
| ---------- | ----- | ---- |
| all        | table | 全部端口 |
| common     | table |      |
| web        | table |      |
| database   | table |      |
| network    | table |      |
| high\_rist | table |      |
| not        | table |      |

### 🔗 `VulnScanner`

| 名称       | 类型     |
| -------- | ------ |
| all      | number |
| ssh      | number |
| web      | number |
| database | number |

### 🔗 `NucleiScanConfig`

| 名称 | 类型 |
| ---- | ---- |
|      |      |
|      |      |
|      |      |
|      |      |

### 🔗 `ScanResult`

| 名称      | 类型                                                                                                                                                                               |
| ------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| type    | [ScanResultType](scan.md#scanresulttype)                                                                                                                                         |
| details | [AliveScanResult](scan.md#alivescanresult)\|[PortScanResult](scan.md#portscanresult)\|[ProtocolScanResult](scan.md#protocolscanresult)\|[VulnScanResult](scan.md#vulnscanresult) |

### 🔗 `AliveScanResult`

| 名称   | 类型          | 描述 |
| ---- | ----------- | -- |
| host | string      |    |
| ok   | boolean     |    |
| err  | string\|nil |    |

### 🔗 `PortScanResult`

| 名称 | 类型        | 描述 |
| ---- | ----------- | ---- |
| host | string      |      |
| port | number(u16) |      |
| open | boolean     |      |

### 🔗 `ProtocolScanResult`

| 名称   | 类型                          | 描述 |
| ------ | ----------------------------- | ---- |
| host   | string                        |      |
| port   | number(u16)                   |      |
| matchx | [MatchX](scan.md#matchx)\|nil |      |

### 🔗 `VulnScanResult`

| 名称 | 类型                                 | 描述                                                         |
| ---- | ------------------------------------ | ------------------------------------------------------------ |
| type | [VulnScanType](scan.md#vulnscantype) |                                                              |
| host | string                               |                                                              |
| port | number(u16)                          |                                                              |
| vuln | table                                | 类型太多了，并且计划支持自定义协议的扫描器，写不过来建议用json序列化看一下每个VulnInfo的结构 |

### 🔗 `MatchX`

| 名称   | 类型                                                     |
| ---- | ------------------------------------------------------ |
| type | string                                                 |
| data | [Match](scan.md#match)\|[SoftMatch](scan.md#softmatch) |

### 🔗 `Match`

| 名称          | 类型                                 |
| ----------- | ---------------------------------- |
| service     | string                             |
| pattern     | string                             |
| versioninfo | [VersionInfo](scan.md#versioninfo) |

### 🔗 `SoftMatch`

| 名称      | 类型     |
| ------- | ------ |
| service | string |
| pattern | string |

### 🔗 `VersionInfo`

| 名称  | 类型     |
| --- | ------ |
| p   | string |
| v   | string |
| h   | string |
| i   | string |
| o   | string |
| cpe | string |

### 🔗 `NucleiMessage`

| 名称      | 类型              |
| --------- | ----------------- |
| type      | NucleiMessageType |
| timestamp | number            |
| data      | any               |

## Enumerates:

### 🔗 `VulnScanType`

| 值   | 描述       |
| --- | -------- |
| 0x0 | NONE     |
| 0x1 | WEB      |
| 0x2 | SSH      |
| 0x3 | DATABASE |

### 🔗 `ScanResultType`

| 值 | 描述        |
| - | --------- |
| 0 | ALIVE     |
| 1 | PORT      |
| 2 | PROTOCOL  |
| 3 | VULN      |
| 4 | COMPLETED |

### 🔗 `NucleiMessageType`

| 值   | 描述     |
| ---- | -------- |
| 0    | LOG      |
| 1    | RESULT   |
| 2    | ERROR    |
| 3    | PROGRESS |
| 4    | STATUS   |
| 5    | TEMPLATE |

