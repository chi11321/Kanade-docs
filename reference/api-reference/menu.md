---
description: 图形化交互。
---

# 💻 menu

## Functions:

### create

**`menu.create(category: string, tab: string, group: string):`** [<mark style="color:purple;">`MenuGroup`</mark>](menu.md#menugroup)

| 参数       | 类型     | 描述 |
| -------- | ------ | -- |
| category | string |    |
| tab      | string |    |
| group    | string |    |

创建新交互组。

### set\_icon

**`menu.create(category: string, ctx: table):`** [<mark style="color:purple;">`MenuGroup`</mark>](menu.md#menugroup)

| 参数       | 类型     | 描述 |
| -------- | ------ | -- |
| category | string |    |
| ctx      | table  |    |

```lua
local script_group = menu.create("脚本", "Scripts", "Scripts")
menu.set_icon("脚本", {"far", "file", "xs"})        -- ctx{type, name, size}
menu.set_icon("设置", {"far", "heart", "xs"})
```

重绘Category图标。[有关图标的信息在此处找到](https://fontawesome.com/search)(仅免费图标)。

### set\_context\_menu

**`menu.set_context_menu(built_in: BuiltInContextMenu, name: string, callback: function)`**

| 参数        | 类型                                                 | 描述 |
| --------- | -------------------------------------------------- | -- |
| built\_in | [BuiltInContextMenu](menu.md#e_builtincontextmenu) |    |
| name      | string                                             |    |
| callback  | function                                           |    |

```lua
menu.set_context_menu("fofa_result_table", "打印到控制台", function(selected)
    print(selected)
end)
```

注册右键菜单。

## Structs:

### 🔗  `MenuGroup`

#### :list

**`tab:table(name: string, value: table):`** [<mark style="color:purple;">`MenuItem`</mark>](menu.md#menuitem)

| 参数    | 类型     | 描述 |
| ----- | ------ | -- |
| name  | string |    |
| value | table  |    |

```lua
local example = menu.create("Example", "Example", "Example")
local list = example:list("List", {"item1", "item2", "item3"})
```

在标签页上创建List。

#### :table

**`tab:table(name: string, columns: table, data: table):`** [<mark style="color:purple;">`MenuItem`</mark>](menu.md#menuitem)

| 参数      | 类型     | 描述     |
| ------- | ------ | ------ |
| name    | string |        |
| columns | table  | 数据定义字段 |
| data    | table  |        |

```lua
local example = menu.create("Example", "Example", "Example")
local tbl = example:table("Table", {"name", "age", "address"}, {
    {
        name = "Kanade",
        age = "unknown",
        address = "void"
    },
    {
        name = "Chill",
        age = "21",
        address = "localhost"
    }
})
```

在标签页上创建Table。

#### :input

**`tab:input(name: string[, value: string, width: number]):`** [<mark style="color:purple;">`MenuItem`</mark>](menu.md#menuitem)

| 参数    | 类型     | 描述             |
| ----- | ------ | -------------- |
| name  | string |                |
| value | string | 默认值            |
| width | number | 元素宽度(百分制0-100) |

```lua
local example = menu.create("Example", "Example", "Example")
local input = example:input("Input", "")
```

在标签页上创建Input。

#### :label

**`tab:input(name: string):`** [<mark style="color:purple;">`MenuItem`</mark>](menu.md#menuitem)

| 参数   | 类型     | 描述 |
| ---- | ------ | -- |
| name | string |    |

```lua
local example = menu.create("Example", "Example", "Example")
local label = example:label("Label1")
```

在标签页上创建Label。

#### :slider

**`tab:slider(name: string, min: number, max: number, value: number[, unit: string, width: number]):`** [<mark style="color:purple;">`MenuItem`</mark>](menu.md#menuitem)

| 参数    | 类型     | 描述             |
| ----- | ------ | -------------- |
| name  | string |                |
| min   | number | 最小值            |
| max   | number | 最大值            |
| value | number | 默认值            |
| unit  | string | 在尾部显示的单位       |
| width | number | 元素宽度(百分制0-100) |

```lua
local example = menu.create("Example", "Example", "Example")
local slider = example:slider("Slider", 0, 100, 5, "个")
```

在标签页上创建Slider。

#### :select

**`tab:select(name: string, value: string, options: table[, width: number]):`** [<mark style="color:purple;">`MenuItem`</mark>](menu.md#menuitem)

| 参数      | 类型     | 描述             |
| ------- | ------ | -------------- |
| name    | string |                |
| options | table  | 选项             |
| value   | string | 默认值            |
| width   | number | 元素宽度(百分制0-100) |

```lua
local example = menu.create("Example", "Example", "Example")
local dropdown = example:select("Dropdown", {"Option1", "Option2", "Option3"}, "Option1")
```

在标签页上创建Dropdown select。

#### :switch

**`tab:switch(name: string[, value: boolean]):`** [<mark style="color:purple;">`MenuItem`</mark>](menu.md#menuitem)

| 参数    | 类型      | 描述 |
| ----- | ------- | -- |
| name  | string  |    |
| value | boolean |    |

```lua
local example = menu.create("Example", "Example", "Example")
local switch = example:switch("Switch", true)
```

在标签页上创建Switch。

#### :button

**`tab:button(name: string):`** [<mark style="color:purple;">`MenuItem`</mark>](menu.md#menuitem)

| 参数   | 类型     | 描述 |
| ---- | ------ | -- |
| name | string |    |

```lua
local example = menu.create("Example", "Example", "Example")
local button = example:button("Button")
```

在标签页上创建Button。

#### :input\_area

**`tab:input_area(name: string[, value: string, width: number]):`** [<mark style="color:purple;">`MenuItem`</mark>](menu.md#menuitem)

| 参数    | 类型     | 描述             |
| ----- | ------ | -------------- |
| name  | string |                |
| value | string | 默认值            |
| width | number | 元素宽度(百分制0-100) |

```lua
local example = menu.create("Example", "Example", "Example")
local area = example:input_area("Input something...")
```

在标签页上创建InputArea。

#### :multi\_select

**`tab:multi_select(name: string, value: table, options: table[, width: number]):`** [<mark style="color:purple;">`MenuItem`</mark>](menu.md#menuitem)

| 参数      | 类型     | 描述             |
| ------- | ------ | -------------- |
| name    | string |                |
| options | table  | 选项             |
| value   | table  | 默认值            |
| width   | number | 元素宽度(百分制0-100) |

```lua
local example = menu.create("Example", "Example", "Example")
local multi_select = example:multi_select("Multi Select", {"Option1", "Option2"}, {})
```

在标签页上创建Multi select。

#### :button\_select

**`tab:button_select(name: string, value: string, options: table[, width: number]):`** [<mark style="color:purple;">`MenuItem`</mark>](menu.md#menuitem)

| 参数      | 类型     | 描述             |
| ------- | ------ | -------------- |
| name    | string |                |
| value   | string | 默认值            |
| options | table  | 选项             |
| width   | number | 元素宽度(百分制0-100) |

```lua
local example = menu.create("Example", "Example", "Example")
local button_select = example:button_select("Button Select", "", {"Option1", "Option2"})
```

在标签页上创建Button select。

### 🔗 `MenuItem`

#### :get

**`item:get():`** <mark style="color:purple;">`any`</mark>

```lua
local example = menu.create("Example", "Example", "Example")
local button_select = example:button_select("Button Select", "", {"Option1", "Option2"})
print(button_select:get())
```

获取值。

#### :set

**`item:set(value: any)`**

```lua
local example = menu.create("Example", "Example", "Example")
local button_select = example:button_select("Button Select", "", {"Option1", "Option2"})
button_select:set("Option2")
```

设定值。

#### :type

**`item:type():`** <mark style="color:purple;">`string`</mark>

```lua
local example = menu.create("Example", "Example", "Example")
local button_select = example:button_select("Button Select", "", {"Option1", "Option2"})
print(button_select:type())
```

获取项目类型。

#### :rows

**`item:rows([r: number]):`** <mark style="color:purple;">`number`</mark>

```lua
local example = menu.create("Example", "Example", "Example")
local area = example:text_area("Area", "")
area:rows(16)
print(area:rows())
```

获取或设定item最大高度倍数（仅table、text\_area、list有效），默认值为8，即8个标准item高度（不含间隔高度）。

#### :name

**`item:name([values: string]):`** <mark style="color:purple;">`string`</mark>

```lua
local example = menu.create("Example", "Example", "Example")
local button_select = example:button_select("Button Select", "", {"Option1", "Option2"})
button_select:name("Select???")
print(button_select:name())
```

获取或设定名称。

#### :create

**`item:create():`** [<mark style="color:purple;">`MenuGroupo`</mark>](menu.md#menugroup)

```lua
local example = menu.create("Example", "Example", "Example")
local button_select = example:button_select("Button Select", "", {"Option1", "Option2"})
local sub_group = button_select:create()
local option3 = sub_group:switch("Option3")
```

在item上创建子组。

#### :visible

**`item:visible([value: boolean]):`** <mark style="color:purple;">`boolean`</mark>

```lua
local example = menu.create("Example", "Example", "Example")
local button_select = example:button_select("Button Select", "", {"Option1", "Option2"})
button_select:visible(false)
print(button_select:visible())
```

获取或设定可视状态可视状态。

#### :tooltip

**`item:tooltip([value: string]):`** <mark style="color:purple;">`string`</mark>

```lua
local example = menu.create("Example", "Example", "Example")
local button_select = example:button_select("Button Select", "", {"Option1", "Option2"})
button_select:tooltip("此选择器为单选")
print(button_select:tooltip())
```

获取或设定提示。

#### :set\_callback

**`item:set_callback(callback: function)`**

```lua
local example = menu.create("Example", "Example", "Example")
local button_select = example:button_select("Button Select", "", {"Option1", "Option2"})
button_select:set_callback(function(this)
    print(this:get())
end)
```

注册回调函数。回调函数在元素被点击/修改值时触发。

#### :unset\_callback

**`item:unset_callback(callback: function)`**

```lua
local example = menu.create("Example", "Example", "Example")
local button_select = example:button_select("Button Select", "", {"Option1", "Option2"})
local foo = function(this)
    this:unset_callback(foo)
end
button_select:set_callback(foo)
```

注销回调函数。所有回调函数将在脚本被卸载时自动注销。

#### set\_context\_menu

**`menu.set_context_menu(name: string, callback: function)`**

| 参数       | 类型       | 描述 |
| -------- | -------- | -- |
| name     | string   |    |
| callback | function |    |

<pre class="language-lua"><code class="lang-lua">local example = menu.create("Example", "Example", "Example")
local button_select = example:button_select("Button Select", "", {"Option1", "Option2"})
<strong>
</strong><strong>button_select:set_context_menu("todo sth", function(value)
</strong>    print(value)
end)
</code></pre>
注册右键菜单。

### 🔗 `BuiltInContextMenu`&#x20;

| 值                   | 描述                 |
| ------------------- | ------------------ |
| list                |                    |
| input               | input\|input\_area |
| table               |                    |
| button              |                    |
| slider              |                    |
| select              |                    |
| switch              |                    |
| button\_select      |                    |
| fofa\_result\_table | 资产测绘->Fofa->结果列表   |
