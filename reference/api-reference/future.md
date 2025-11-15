---
description: 链式异步与流式回调。
---

# 📩 future

来自Future和FutureStream的回调是非阻塞的，你可以在内部运行任何异步阻塞代码同时不阻塞Lua状态主线程。

## 🔗 `Future`&#x20;

Rust异步是惰性的，需要手动启动，调用and\_then或await来启动异步任务。

### :and\_then

**`future:and_then([callback: function]):` **[<mark style="color:purple;">`Future`</mark>](future.md#future)

在异步线程中非阻塞运行并在完成时回调。

### :map\_err

**`future:map_err(callback: function):` **[<mark style="color:purple;">`Future`</mark>](future.md#future)

在错误时回调。

### :finally

**`future:finally(callback: function):` **[<mark style="color:purple;">`Future`</mark>](future.md#future)

### :await

**`future:await():` **<mark style="color:purple;">`any`</mark>

在异步线程中阻塞运行。

## 🔗 `FutureStream`&#x20;

Rust异步是惰性的，需要手动启动，调用listen来启动流式异步任务。

### :listen

**`future:listen(callback: function):` **[<mark style="color:purple;">`FutureStream`</mark>](future.md#futurestream)

在异步线程中非阻塞运行并在有结果时流式回调。

### :map\_err

**`future:map_err(callback: function):` **[<mark style="color:purple;">`FutureStream`</mark>](future.md#futurestream)

### :finally

**`future:finally(callback: function):` **[<mark style="color:purple;">`FutureStream`</mark>](future.md#futurestream)

所有任务完成时回调。
