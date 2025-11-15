# 通过FFI调用C语言

```lua
ffi.cdef[[
	typedef struct {float x, y, z;} Vector_t;
	typedef int (*CFunctionPtr)(int, int);

	int printf(const char *fmt, ...);
]]
local vec = ffi.new("Vector_t")
print(vec)
vec.x = 1
vec.y = 2
vec.z = 3

local add = function(a, b)
	return a + b
end

local c_function_ptr = ffi.cast("CFunctionPtr", add)
ffi.C.printf("Hello %s!\\n", "luajit")	-- printf将内容打印到stdout，因此在日志中是不可见的
print(c_function_ptr(1, 2))
```
