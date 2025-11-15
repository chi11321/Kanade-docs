# 🔑 crypto

## Functions:

### md5

**`crypto.md5(ctx: string):`**<mark style="color:purple;">`string`</mark>

对字符串进行md5 hash散列计算。

### sha1

**`crypto.sha1(ctx: string):`**<mark style="color:purple;">`string`</mark>

### sha224

**`crypto.sha224(ctx: string):`**<mark style="color:purple;">`string`</mark>

### sha256

**`crypto.sha256(ctx: string):`**<mark style="color:purple;">`string`</mark>

### sha384

**`crypto.sha384(ctx: string):`**<mark style="color:purple;">`string`</mark>

### sha512

**`crypto.sha512(ctx: string):`**<mark style="color:purple;">`string`</mark>

### en\_base32

**`crypto.en_base32(ctx: string):`**<mark style="color:purple;">`string`</mark>

**参数:**

| 名称  | 类型     | 描述 |
| --- | ------ | -- |
| ctx | string |    |

```lua
print(crypto.de_base32(crypto.en_base32("123456")))
```

编码base32数据。

### de\_base32

**`crypto.de_base32(ctx: string):`**<mark style="color:purple;">`string`</mark>

**参数:**

| 名称  | 类型     | 描述 |
| --- | ------ | -- |
| ctx | string |    |

解码base32数据。

### en\_base64

**`crypto.en_base64(ctx: string):`**<mark style="color:purple;">`string`</mark>

编码base64数据。

### de\_base64

**`crypto.de_base64(ctx: string):`**<mark style="color:purple;">`string`</mark>

解码base64数据。
