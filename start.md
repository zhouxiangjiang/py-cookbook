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
assert i[:] == [1, 2, 3, 4, 5, 6]  ## 复制列表
i.append(7)
del i[6]
i.sort() ##对列表进行原址排序

##列表当作队列使用

# 元组
i = (1, 2, 3, 4, 5, 6)
assert len(i) == 6
assert i[0] == 1
assert i[-1] == 6
assert i[1:3] == (2, 3)
assert i[1:] == (2, 3, 4, 5, 6)
assert i[:3] == (1, 2, 3)
assert i[::2] == (2,)

len(i)
t = 12345, 54321, 'hello!'
x, y, z = t

#集合
basket = {'apple', 'orange', 'apple', 'pear', 'orange', 'banana'}
print(basket)  ##打印{'orange', 'banana', 'pear', 'apple'}
'orange' in basket   ##打印True

a = set('abracadabra') 
b = set('alacazam')
a   ##打印{'a', 'r', 'b', 'c', 'd'}
a - b   # letters in a but not in b
a | b   # letters in either a or b
a & b   # letters in both a and b
a ^ b   # letters in a or b but not both

a = {x for x in 'abracadabra' if x not in 'abc'}
a  ##打印 {'r', 'd'}


# 字典
i = {'a': 1, 'b': 2}
assert len(i) == 2
assert i['a'] = 1
```

## 控制流

```python
if True:
    print('True')
elif False:
    print('False')
else:
    print('False')

i = 0
while i<10:
    print(i)
    i += 1

for i in range(3):
    print(i)
```

## 函数

```python

#定义函数

def f():
    return 0
```
#函数的默认参数值

def ask_ok(prompt, retries=4, complaint='Yes or no, please!'):
    while True:
        ok = input(prompt)
        if ok in ('y', 'ye', 'yes'):
            return True
        if ok in ('n', 'no', 'nop', 'nope'):
            return False
        retries = retries - 1
        if retries < 0:
            raise OSError('uncooperative user')
        print(complaint)
		
PS：函数的默认值只计算一次。
def f(a, L=[]):
    L.append(a)
    return L

print(f(1))
print(f(2))
print(f(3))
这将会打印
[1]
[1, 2]
[1, 2, 3]
	
#lambda 表达式
def make_incrementor(n):
    return lambda x: x + n
	
f = make_incrementor(42)
f(0) ##打印42



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
