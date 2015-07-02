# 入门
Python 3.4.3+

参考 [Python 3 官方文档](https://docs.python.org/3/) ([中文翻译版](http://python.usyiyi.cn/python_343/tutorial/))

## 代码编辑器

- Notepad++ (Windows)

编码方式: 无BOM`UTF-8`.

## Hello World

```python
#!/usr/bin/env python

print('Hello World')
```

Python 2.7:

```python
#!/usr/bin/env python

from __future__ import print_function

print('Hello World')
```

## 定义变量

```python
i = 1           # 整数 int
i = 0xff        # 十六进制整数 int
i = 's'         # 字符串 str (utf-8编码)
i = "a, 's'"    # 带单引号的字符串 str (utf-8编码)
i = 'a, "s"'    # 带双引号的字符串 str (utf-8编码)
i = 1.0         # 浮点数 float
i = 1.23e9      # 科学计数法浮点数 float
i = b'abc'      # 二进制 bytes
i = True        # 布尔值 真
i = False       # 布尔值 假
```

## 定义数据结构

```python
# 列表
i = [1, 2, 3, 4, 5, 6]
assert len(i) == 6
assert i[0] == 1
assert i[-1] == 6
assert i[1:3] == [2, 3]
assert i[1:] == [2, 3, 4, 5, 6]
assert i[:3] == [1, 2, 3]
assert i[::2] == [2]
assert i[:] == [1, 2, 3, 4, 5, 6]  ## 复制列表
i.append(7)
del i[6]

# 元组
i = (1, 2, 3, 4, 5, 6)
assert len(i) == 6
assert i[0] == 1
assert i[-1] == 6
assert i[1:3] == (2, 3)
assert i[1:] == (2, 3, 4, 5, 6)
assert i[:3] == (1, 2, 3)
assert i[::2] == (2,)

# 字典
i = {'a': 1, 'b': 2}
assert len(i) == 2
assert i['a'] = 1
```

## 控制流

```python
if True:
    print('True')
else:
    print('False')

i = 0
while i<10:
    print(i)
    i += 1

for i in range(3):
    print(i)
```

## 定义函数

```python
def f():
    return 0
```
