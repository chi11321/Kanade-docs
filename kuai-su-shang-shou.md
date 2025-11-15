# 📲 快速上手

## 运行你的第一个Lua脚本

将编写完成的Lua脚本存放在"～/.kanade\_scripts/"文件夹中，并在Kanade左侧找到"脚本"选项卡，运行你刚刚编写的脚本！

```lua
print("Hello Kanade!")
```

## 安全性

Kanade并没有为Lua脚本添加安全检查，通过LuaJIT模块，脚本能够调用系统API，恶意脚本能够通过此方式在您的机器上执行任意代码，或是直接通过os.execute执行命令，因此<mark style="color:orange;">**请使用从信任来源获取的脚本**</mark>，Kanade不为Lua脚本造成的任何后果负责。

## 其他有用的信息

1.API中使用"\[]"标注的参数是可选的。

2.大部分可选参数是可跳过的，例如在回调函数之前的可选参数。

3.Kanade内置的Lua解释器支持LuaJIT2.1.0/FFI/bit，[有关FFI的更多有关信息在此处找到。](https://luajit.org/ext_ffi_api.html)

4.Lua解释器包含如下基本库。

* base
* math
* string
* debug
* package
* os
* io
* ffi
* bit
