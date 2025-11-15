---
description: yaml序列化和反序列化
---

# 📃 yaml

## Functions:

### parse

**`yaml.parse(yaml_text: string):` **<mark style="color:purple;">`table`</mark>

| 参数         | 类型     | 描述      |
| ---------- | ------ | ------- |
| yaml\_text | string | yaml字符串 |

```lua
local raw = [[
name: "Example"
age: 30
is_student: false
courses:
  - name: "Web Development"
    level: "Beginner"
address:
  city: "Shenzhen"
  country: "China"
]]
local yml_metamethod = raw:yaml()    -- 通过string:yaml()元方法调用
local yml = yaml.parse(raw)
for k, v in pairs(yml) do
	print(k, v)
end
```

反序列化yaml格式数据。

### stringify

**`yaml.stringify(data: table):` **<mark style="color:purple;">`string`</mark>

| 参数   | 类型    | 描述 |
| ---- | ----- | -- |
| data | table |    |

```lua
local tbl = {
	name = "Example",
	age = 30,
	is_student = false,
	courses = {
		name = "Web Development",
		level = "Beginner"
	},
	address = {
		city = "Shenzhen",
		country = "China"
	}
}
print(yaml.stringify(tbl))
```

将table以yaml格式序列化。
