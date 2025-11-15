# ⌚ common

## Functions:

### async

**`common.async(func: function):`** [<mark style="color:purple;">`Future`</mark>](future.md#future)

| 参数   | 类型       | 描述 |
| ---- | -------- | -- |
| func | function |    |

创建Future包装。

### sleep

**`common.sleep(millis: u64):`** [<mark style="color:purple;">`Future`</mark>](future.md#future)

| 参数     | 类型  | 描述       |
| ------ | --- | -------- |
| millis | u64 | 睡眠时长(毫秒) |

在当前线程中异步睡眠。

### notify

**`common.nofity(type: NotifyType, msg: string)`**

| 参数   | 类型                                   | 描述   |
| ---- | ------------------------------------ | ---- |
| type | [NotifyType](common.md#e_notifytype) | 通知类型 |
| msg  | string                               | 通知内容 |

在客户端上发送全局通知。

## Variables:

| 名称                   | 描述                 |
| ---------------------- | -------------------- |
| lua\_path              | lua文件夹路径        |
| nuclei\_template\_path | nuclei模板文件夹路径 |

## 🔗 `NotifyType`

| 值 | 描述   |
| - | ---- |
| 0 | info |
| 1 | succ |
| 2 | err  |
| 3 | warn |
