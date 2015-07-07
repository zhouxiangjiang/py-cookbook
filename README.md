# Python菜谱
支持Python v3.4.3+.

## The Zen of Python （Python之禅）

在Python Shell里输入 `import this` 或者参考[PEP 20](http://legacy.python.org/dev/peps/pep-0020/)

> Beautiful is better than ugly. 优美胜于丑陋（Python 以编写优美的代码为目标）
>
> Explicit is better than implicit. 明了胜于晦涩（优美的代码应当是明了的，命名规范，风格相似）
>
> Simple is better than complex. 简洁胜于复杂（优美的代码应当是简洁的，不要有复杂的内部实现）
>
> Complex is better than complicated. 复杂胜于凌乱（如果复杂不可避免，那代码间也不能有难懂的关系，要保持接口简洁）
>
> Flat is better than nested. 扁平胜于嵌套（优美的代码应当是扁平的，不能有太多的嵌套）
>
> Sparse is better than dense. 间隔胜于紧凑（优美的代码有适当的间隔，不要奢望一行代码解决问题）
>
> Readability counts. 优美源于代码可读
>
> Special cases aren't special enough to break the rules. 没有特例足以违背这些规则（这些规则至高无上），
>
> Although practicality beats purity. 即便特例确实存在
>
> Errors should never pass silently. 不要包容所有错误，
>
> Unless explicitly silenced. 除非你确定需要这样做（精准地捕获异常，不写 except:pass 风格的代码）
>
> In the face of ambiguity, refuse the temptation to guess. 当存在多种可能，不要尝试去猜测
>
> There should be one-- and preferably only one --obvious way to do it. 而是尽量找一种，最好是唯一一种明显的解决方案（如果不确定，就用穷举法）
>
> Although that way may not be obvious at first unless you're Dutch. 虽然这并不容易，因为你不是 Python 之父（这里的 Dutch 是指 Guido）
>
> Now is better than never. 现在胜与永远不做，
>
> Although never is often better than *right* now. 即便这样可能不一定好
>
> If the implementation is hard to explain, it's a bad idea. 如果实现方案很难解释，则一定不是好方案
>
> If the implementation is easy to explain, it may be a good idea. 反之亦然（方案测评标准）
>
> Namespaces are one honking great idea -- let's do more of those! 命名空间是一种绝妙的理念，我们应当多加利用（倡导与号召）

## Python Coding Style （Python编码规范）

参考 [PEP 8](https://www.python.org/dev/peps/pep-0008/)

- 使用4个空格缩进，避免使用`Tab`.（如果使用`Tab`，则使用4个空格替换`Tab`的方式）

- 括号中使用悬挂缩进，2个缩进

```python
a = long_function_name(
        var_one, var_two,
        var_three, var_four)
```

- `if`语句跨行使用悬挂缩进，2个缩进

```python
if this_is_one_condition
        and this_is_another_condition:
    do_something()
```

- 限制最大行宽为100字符，文档字符串或注释为79

> Python 标准库比较保守，限制行宽为79字符

- 两行空行分割顶层函数和类的定义

- 单个空行分割类的方法定义

- 额外的空行可以分割逻辑块，但尽量节约使用

- 所有文本文件（包括代码）一律使用**UTF-8**编码

- 尽可能将注释放在单独一行

- 更新代码前，优先更新注释

- 使用docstring注释模块、类、方法、函数

- 在操作符两边、逗号后使用空格。例如：`a = f(a, b)`

- 类的命名方式为`CamelCase`，方法及函数为`lower_case_with_underscores`

- 避免使用下划线开始的方式命名变量、函数或类

> 一般而言，使用`_xxx`开始的变量名为“私有的”变量或者方法。

> 以`__xxx__`命名的方法或变量，是Python内部变量。

- 避免重复计算，使用变量保存计算结果

- 避免"Magic"数字。例如：`a[0]`或者`if a == 1`

- 模块导入`import`始终在文件顶部，在模块注释和文档字符串之后，在模块全局变量和常量之前

- 模块导入在单独一行

```python
import sys
import os

# 不是
import sys, os
```

> 模块导入顺序:
>
>      - 标准库模块
>      - 第三方模块
>      - 自定义模块
>
> 每个模块类型都以一个空行分隔

- 禁止使用通配符导入 ( `from module import *` ).

- 编程建议

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

# 尽量使用`.join()`方法连接字符串
c = ''.join(['a','b'])
c = 'a' + 'b'          # JPython版本中运行效率很低!!!

# 自定义异常类继承自`Exception`，而不是`BaseException`
# 异常设计参考[PEP 3151](https://www.python.org/dev/peps/pep-3151/)

# 比较对象类型
if isinstance(obj, int)
if type(obj) is type(int)  # Bad!!!
```
