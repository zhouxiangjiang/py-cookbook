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

from __future__ import unicode_literals
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
record = ('Dave', 'dave@example.com', '773-555-1212', '847-555-1212')
_, email, *phone_numbers = record
assert email == 'dave@example.com'
```

## 数据结构

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
assert i[:] == [1, 2, 3, 4, 5, 6]  # 复制列表
i.append(7)
del i[6]
i.sort()  # 进行原址排序


# 元组
i = (1, 2, 3, 4, 5, 6)
assert len(i) == 6
assert i[0] == 1
assert i[-1] == 6
assert i[1:3] == (2, 3)
assert i[1:] == (2, 3, 4, 5, 6)
assert i[:3] == (1, 2, 3)
assert i[::2] == (2,)
assert len(i) == 6
t = 12345, 54321, 'hello!'
x, y, z = t

# 集合
basket = {'apple', 'orange', 'apple', 'pear', 'orange', 'banana'}
assert basket = {'orange', 'banana', 'pear', 'apple'}
assert 'orange' in basket = True

a = set('abracadabra') 
b = set('alacazam')
assert a == {'a', 'r', 'b', 'c', 'd'}
a - b   # letters in a but not in b
a | b   # letters in either a or b
a & b   # letters in both a and b
a ^ b   # letters in a or b but not both

a = {x for x in 'abracadabra' if x not in 'abc'}
assert a == {'r', 'd'}


# 字典
i = {'a': 1, 'b': 2}
assert len(i) == 2
assert i['a'] == 1
```

## 控制流

```python
if a == 1:
    print('a == 1')
elif a == 2:
    print('a == 2')
else:
    print('a != 1 and a != 2')

i = 0
while i<10:
    print(i)
    i += 1

for i in range(3):
    print(i)
```

## 条件判断

```python
# None 判断
if a is None
if a is not None
if not a is None  # Bad!!!

# 布尔值判断
if a
if a == True      # Bad!!!
if a is True      # Worse!!!

# 空序列（字符串、列表、元组）判断
# 空序列为false
if seq
if len(seq)        # Bad!!!
if len(seq) != 0   # Worse!!!
if not len(seq)    # Worse!!!
```

## 循环遍历

```python
# 遍历且更新可变序列（列表）
assert isinstance(words, list)
for word in words[:]:
    if len(word) > 6:
        words.insert(0, word)

# 遍历字典
assert isinstance(mydict, dict)
for key, value in mydict.items(): # Python 2: mydict.iteritems()
    pass
```

## 定义函数

```python
'''Function Annotations (Python 3 Only)

    The Python interpreter does not attach any semantic meaning to the attached
    annotations. They are not type checks, nor do they make Python behave any
    differently than it did before. However, they might give useful hints to
    others reading the source code about what you had in mind. Third-party
    tools and frameworks might also attach semantic meaning to the annotations.

    Although you can attach any kind of object to a function as an annotation
    (e.g., numbers, strings, instances, etc.), classes or strings often seem to
    make the most sense.

    Function annotations are merely stored in a function’s `__annotations__`
    attribute.

    For example:

        def f(x:int, y:int) -> int:
            return x + y
'''

def f():
    return 0
```

##函数的默认参数值

```python
# 函数的默认值只计算一次。
def f(a, L=[]):
    L.append(a)
    return L

assert f(1) == [1]
assert f(2) == [1 , 2]
assert f(3) == [1, 2, 3]
	
# lambda 表达式
def make_incrementor(n):
    return lambda x: x + n
	
f = make_incrementor(42)
assert f(0) == 42
assert f(1) == 43

```

## 面向对象 (OOP)

```python
class A(object):
    '''A class.

    # Built-in Class Attributes:
    - __name__   : string name of class
    - __doc__    : documentation string
    - __bases__  : tuple of class's base classes
    - __slots__  : list of attribute names (reduce memory)

    # Built-in Instance Attributes:
    - __doc__    : documentation string
    - __class__  : class for instance
    - __module__ : module where class is defined

    # Built-in Methods:
    - __init__() : constructor
    - __str__()  : string representation, str(obj)
    - __len__()  : length, len(obj)
    '''

    # Python does not provide any internal mechanism track how many instances
    # of a class have been created or to keep tabs on what they are. The best
    # way is to keep track of the number of instances using a class attribute.
    num_of_instances = 0

    def __init__(self, a1=None, a2=None):
        A.num_of_instances += 1
        self.public_instance_attribute = a1
        self.private_instance_attribute = a2

    def public_instance_method(self):
        return (A.num_of_instances,
                self.publuc_instance_attribute,
                self.private_instance_attribute)

    def _private_instance_method(self):
        pass

    @staticmethod
    def static_method():
        return A.num_of_instances

    @classmethod
    def class_method(cls):
        return cls.__name__


class B(A):
    '''Subclass of A.
    '''

    def __init__(self, b, a1=None, a2=None):
        super(B, self).__init__(a1, a2)
        self.b = b

    def public_instance_method(self):
        print('Override method of {0}'.format(self.__class__.__bases__[0]))

    def new_method(self):
        print('New method without inheritance from {0}'
                .format(self.__class__.__bases__[0]))


assert isinstance(A(), A)
assert issubclass(B, A)
```
