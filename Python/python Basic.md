# <center>python 基础</center>

## <font class="text-color-13" color="#ffeb3b">数据类型</font>

1. <font class="text-color-7" color="#03a9f4">数字类型</font>（Numeric Types）：
  
	  - 整数（int）：表示整数值，例如：-5、0、10等。
	  - 浮点数（float）：表示浮点数值，即带有小数部分的数值，例如：3.14、-2.5等。
	  - 复数（complex）：表示复数，例如：3 + 2j。
2. <font class="text-color-61" color="#03a9f4">字符串</font>（String）：
  
  	- 字符串（str）：表示一串字符，可以是单引号（'）或双引号（"）括起来的任意文本，例如：`"Hello, World!"` 。
3. <font class="text-color-61" color="#03a9f4">布尔类型</font>（Boolean Type）：
  
  	- 布尔值（bool）：表示逻辑值，只有两个取值：`True` 和 `False` 。
4. <font class="text-color-61" color="#03a9f4">列表</font>（List）：
  
  	- 列表（list）：表示一个有序的、可变的元素集合，用方括号 `[ ]` 括起来，元素之间用逗号分隔，例如：`[1, 2, 3]`。
5. <font class="text-color-61" color="#03a9f4">元组</font>（Tuple）：
  
  	- 元组（tuple）：表示一个有序的、不可变的元素集合，用圆括号 `( )` 括起来，元素之间用逗号分隔，例如：`(1, 2, 3)` 。
6. <font class="text-color-61" color="#03a9f4">字典</font>（Dictionary）：
  
  	- 字典（dict）：表示键值对的无序集合，用花括号 `{ }` 括起来，每个键值对之间用冒号 `:` 分隔，键值对之间用逗号分隔，例如：`{"name": "Alice", "age": 25}` 。
7. <font class="text-color-61" color="#03a9f4">集合</font>（Set）：
  
  	- 集合（set）：表示无序、唯一元素的集合，用花括号 `{ }` 括起来，元素之间用逗号分隔，例如：`{1, 2, 3}` 。
8. <font class="text-color-61" color="#03a9f4">字节串</font>（Bytes）：
  
  	- 字节串（bytes）：表示字节的不可变序列，用前缀 `b` 或 `B` 表示，例如：`b"Hello"` 。
9. <font class="text-color-61" color="#03a9f4">字节数组</font>（Bytearray）：
  
  	- 字节数组（bytearray）：表示字节的可变序列，用前缀 `bytearray` 表示，例如：`bytearray(b"Hello")`。
10. <font class="text-color-61" color="#03a9f4">空值</font>（None）：
  
  	- 空值（NoneType）：表示空值或缺失值，用关键字 `None` 表示。
---
### <font class="text-color-15" color="#ff9800">数字（Number）</font>

| 数据类型   | 描述                                                                                                   |
|------------|--------------------------------------------------------------------------------------------------------|
| 整数（int） | 表示整数值，例如：-5、0、10等。                                                                           |
| 浮点数（float） | 表示带有小数的数值，例如：3.14、2.718等。                                                                 |
| 复数（complex） | 表示具有实部和虚部的数值，例如：1+2j、-3+4j等。                                                            |
| 布尔值（bool）   | 表示逻辑值，只有两个取值，True和False，用于表示真和假。                                                   |
| 长整数（long）   | 用于表示比普通整数范围更大的整数，一般在Python 2.x版本中使用，Python 3.x中整数类型已经统一为int，可以表示任意大小的整数。 |

- 示例
```python
# 整数
x = 5
y = -10

# 浮点数
pi = 3.14159
e = 2.718

# 复数
z = 1 + 2j
w = -3 + 4j

# 布尔值
is_true = True
is_false = False

# 长整数（在Python 3.x中，普通整数可以表示任意大小的整数，无需使用long类型）
big_number = 1234567890123456789012345678901234567890
```
### <font class="text-color-15" color="#ff9800">空值 None</font>
1. 表示缺失值或空值： `None` 用作一个特殊的对象，表示缺少值或空值的情况。它可以用于标识变量尚未赋值或函数没有明确的返回值。
```python
my_variable = None
result = do_something()
if result is None:
    print("No result available")
```
2. 函数参数的默认值：
	在函数定义中，可以使用 `None` 作为参数的默认值，以便在调用函数时，参数可以选择性地传递或使用默认值。
```python
def process_data(data, option=None):
    # 处理数据的代码
    # 如果未指定选项参数，则使用默认逻辑

process_data(my_data)           # 不指定选项参数，使用默认逻辑
process_data(my_data, "option")  # 指定选项参数为 "option"
```
3. 标识空容器或缺失数据： `None` 可以用作容器（如列表、字典等）的初始值，以表示容器为空或数据缺失的情况。
```python
my_list = None
my_dict = None
```
4. 指示函数结束：
	在特定情况下，可以使用 `return None` 语句来显式指示函数的结束，并将结果设置为 `None`。
```python
def process_data(data):
    # 处理数据的代码
    if len(data) == 0:
        return None
    # 继续处理数据的代码
```


### <font class="text-color-15" color="#ff9800">数据类型转换</font>
| 转换类型       | 描述                             |
|--------------|----------------------------------|
| int(x)       | 将x转换为整数类型。                 |
| float(x)     | 将x转换为浮点数类型。               |
| str(x)       | 将x转换为字符串类型。               |
| bool(x)      | 将x转换为布尔类型。                 |
| list(x)      | 将x转换为列表类型。                 |
| tuple(x)     | 将x转换为元组类型。                 |
| dict(x)      | 将x转换为字典类型。                 |
| set(x)       | 将x转换为集合类型。                 |

```python
# 整数转换
num_int = int(10.5)
print(num_int)  # 输出: 10

# 浮点数转换
num_float = float("3.14")
print(num_float)  # 输出: 3.14

# 字符串转换
num_str = str(100)
print(num_str)  # 输出: "100"

# 布尔类型转换
bool_val = bool(0)
print(bool_val)  # 输出: False

# 列表转换
list_val = list("Hello")
print(list_val)  # 输出: ['H', 'e', 'l', 'l', 'o']

# 元组转换
tuple_val = tuple([1, 2, 3])
print(tuple_val)  # 输出: (1, 2, 3)

# 字典转换
dict_val = dict([(1, "one"), (2, "two")])
print(dict_val)  # 输出: {1: 'one', 2: 'two'}

# 集合转换
set_val = set([1, 2, 2, 3, 3, 3])
print(set_val)  # 输出: {1, 2, 3}
```

## <font class="text-color-13" color="#ffeb3b">变量</font>
- 在Python中，变量是用于存储数据的标识符。它们用于给数据赋予名称，以便在程序中引用和操作这些数据。在Python中，变量是动态类型的，这意味着你可以在运行时为变量分配不同类型的值。

- 要定义一个变量，你需要遵循以下规则：
	1. 变量名必须以字母或下划线开头，后面可以跟字母、数字或下划线。变量名区分大小写，例如`my_variable`和`My_Variable`是不同的变量。
	2. 变量名不能是Python的关键字（如`if`、`for`、`while`等）或内置函数名（如`print`、`len`、`range`等）。
	3. 选择一个描述性的变量名，以便于代码的可读性和理解。

- 示例：
```python
# 定义整数变量
age = 25

# 定义浮点数变量
temperature = 98.6

# 定义字符串变量
name = "John Doe"

# 定义布尔变量
is_valid = True

# 定义列表变量
numbers = [1, 2, 3, 4, 5]

# 定义字典变量
person = {"name": "John", "age": 25}

# 定义空变量
my_variable = None
```
- 在上面的示例中，我们使用等号 `=` 将值分配给变量。Python会根据所赋的值自动推断变量的类型。你可以根据需要随时更改变量的值和类型。例如：
```python
x = 10  # 整数类型
x = 3.14  # 浮点数类型
x = "Hello"  # 字符串类型

# 通过将新值赋给变量，我们可以更新变量的内容。
```
### <font class="text-color-15" color="#ff9800">作用域</font>
1. 全局变量（Global Variables）：
	全局变量是在全局作用域中定义的变量，可以在程序的任何地方被访问。它们在整个程序的执行过程中都是可见的。
```python
global_var = 10  # 全局变量

def my_function():
    print(global_var)  # 在函数中访问全局变量

my_function()  # 输出: 10
```
2. 局部变量（Local Variables）：
	局部变量是在函数或代码块内部定义的变量，其作用域仅限于所在的函数或代码块。局部变量在其所在的作用域内可见，外部作用域无法直接访问。
```python
def my_function():
    local_var = 20  # 局部变量
    print(local_var)  # 在函数内部访问局部变量

my_function()  # 输出: 20
print(local_var)  # 报错，无法在函数外部访问局部变量
```
3. 函数参数（Function Parameters）：
	函数参数是在函数定义中声明的变量，用于接收函数调用时传递的值。函数参数的作用域仅限于函数内部。
```python
def my_function(param):
    print(param)  # 在函数内部访问函数参数

my_function(30)  # 输出: 30
print(param)  # 报错，无法在函数外部访问函数参数
```
4. 内置变量（Built-in Variables）：
	内置变量是由Python解释器提供的预定义变量，可以在任何地方直接使用。这些变量具有全局作用域。
```python
print(__name__)  # 输出当前模块的名称
print(len([1, 2, 3]))  # 输出列表的长度
```


## <font class="text-color-13" color="#ffeb3b">语法相关</font>

### <font class="text-color-15" color="#ff9800">注释</font>
- Python中有两种常见的注释方式：单行注释和多行注释。

- 单行注释使用 `#` 符号。在 `#` 后面的任何内容都被认为是注释，并且不会被解释器执行。例如：
```python
# 这是一个单行注释
x = 10  # 这是另一个单行注释
```
- 多行注释使用三个引号(`"""`或`'''`)将注释内容括起来。多行注释通常用于解释函数或类的功能，以及提供模块级的文档字符串（docstring）。例如：
```python
"""
这是一个多行注释的示例。
它可以跨越多行，并且可以包含更多的详细信息。
"""
```
- 除了用于注释代码的功能，多行注释还可以用作文档字符串（docstring），它们可以在函数或类的定义之后进行访问。可以使用`help()`函数来查看文档字符串。例如：
```python
def my_function():
    """
    这是一个函数的文档字符串。
    它提供了有关函数功能和用法的详细信息。
    """
    # 函数的代码

help(my_function)  # 显示函数的文档字符串
```
## <font class="text-color-13" color="#ffeb3b">运算符</font>
1. 算术运算符（Arithmetic Operators）：
  
	  - 加法（+）：将两个值相加。
	  - 减法（-）：从第一个值中减去第二个值。
	  - 乘法（*）：将两个值相乘。
	  - 除法（/）：将第一个值除以第二个值。
	  - 取模（%）：返回除法的余数。
	  - 整除（//）：返回除法的商的整数部分。
	  - 幂运算（**）：将第一个值的幂指数为第二个值。
```python
# 加法
result = 5 + 3
print(result)  # 输出: 8

# 减法
result = 10 - 2
print(result)  # 输出: 8

# 乘法
result = 4 * 3
print(result)  # 输出: 12

# 除法
result = 15 / 5
print(result)  # 输出: 3.0

# 取模
result = 17 % 4
print(result)  # 输出: 1

# 整除
result = 17 // 4
print(result)  # 输出: 4

# 幂运算
result = 2 ** 3
print(result)  # 输出: 8
```

2. 比较运算符（Comparison Operators）：
  
	  - 相等（==）：检查两个值是否相等。
	  - 不相等（!=）：检查两个值是否不相等。
	  - 大于（>）：检查第一个值是否大于第二个值。
	  - 小于（<）：检查第一个值是否小于第二个值。
	  - 大于等于（>=）：检查第一个值是否大于或等于第二个值。
	  - 小于等于（<=）：检查第一个值是否小于或等于第二个值。
3. 赋值运算符（Assignment Operators）：
  
	  - 赋值（=）：将右侧的值赋给左侧的变量。
	  - 加法赋值（+=）：将右侧的值与左侧的变量相加，并将结果赋给左侧的变量。
	  - 减法赋值（-=）：从左侧的变量中减去右侧的值，并将结果赋给左侧的变量。
	  - 乘法赋值（*=）：将左侧的变量乘以右侧的值，并将结果赋给左侧的变量。
	  - 除法赋值（/=）：将左侧的变量除以右侧的值，并将结果赋给左侧的变量。
	  - 取模赋值（%=）：将左侧的变量取模右侧的值，并将结果赋给左侧的变量。
	  - 整除赋值（//=）：将左侧的变量整除以右侧的值，并将结果赋给左侧的变量。
	  - 幂赋值（**=）：将左侧的变量的值提升到右侧的值所指定的幂，并将结果赋给左侧的变量。
4. 逻辑运算符（Logical Operators）：
  
	  - 与（and）：如果两个条件都为True，则结果为True。
	  - 或（or）：如果两个条件中至少有一个为True，则结果为True。
	  - 非（not）：对条件的结果进行取反。
```python
x = True
y = False

# 与
result = x and y
print(result)  # 输出: False

# 或
result = x or y
print(result)  # 输出: True

# 非
result = not x
print(result)  # 输出: False
```
5. 位运算符（Bitwise Operators）：
  
	  - 按位与（&）：对两个数的每一位进行与运算。
	  - 按位或（|）：对两个数的每一位进行或运算。
	  - 按位异或（^）：对两个数的每一位进行异或运算。
	  - 按位取反（~）：对数的每一位进行取反运算。
	  - 左移（<<）：将数的二进制表示向左移动指定的位数。
	  - 右移（>>）：将数的二进制表示向右移动指定的位数。
```python
x = 5  # 二进制表示为 0b101
y = 3  # 二进制表示为 0b011

# 按位与
result = x & y
print(result)  # 输出: 1 (二进制表示为 0b001)

# 按位或
result = x | y
print(result)  # 输出: 7 (二进制表示为 0b111)

# 按位异或
result = x ^ y
print(result)  # 输出: 6 (二进制表示为 0b110)

# 按位取反
result = ~x
print(result)  # 输出: -6 (二进制表示为 -0b110)

# 左移
result = x << 2
print(result)  # 输出: 20 (二进制表示为 0b10100)

# 右移
result = x >> 1
print(result)  # 输出: 2 (二进制表示为 0b10)

```
6. 成员运算符（Membership Operators）：
  
	  - 存在于（in）：如果指定的值存在于序列中，则结果为True。
	  - 不存在于（not in）：如果指定的值不存在于序列中，则结果为True。
```python
my_list = [1, 2, 3, 4, 5]

# 存在于
result = 3 in my_list
print(result)  # 输出: True

# 不存在于
result = 6 not in my_list
print(result)  # 输出: True
```

7. 身份运算符（Identity Operators）：
  
	  - 相同（is）：如果两个对象引用同一个对象，则结果为True。
	  - 不同（is not）：如果两个对象引用不同的对象，则结果为True。
```python
x = 5
y = 5

# 相同
result = x is y
print(result)  # 输出: True

# 不同
result = x is not y
print(result)  # 输出: False

x = [1, 2, 3]
y = x
print(x is y)  # 输出: True

z = [1, 2, 3]
print(x is z)  # 输出: False
```
8. 运算符优先级（Operator Precedence）：

  	- 运算符具有不同的优先级，可以使用括号来改变运算的顺序。

## <font class="text-color-13" color="#ffeb3b">常用函数</font>

### <font class="text-color-15" color="#ff9800">print 函数</font>
- `print()` 函数是Python中用于输出（打印）信息到标准输出设备（通常是控制台）的内置函数。它可以用于显示文本、变量的值、表达式的结果等。

- `print()` 函数的基本语法如下：
```python
print(value1, value2, ..., sep=' ', end='\n', file=sys.stdout, flush=False)
```
- 参数说明：

	- `value1, value2, ...`：要打印的值，可以是一个或多个参数。它们将按照给定的顺序打印在一行上。
	- `sep=' '`：用于分隔多个值之间的分隔符。默认情况下，它是一个空格字符。
	- `end='\n'`：打印完所有值后在末尾添加的字符。默认情况下，它是换行符`\n`，即每个`print()`调用会在输出后换行。
	- `file=sys.stdout`：指定要打印到的文件对象。默认情况下，它将打印到标准输出设备（控制台）。
	- `flush=False`：刷新输出缓冲区的设置。默认情况下，缓冲区在换行时自动刷新。

- 以下是一些示例，演示了`print()`函数的用法：
```python
# 打印字符串
print("Hello, World!")

# 打印变量的值
name = "Alice"
age = 25
print("Name:", name, "Age:", age)

# 使用不同的分隔符
print(1, 2, 3, sep="-")  # 输出：1-2-3

# 更改末尾字符
print("Hello", end="!")
print("World")  # 输出：Hello!World

# 打印到文件
with open("output.txt", "w") as f:
    print("This is written to a file.", file=f)
```
---
### <font class="text-color-15" color="#ff9800">type 函数</font>
- `type()`函数是Python中的一个内置函数，用于获取给定对象的类型。它返回表示对象类型的类型对象。

- `type()`函数的基本语法如下：
```python
type(object)
```
- 参数说明：
	- `object`：要检查类型的对象，可以是变量、表达式、数据结构、函数等。

- 以下是一些示例，演示了`type()`函数的用法：
```python
x = 10
print(type(x))  # 输出：<class 'int'>，表示x的类型是整数

y = 3.14
print(type(y))  # 输出：<class 'float'>，表示y的类型是浮点数

name = "Alice"
print(type(name))  # 输出：<class 'str'>，表示name的类型是字符串

numbers = [1, 2, 3, 4, 5]
print(type(numbers))  # 输出：<class 'list'>，表示numbers的类型是列表

def my_function():
    pass

print(type(my_function))  # 输出：<class 'function'>，表示my_function的类型是函数
```
- `type()`函数返回的结果是一个类型对象，可以与其他类型进行比较，用于判断对象的类型。例如，你可以使用`type()`函数的结果与某个类型进行比较，如下所示：
```python
x = 10
if type(x) == int:
    print("x是整数类型")
```

### <font class="text-color-15" color="#ff9800">input 函数</font>
- `input()` 函数是Python中的一个内置函数，用于从用户处获取输入。它允许程序暂停执行，等待用户输入一些数据，并将用户输入的数据作为字符串返回。

- `input()` 函数的基本语法如下：
```python
input(prompt)
```
- 参数说明：

	- `prompt`（可选）：作为提示用户输入的可选字符串。它将显示给用户，以指导用户提供正确的输入。默认情况下，它是空字符串。

- 以下是一些示例，演示了`input()` 函数的用法：
```python
name = input("请输入您的姓名：")
print("您好，" + name + "！")

age = input("请输入您的年龄：")
age = int(age)  # 将输入的字符串转换为整数类型
year_of_birth = 2023 - age
print("您的出生年份是：" + str(year_of_birth))
```
- 需要注意的是，`input()`函数返回的是字符串类型。如果你需要使用输入的值进行数值计算或与其他类型进行比较，你可能需要将其转换为相应的类型（如整数、浮点数）。

### <font class="text-color-15" color="#ff9800">len 函数</font>
- `len()` 函数是一个内置函数，在Python中用于返回对象的长度或元素个数。它适用于多种类型的对象，包括字符串、列表、元组、字典、集合等。

- 示例
```python
text = "Hello, World!"
print(len(text))  # 输出: 13

numbers = [1, 2, 3, 4, 5]
print(len(numbers))  # 输出: 5

point = (3, 4)
print(len(point))  # 输出: 2

person = {"name": "Alice", "age": 25, "city": "New York"}
print(len(person))  # 输出: 3

numbers_set = {1, 2, 3, 4, 5}
print(len(numbers_set))  # 输出: 5
```


## <font class="text-color-13" color="#ffeb3b">字符串(string)</font>

### <font class="text-color-15" color="#ff9800">字符串定义</font>
- 使用单引号或双引号将字符串括起来。
- 示例：
```python
str1 = 'Hello, World!'
str2 = "Python Programming"
```
- 使用三引号或三双引号将字符串括起来，可以跨越多行。
- 示例：
```python
str3 = '''This is a multi-line
string using triple quotes.'''
str4 = """Hello,
Python!"""
```
- 使用转义字符（\）来表示特殊字符，如换行符、制表符等。
- 示例：
```python
str5 = "This is a string with\na new line."
str6 = "This is a string with\ttab."
```
- 原始字符串（Raw String）：
	- 在字符串前加上字母 `r` 或 `R`，创建一个原始字符串，其中转义字符不被处理。
- 示例：
```python
str7 = r"C:\path\to\file.txt"
```
- 字符串连接（String Concatenation）：
	- 使用加号（+）来连接多个字符串。
- 示例：
```python
str9 = "Hello" + " " + "World!"
```
### <font class="text-color-15" color="#ff9800">字符串格式化</font>
1. 使用占位符（Placeholder）：
	在字符串中使用占位符来指示要插入值的位置，并使用`%`运算符和元组（或字典）来提供要插入的值。
	- `%s`：用于插入字符串值。
	- `%d`：用于插入整数值。
	- `%f`：用于插入浮点数值。
- 示例：
```python
name = "Alice"
age = 25
height = 1.65
print("My name is %s, I am %d years old, and my height is %.2f meters." % (name, age, height))
# 输出: My name is Alice, I am 25 years old, and my height is 1.65 meters.
```
2. 使用 `format()` 方法：
	使用大括号（`{}`）作为占位符，通过调用字符串的`format()`方法并传入变量或表达式的值来替换占位符。
- 示例：
```python
name = "Alice"
age = 25
height = 1.65
print("My name is {}, I am {} years old, and my height is {:.2f} meters.".format(name, age, height))
# 输出: My name is Alice, I am 25 years old, and my height is 1.65 meters.
```
3. 使用 f-字符串（f-String）：
	在字符串前加上字母 `f`，然后在字符串中使用花括号（`{}`）来引用变量或表达式的值。
- 示例：
```python
name = "Alice"
age = 25
height = 1.65
print(f"My name is {name}, I am {age} years old, and my height is {height:.2f} meters.")
# 输出: My name is Alice, I am 25 years old, and my height is 1.65 meters.
```
#### <font class="text-color-7" color="#03a9f4">注</font>
* 字符串格式化的括号中可以直接填表达式
* 示例
```python
x = 10
y = 5

# 使用表达式进行字符串格式化
result = "The sum of {} and {} is {}".format(x, y, x + y)
print(result)  # 输出: The sum of 10 and 5 is 15

# 使用表达式进行数值计算
result = "The product of {} and {} is {}".format(x, y, x * y)
print(result)  # 输出: The product of 10 and 5 is 50
```

### <font class="text-color-15" color="#ff9800">格式化精度控制</font>
1. 字段宽度：
	- `width`：可以使用整数值来指定字段的宽度，即所占字符数。
- 示例：
```python
name = "Alice"
print("Name: %10s" % name)
# 输出: Name:      Alice
```
2. 对齐方式：
	- `<`：左对齐（默认对齐方式）。
	- `>`：右对齐。
	- `^`：居中对齐。
- 示例：
```python
name = "Alice"
print("Name: %-10s" % name)  # 左对齐
# 输出: Name: Alice     
print("Name: %10s" % name)   # 右对齐
# 输出: Name:      Alice
print("Name: %^10s" % name)  # 居中对齐
# 输出: Name:   Alice
```
3. 数值格式：
	- `d`：十进制整数。
	- `f`：浮点数。
	- `e`：科学计数法表示的浮点数。
	- `x`：十六进制整数。
- 示例：
```python
value = 12345.6789  
print("Value: %10.2f" % value) # 浮点数，宽度为10，保留2位小数  
# 输出: Value: 12345.68  
print("Value: %.2e" % value) # 科学计数法表示，保留2位小数  
# 输出: Value: 1.23e+04  
int_value = int(value) # 将浮点数转换为整数   
print("Value: %010x" % int_value) # 十六进制表示，宽度为10，前导零填充  
# 输出: Value: 00003039
```

- 除了使用`%`运算符进行格式化外，还可以使用 `format()` 方法或f-字符串来实现格式化。这些方式提供了更多灵活的选项，并可以在占位符中使用类似的格式规范。例如，`{:10s}` 表示字符串字段宽度为10个字符。

### <font class="text-color-15" color="#ff9800">字符串操作</font>
- 可以通过下标索引来获取字符串中特定位置的字符。字符串的下标从0开始，表示第一个字符，依次递增。可以使用方括号 `[]` 并指定相应的下标来访问字符串中的字符。
```python
my_string = "Hello, World!"

# 获取第一个字符
first_char = my_string[0]
print(first_char)  # 输出: 'H'

# 获取最后一个字符
last_char = my_string[-1]
print(last_char)  # 输出: '!'

# 获取特定位置的字符
char = my_string[7]
print(char)  # 输出: 'W'
```
- 需要注意的是，字符串是不可变的，即不能直接通过索引修改字符串中的字符。但是，可以使用字符串的切片操作来创建一个新的字符串。
```python
my_string = "Hello, World!"

# 使用切片获取子字符串
substring = my_string[7:12]
print(substring)  # 输出: 'World'
```
#### <font class="text-color-61" color="#03a9f4">len()</font>
- 返回字符串的长度（字符个数）。
```python
my_string = "Hello, World!"
length = len(my_string)
print(length)  # 输出: 13
```

#### <font class="text-color-61" color="#03a9f4">count(sub, start, end)</font>
- 计算字符串中指定子字符串的出现次数。
    - `sub`：要计数的子字符串。
    - `start`（可选）：计数起始位置的索引，默认为0。
    - `end`（可选）：计数结束位置的索引，默认为字符串末尾。
```python
my_string = "Hello, World!"
count = my_string.count('o')
print(count)  # 输出: 2
```


#### <font class="text-color-61" color="#03a9f4">str()</font>
- 将其他数据类型转换为字符串类型。
```python
number = 10
string_number = str(number)
print(string_number)  # 输出: '10'
```
#### <font class="text-color-61" color="#03a9f4">lower()</font>
- 将字符串转换为小写字母。
```python
my_string = "Hello, World!"
lowercase_string = my_string.lower()
print(lowercase_string)  # 输出: 'hello, world!'
```
#### <font class="text-color-61" color="#03a9f4">upper()</font>
- 将字符串转换为大写字母。
```python
my_string = "Hello, World!"
uppercase_string = my_string.upper()
print(uppercase_string)  # 输出: 'HELLO, WORLD!'
```
#### <font class="text-color-61" color="#03a9f4">capitalize()</font>
- 将字符串的首字母转换为大写，其他字母转换为小写。
```python
my_string = "hello, world!"
capitalized_string = my_string.capitalize()
print(capitalized_string)  # 输出: 'Hello, world!'
```
#### <font class="text-color-61" color="#03a9f4">title()</font>
- 将字符串中每个单词的首字母转换为大写。
```python
my_string = "hello, world!"
titled_string = my_string.title()
print(titled_string)  # 输出: 'Hello, World!'
```
#### <font class="text-color-61" color="#03a9f4">swapcase()</font>
- 将字符串中的大写字母转换为小写，小写字母转换为大写。
```python
my_string = "Hello, World!"
swapped_case_string = my_string.swapcase()
print(swapped_case_string)  # 输出: 'hELLO, wORLD!'
```
#### <font class="text-color-61" color="#03a9f4">strip()</font>
- 去除字符串两端的空格、换行符或指定的字符。
```python
my_string = "   Hello, World!   "
stripped_string = my_string.strip()
print(stripped_string)  # 输出: 'Hello, World!'
```
#### <font class="text-color-61" color="#03a9f4">split()</font>
- 将字符串按照指定的分隔符拆分为子串，返回一个列表。
```python
my_string = "apple,banana,orange"
fruits = my_string.split(',')
print(fruits)  # 输出: ['apple', 'banana', 'orange']
```
#### <font class="text-color-61" color="#03a9f4">join()</font>
- 将一个可迭代对象中的字符串元素连接为一个字符串。
```python
fruits = ['apple', 'banana', 'orange']
joined_string = ','.join(fruits)
print(joined_string)  # 输出: 'apple,banana,orange'
```
#### <font class="text-color-61" color="#03a9f4">index(substring, start, end)</font>
- 返回子字符串第一次出现的索引位置。
    - `substring`：要搜索的子字符串。
    - `start`（可选）：搜索起始位置的索引，默认为0。
    - `end`（可选）：搜索结束位置的索引，默认为字符串末尾。
```python
my_string = "Hello, World!"

# 在索引范围内搜索子字符串
index = my_string.index('o', 5, 10)
print(index)  # 输出: 8
```
#### <font class="text-color-61" color="#03a9f4">replace(old, new, count)</font>
- 将字符串中的指定子字符串替换为新的子字符串。
    - `old`：要被替换的子字符串。
    - `new`：替换后的新子字符串。
    - `count`（可选）：指定替换的次数，默认替换所有匹配项。
```python
my_string = "Hello, World!"
new_string = my_string.replace('o', 'x')
print(new_string)  # 输出: Hellx, Wxrld!
```
#### <font class="text-color-61" color="#03a9f4">切片</font>
```python
my_string = "Hello, World!"

# 切片获取子字符串
sub_string = my_string[7:12]
print(sub_string)  # 输出: "World"

# 使用负数索引进行切片操作
sub_string = my_string[-6:-1]
print(sub_string)  # 输出: "World"

# 使用步长进行切片操作
sub_string = my_string[::2]
print(sub_string)  # 输出: "HloWrd"

# 字符串反转
reversed_string = my_string[::-1]
print(reversed_string)  # 输出: "!dlroW ,olleH"
```


## <font class="text-color-13" color="#ffeb3b">控制语句</font>
### <font class="text-color-15" color="#ff9800">条件语句</font>

- `if` 语句：用于基于条件执行代码块。如果条件为真，则执行 `if` 代码块；否则，执行可选的 `elif`（如果有）或 `else` 代码块。
- `elif` 语句（可选）：用于添加额外的条件检查。可以有多个 `elif` 语句。
- `else` 语句（可选）：用于指定在所有条件都不满足时要执行的代码块。

- 示例
```python
x = 10
if x > 0:
    print("x是正数")
elif x == 0:
    print("x是零")
else:
    print("x是负数")
```
### <font class="text-color-141" color="#ff9800">循环语句</font>

	- `for` 循环：用于迭代遍历可迭代对象（如列表、字符串等）中的元素。每次迭代时，代码块都会执行一次，直到迭代结束或遇到 `break` 语句为止。
	- `while` 循环：在条件为真时重复执行代码块，直到条件为假或遇到 `break` 语句为止。
- 示例：
```python
# for循环
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print(fruit)

# while循环
count = 0
while count < 5:
    print(count)
    count += 1
```
- 在Python中，没有直接的 `fori` 循环，但是可以使用 `range()` 函数结合 `for` 循环来实现类似的功能。
	- `range()` 函数是Python内置函数，用于生成指定范围内的整数序列。它常用于 `for` 循环的迭代控制。

- 以下是一些示例，演示如何使用 `range()` 函数和 `for` 循环来实现类似 `fori` 循环的功能：
```python
# 使用range()迭代指定范围的整数
for i in range(5):
    print(i)  # 输出：0 1 2 3 4

# 指定起始值和结束值的范围
for i in range(1, 6):
    print(i)  # 输出：1 2 3 4 5

# 指定起始值、结束值和步长的范围
for i in range(0, 10, 2):
    print(i)  # 输出：0 2 4 6 8
```
### <font class="text-color-141" color="#ff9800">跳转语句</font>
- `break` 语句：用于跳出当前循环，不再执行循环中剩余的代码，并继续执行循环之后的代码。

- `continue` 语句：用于停止当前迭代，并继续执行下一次迭代。
- `pass` 语句：用于在代码块中占位，不执行任何操作，仅作为语法要求。
- 示例：
```python
# break语句
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    if fruit == "banana":
        break
    print(fruit)

# continue语句
numbers = [1, 2, 3, 4, 5]
for number in numbers:
    if number % 2 == 0:
        continue
    print(number)

# pass语句
x = 10
if x > 0:
    pass  # 占位，暂时不执行任何操作
```

## <font class="text-color-13" color="#ffeb3b">函数</font>
- 可以使用 `def` 关键字来定义函数。函数定义是一种创建可重用代码块的方式，可以接受参数并执行特定任务，可以在需要时多次调用。

- 定义函数的基本语法和步骤：
1. 使用 `def` 关键字声明函数：
```python
def function_name(parameters):
    # 函数体
    # 执行任务的代码
    # 可能包含返回语句
```
- `function_name` 是函数的名称，可以根据需求自行命名。
- `parameters` 是函数的参数列表，可以包含零个或多个参数，多个参数之间使用逗号进行分隔。

2. 编写函数体：
  
	  - 函数体是包含在函数定义中的一段代码块。
	  - 函数体内的代码定义了函数要执行的具体任务。
3. 返回结果（可选）：
  
	  - 在函数体内，可以使用 `return` 语句返回函数的结果。
	  - 如果没有指定返回值，函数将默认返回 `None`。

- 下面是一个简单的示例，展示了如何定义一个接收参数并返回结果的函数：
```python
def greet(name):
    """向给定的名称打招呼"""
    message = f"Hello, {name}! How are you today?"
    return message

# 调用函数
result = greet("Alice")
print(result)  # 输出: Hello, Alice! How are you today?
```
### <font class="text-color-141" color="#ff9800">参数默认值</font>
- 在定义函数时，可以为函数的参数指定默认值，使得在调用函数时可以选择性地传递参数。如果没有传递参数，则函数将使用默认值作为参数的值。
```python
def function_name(parameter1=default_value1, parameter2=default_value2, ...):
    # 函数体
    # 执行任务的代码
    # 可能包含返回语句
```
- 在函数定义中，可以在参数列表中为每个参数指定默认值。参数的默认值是在函数定义过程中确定的，而不是在函数调用时确定的。

- 示例
```python
def greet(name, greeting="Hello"):
    """向给定的名称打招呼，默认使用 "Hello"""
    message = f"{greeting}, {name}! How are you today?"
    return message

# 调用函数
result1 = greet("Alice")
result2 = greet("Bob", "Hi")

print(result1)  # 输出: Hello, Alice! How are you today?
print(result2)  # 输出: Hi, Bob! How are you today?
```
- 注意事项：

	- 在定义函数时，将带有默认值的参数放在参数列表的最后。
	- 可以为多个参数设置默认值，但在调用函数时仅按照参数的顺序省略某些参数。

### <font class="text-color-141" color="#ff9800">关键字参数</font>
- 关键字参数允许在函数调用时使用参数名来指定参数的值，而不必按照参数定义的顺序传递参数。这提供了更灵活和可读性更好的函数调用方式。
```python
def greet(name, message):
    print(f"Hello, {name}! {message}")

# 使用关键字参数进行函数调用
greet(name="John", message="How are you?")
# 输出：Hello, John! How are you?

# 关键字参数可以任意顺序使用
greet(message="Nice to meet you!", name="Alice")
# 输出：Hello, Alice! Nice to meet you?
```


### <font class="text-color-141" color="#ff9800">可变长度参数</font>
- 函数的可变参数允许函数接受不定数量的参数。这在处理不确定数量的输入时非常有用，因为它允许你编写更加灵活的函数。在Python中，有两种类型的可变参数：`*args` 和 `**kwargs` 。

1.  `*args`（星号参数）：
	*args用于传递不定数量的非关键字参数给函数。在函数定义中，*args表示一个元组（tuple），其中包含了传递给函数的所有位置参数。这样，函数就可以接受任意数量的参数。
```python
def my_function(*args):
    for arg in args:
        print(arg)

my_function(1, 2, 3, 4)

'''
1
2
3
4
'''
```
2. `**kwargs`（双星号参数）：
	**kwargs用于传递不定数量的关键字参数给函数。在函数定义中，**kwargs表示一个字典（dictionary），其中包含了传递给函数的所有关键字参数。这样，函数就可以接受任意数量的关键字参数。
```python
def my_function(**kwargs):
    for key, value in kwargs.items():
        print(key, value)

my_function(name='Alice', age=25, city='New York')

'''
name Alice
age 25
city New York
'''
```

### <font class="text-color-141" color="#ff9800">函数作为参数传递</font>
- 函数是一等公民，这意味着可以将函数作为参数传递给其他函数。这种将函数作为参数传递的方式可以帮助实现更灵活和可重用的代码。
```python
def greet(name):
    print(f"Hello, {name}!")

def greet_with_message(name, message):
    print(f"{message}, {name}!")

def greet_wrapper(func, name, *args, **kwargs):
    print("Before greeting")
    func(name, *args, **kwargs)
    print("After greeting")

# Pass greet function as an argument to greet_wrapper function
greet_wrapper(greet, "John")
# Output:
# Before greeting
# Hello, John!
# After greeting

# Pass greet_with_message function as an argument to greet_wrapper function
greet_wrapper(greet_with_message, "Alice", message="Nice to meet you")
# Output:
# Before greeting
# Nice to meet you, Alice!
# After greeting
```


### <font class="text-color-141" color="#ff9800">多返回值</font>
1. 使用元组返回多个值：
```python
def get_user_info():
    name = "John"
    age = 25
    city = "New York"
    return name, age, city

result = get_user_info()
print(result)  # 输出：("John", 25, "New York")

name, age, city = get_user_info()  # 将返回的元组进行解包
print(name)  # 输出："John"
print(age)  # 输出：25
print(city)  # 输出："New York"
```
2. 使用列表返回多个值：
```python
def get_numbers():
    return [1, 2, 3, 4, 5]

result = get_numbers()
print(result)  # 输出：[1, 2, 3, 4, 5]

# 可以通过索引访问列表中的元素
print(result[0])  # 输出：1
print(result[2])  # 输出：3
```
3. 使用字典返回多个值：
```python
def get_person():
    return {"name": "John", "age": 25, "city": "New York"}

result = get_person()
print(result)  # 输出：{"name": "John", "age": 25, "city": "New York"}

# 可以通过键访问字典中的值
print(result["name"])  # 输出："John"
print(result["age"])  # 输出：25
```

### <font class="text-color-141" color="#ff9800">lambda 函数</font>
- `lambda` 函数是一种匿名函数，它可以在需要一个简单函数的地方定义并使用，而无需显式地定义一个函数名称。`lambda` 函数通常用于一次性的、简单的函数操作，它们可以接收任意数量的参数，但只能有一个表达式作为函数体，并返回该表达式的结果。

- `lambda` 函数的语法如下：（`lambda` 关键字表示定义一个匿名函数，`arguments` 是函数的参数列表（可以包含多个参数），`expression` 是函数体，只能包含一个表达式。）
```python
lambda arguments: expression
```

1. 基本用法：
```python
add = lambda x, y: x + y
result = add(2, 3)
print(result)  # 输出：5
```
2. 与内置函数结合使用：
```python
numbers = [1, 2, 3, 4, 5]
squared_numbers = list(map(lambda x: x**2, numbers))
print(squared_numbers)  # 输出：[1, 4, 9, 16, 25]
```
3. 排序：
```python
students = [("Alice", 23), ("Bob", 20), ("Charlie", 21)]
students.sort(key=lambda student: student[1])
print(students)
# 输出：[("Bob", 20), ("Charlie", 21), ("Alice", 23)]
```

## <font class="text-color-13" color="#ffeb3b">随机数</font>
- 在Python中生成随机数，你可以使用 `random` 模块。`random` 模块提供了各种生成随机数的函数和方法。下面是一些常用的方法：

1. `random()` 函数：生成一个0到1之间的随机浮点数。
```python
import random

x = random.random()
print(x)  # 输出：0.123456789

```
2. `randint(a, b)` 函数：生成一个在指定范围内的随机整数，包括边界值 `a` 和 `b` 。
```python
import random

x = random.randint(1, 10)
print(x)  # 输出：6
```
3. `randrange(start, stop[, step])` 函数：生成一个指定范围内的随机整数，可以指定起始值、结束值和步长。与 `range()` 函数类似。
```python
import random

x = random.randrange(1, 10, 2)
print(x)  # 输出：7
```
4. `choice(seq)` 函数：从序列中随机选择一个元素。
```python
import random

items = [1, 2, 3, 4, 5]
x = random.choice(items)
print(x)  # 输出：3
```
5. `shuffle(seq)` 函数：对序列中的元素进行随机排序（就地修改原序列）。
```python
import random

items = [1, 2, 3, 4, 5]
random.shuffle(items)
print(items)  # 输出：[5, 3, 1, 4, 2]
```

## <font class="text-color-13" color="#ffeb3b">列表 (list)</font>
- 列表（List）是Python中最常用的数据类型之一，它是一个有序、可变、可重复的集合。列表以方括号 `[]` 表示，其中的元素通过逗号 `,` 分隔。

	1. 有序性：列表中的元素是有序排列的，元素的顺序与它们被添加到列表的顺序相同。

	2. 可变性：列表是可变的，即可以通过索引对元素进行修改、添加和删除操作。

	3. 可重复性：列表中可以包含重复的元素，同一个元素可以出现多次。

	4. 可以包含不同类型的元素：列表可以同时包含不同类型的元素，例如整数、浮点数、字符串、其他列表等。

	6. 动态性：列表的长度是可变的，可以根据需要动态地添加或删除元素。

	7. 可以存储大量元素：列表没有固定的容量限制，可以存储任意数量的元素。

	8. 支持索引和切片：可以使用索引和切片操作来访问列表中的元素或获取子列表。

#### <font class="text-color-61" color="#03a9f4">1. 创建列表：</font>
- 列表可以通过直接使用方括号 `[]` 来创建，或者使用内置的 `list()` 函数进行创建。

- 示例：
```python
# 创建空列表
empty_list = []
# 创建包含元素的列表
numbers = [1, 2, 3, 4, 5]
fruits = ['apple', 'banana', 'orange']
```

#### <font class="text-color-61" color="#03a9f4">2. 访问列表元素：</font>
- 可以使用索引运算符 `[]` 来访问列表中的元素。索引从0开始，可以使用正数或负数索引来访问列表中的元素。

- 示例：
```python
fruits = ['apple', 'banana', 'orange']
print(fruits[0])  # 输出: apple
print(fruits[-1])  # 输出: orange
```
### <font class="text-color-141" color="#ff9800">列表操作</font>

#### <font class="text-color-7" color="#03a9f4">1. 修改列表元素：</font>
	列表中的元素是可变的，可以通过索引对其进行修改。

- 示例：
```python
fruits = ['apple', 'banana', 'orange']
fruits[1] = 'kiwi'
print(fruits)  # 输出: ['apple', 'kiwi', 'orange']
```

#### <font class="text-color-61" color="#03a9f4">2. 添加元素：</font>

- `append()`：向列表末尾添加一个元素。
```python
fruits = ['apple', 'banana']
fruits.append('orange')
print(fruits)  # 输出: ['apple', 'banana', 'orange']
```

- `insert()`：在指定位置插入一个元素。
```python
fruits = ['apple', 'banana']
fruits.insert(1, 'orange')
print(fruits)  # 输出: ['apple', 'orange', 'banana']
```

#### <font class="text-color-61" color="#03a9f4">3. 删除元素：</font>
- `remove()`：根据值删除第一个匹配的元素。
```python
fruits = ['apple', 'banana', 'orange']
fruits.remove('banana')
print(fruits)  # 输出: ['apple', 'orange']
```
 - `pop()`：删除并返回指定索引位置的元素，默认删除最后一个元素。
```python
fruits = ['apple', 'banana', 'orange']
removed_fruit = fruits.pop(1)
print(removed_fruit)  # 输出: 'banana'
print(fruits)  # 输出: ['apple', 'orange']
```
- `del` 语句：根据索引删除元素。
```python
fruits = ['apple', 'banana', 'orange']
del fruits[1]
print(fruits)  # 输出: ['apple', 'orange']
```
- `clear()` 方法用于清空列表中的所有元素，使列表变为空列表
```python
fruits = ['apple', 'banana', 'orange']
fruits.clear()
print(fruits)  # 输出: []
```
#### <font class="text-color-61" color="#03a9f4">4. 切片操作：</font>
- 使用切片操作获取列表的子列表。
```python
numbers = [1, 2, 3, 4, 5]
sublist = numbers[1:3]
print(sublist)  # 输出: [2, 3]
```
#### <font class="text-color-61" color="#03a9f4">5. 合并列表：</font>
- 使用 `+` 运算符来合并两个或多个列表。
```python
fruits = ['apple', 'banana']
vegetables = ['carrot', 'tomato']
merged_list = fruits + vegetables
print(merged_list)  # 输出: ['apple', 'banana', 'carrot', 'tomato']
```
-  `extend()` 方法用于将一个可迭代对象的元素添加到列表的末尾，扩展列表的长度。
```python
fruits = ['apple', 'banana']
more_fruits = ['orange', 'kiwi']

fruits.extend(more_fruits)
print(fruits)  # 输出: ['apple', 'banana', 'orange', 'kiwi']
```

#### <font class="text-color-61" color="#03a9f4">6. 排序：</font>
- `sort()`：原地对列表进行升序排序。
```python
numbers = [3, 1, 4, 2]
numbers.sort()
print(numbers)  # 输出: [1, 2, 3, 4]
```

- `sorted()`：返回一个新的已排序的列表，不修改原列表。
```python
numbers = [3, 1, 4, 2]
sorted_numbers = sorted(numbers)
print(sorted_numbers)  # 输出: [1, 2, 3, 4]
```
- 如果你需要降序排序（从大到小），可以传递一个`reverse=True` 的参数。
```python
my_list = [4, 2, 1, 3]
sorted_list = sorted(my_list, reverse=True)
print(sorted_list) # 输出 [4, 3, 2, 1]
```

#### <font class="text-color-61" color="#03a9f4">7. 其他常用操作：</font>

- `len()`：获取列表的长度（元素个数）。
```python
fruits = ['apple', 'banana', 'orange']
print(len(fruits))  # 输出: 3
```
- `index()`：返回指定元素第一次出现的索引。
```python
fruits = ['apple', 'banana', 'orange']
index = fruits.index('banana')
print(index)  # 输出: 1
```
- `count()`：返回指定元素在列表中出现的次数。
```python
numbers = [1, 2, 3, 2, 4, 2]
count = numbers.count(2)
print(count)  # 输出: 3
```
- `reverse()`：反转列表中的元素顺序。
```python
numbers = [1, 2, 3, 4, 5]
numbers.reverse()
print(numbers)  # 输出: [5, 4, 3, 2, 1]
```
- 使用 `in` 运算符来检查元素是否存在于列表中
```python
fruits = ['apple', 'banana', 'orange']

if 'apple' in fruits:
    print("Fruits list contains 'apple'")

if 'grape' not in fruits:
    print("Fruits list does not contain 'grape'")
```
---
### <font class="text-color-141" color="#ff9800">遍历</font>
- 使用 `for` 循环可以便捷地遍历列表中的每个元素，不需要显式地指定索引。
```python
fruits = ['apple', 'banana', 'orange']

for fruit in fruits:
    print(fruit)
```
- 使用索引进行循环遍历：
	如果需要访问元素的索引或对元素进行更多的操作，可以使用索引进行循环遍历。
```python
fruits = ['apple', 'banana', 'orange']

for i in range(len(fruits)):
    print(fruits[i], "is at index", i)
```

## <font class="text-color-13" color="#ffeb3b">元组 (tuple)</font>
- 元组（Tuple）是Python中的一种数据类型，类似于列表，用于存储多个元素。元组是不可变的，即创建后不能修改。以下是关于元组的详细介绍：

#### <font class="text-color-61" color="#03a9f4">1. 创建元组：</font>
- 元组使用圆括号 `()` 来表示，其中的元素通过逗号 `,` 分隔。
```python
my_tuple = (1, 2, 3)
another_tuple = ('apple', 'banana', 'orange')
mixed_tuple = (1, 'apple', True)
```
- 注意：如果元组只有一个元素，需要在元素后面加一个逗号，否则会被当作普通的数据类型。
```python
t3 = (1,)
t4 = 1,
print(t3)  # 输出：(1,)
print(t4)  # 输出：(1,)
```


#### <font class="text-color-61" color="#03a9f4">2. 访问元组元素：</font>
- 可以使用索引运算符 `[]` 来访问元组中的元素。索引从0开始，可以使用正数或负数索引来访问元素。
```python
my_tuple = ('apple', 'banana', 'orange')
print(my_tuple[0])   # 输出: 'apple'
print(my_tuple[-1])  # 输出: 'orange'
```
#### <font class="text-color-61" color="#03a9f4">3. 元组的不可变性：</font>
- 元组是不可变的，一旦创建后，无法修改元组中的元素。这意味着不能添加、删除或修改元组的元素。
```python
my_tuple = ('apple', 'banana', 'orange')
my_tuple[0] = 'kiwi'  # 报错：元组不支持修改操作
```
- 然而，如果元组中包含可变的对象（例如列表），则可以修改列表对象的内容，但不能修改元组本身。
```python
my_tuple = ([1, 2, 3], 'apple', 'banana')

# 修改嵌套列表中的元素
my_tuple[0][1] = 4

print(my_tuple)  # 输出: ([1, 4, 3], 'apple', 'banana')
```
#### <font class="text-color-61" color="#03a9f4">4. 元组的特性：</font>
  
  - 元组可以包含不同类型的元素，例如整数、字符串、布尔值等。
  - 元组可以包含重复的元素。
  - 元组的长度是固定的，创建后不能改变。

### <font class="text-color-141" color="#ff9800">元组操作</font>
#### <font class="text-color-61" color="#03a9f4">切片操作：</font>
- 使用切片操作来获取元组的子元组。
```python
my_tuple = ('apple', 'banana', 'orange', 'kiwi')
sub_tuple = my_tuple[1:3]
print(sub_tuple)  # 输出: ('banana', 'orange')
```
#### <font class="text-color-61" color="#03a9f4">拼接元组：</font>
- 使用 `+` 运算符将两个元组合并成一个新的元组。
```python
tuple1 = ('apple', 'banana')
tuple2 = ('orange', 'kiwi')
merged_tuple = tuple1 + tuple2
print(merged_tuple)  # 输出: ('apple', 'banana', 'orange', 'kiwi')
```
#### <font class="text-color-61" color="#03a9f4">复制元组：</font>
- 使用 `*` 运算符复制元组的内容。
```python
my_tuple = ('apple', 'banana')
copied_tuple = my_tuple * 3
print(copied_tuple)  # 输出: ('apple', 'banana', 'apple', 'banana', 'apple', 'banana')
```
#### <font class="text-color-61" color="#03a9f4">元组解包：</font>
- 将元组的元素解包（按顺序赋值给多个变量）。
```python
my_tuple = ('apple', 'banana', 'orange')
fruit1, fruit2, fruit3 = my_tuple
print(fruit1)  # 输出: 'apple'
print(fruit2)  # 输出: 'banana'
print(fruit3)  # 输出: 'orange'
```
#### <font class="text-color-61" color="#03a9f4">元组比较：</font>
- 使用比较运算符（`<`, `<=`, `>`, `>=`, `==`, `!=`）比较两个元组的大小。（注：按照字典顺序的模式比较两个元组）
```python
tuple1 = ('apple', 'banana')
tuple2 = ('orange', 'kiwi')
print(tuple1 < tuple2)  # 输出: True
```
#### <font class="text-color-61" color="#03a9f4">元组长度：</font>
- 使用 `len()` 函数获取元组中元素的个数。
```python
my_tuple = ('apple', 'banana', 'orange')
length = len(my_tuple)
print(length)  # 输出: 3
```
#### <font class="text-color-61" color="#03a9f4">元素存在性检查：</font>
- 使用 `in` 或 `not in` 运算符检查元素是否存在于元组中。
```python
my_tuple = ('apple', 'banana', 'orange')
print('apple' in my_tuple)      # 输出: True
print('kiwi' not in my_tuple)   # 输出: True
```
#### <font class="text-color-61" color="#03a9f4">元组计数：</font>
- 使用 `count()` 方法计算指定元素在元组中出现的次数。
```python
my_tuple = ('apple', 'banana', 'orange', 'banana')
count = my_tuple.count('banana')
print(count)  # 输出: 2
```
#### <font class="text-color-61" color="#03a9f4">元组索引：</font>
- 使用 `index()` 方法查找指定元素的第一个匹配项的索引。
```python
my_tuple = ('apple', 'banana', 'orange', 'banana')
index = my_tuple.index('banana')
print(index)  # 输出: 1
```
#### <font class="text-color-61" color="#03a9f4">元组长度和最大/最小值：</font>
- 使用 `len()` 函数获取元组的长度（元素个数）。
- 使用 `max()` 函数获取元组中的最大值。
- 使用 `min()` 函数获取元组中的最小值。
```python
my_tuple = (3, 1, 4, 2)
length = len(my_tuple)
max_value = max(my_tuple)
min_value = min(my_tuple)
print(length)     # 输出: 4
print(max_value)  # 输出: 4
print(min_value)  # 输出: 1
```
### <font class="text-color-141" color="#ff9800">遍历</font>
- 使用 `for` 循环可以方便地遍历元组中的每个元素，无需显式指定索引。
```python
my_tuple = ('apple', 'banana', 'orange')

for item in my_tuple:
    print(item)
```
- 如果需要访问元素的索引或对元素进行更多的操作，可以使用索引进行循环遍历。
```python
my_tuple = ('apple', 'banana', 'orange')

for i in range(len(my_tuple)):
    print(my_tuple[i], "is at index", i)
```

## <font class="text-color-13" color="#ffeb3b">集合(set)</font>
### <font class="text-color-141" color="#ff9800">创建集合</font>
- 使用花括号 `{}` 定义集合：
```python
my_set = {1, 2, 3, 4, 5}
empty_set = {}
```
- 使用 `set()` 函数定义集合：
```python
my_set = set([1, 2, 3, 4, 5])
empty_set = set()
```

### <font class="text-color-141" color="#ff9800">集合操作</font>

#### <font class="text-color-61" color="#03a9f4">len(set)</font>
- 返回集合中元素的个数
```python
my_set = {1, 2, 3, 4, 5}
length = len(my_set)
print(length)  # 输出: 5
```
#### <font class="text-color-61" color="#03a9f4">add(element)</font>
- 向集合中添加元素
```python
my_set = {1, 2, 3}
my_set.add(4)
print(my_set)  # 输出: {1, 2, 3, 4}
```
#### <font class="text-color-61" color="#03a9f4">remove(element)</font>
- 从集合中删除指定元素
```python
my_set = {1, 2, 3, 4, 5}
my_set.remove(3)
print(my_set)  # 输出: {1, 2, 4, 5}
```
#### <font class="text-color-61" color="#03a9f4">discard(element)</font>
- 从集合中删除指定元素，如果元素不存在则不会引发错误
```python
my_set = {1, 2, 3, 4, 5}
my_set.discard(3)
print(my_set)  # 输出: {1, 2, 4, 5}
```
#### <font class="text-color-61" color="#03a9f4">pop()</font>
- 随机删除并返回集合中的一个元素
```python
my_set = {1, 2, 3, 4, 5}
removed_element = my_set.pop()
print(removed_element)  # 输出: 随机删除的一个元素
print(my_set)  # 输出: 删除后的集合
```
#### <font class="text-color-61" color="#03a9f4">clear()</font>
- 清空集合中的所有元素
```python
my_set = {1, 2, 3, 4, 5}
my_set.clear()
print(my_set)  # 输出: set()
```
#### <font class="text-color-61" color="#03a9f4">union(set1, set2, ...)</font>
- 返回多个集合的并集
```python
set1 = {1, 2, 3}
set2 = {3, 4, 5}
union_set = set.union(set1, set2)
print(union_set)  # 输出: {1, 2, 3, 4, 5}
```
#### <font class="text-color-61" color="#03a9f4">intersection(set1, set2, ...)</font>
- 返回多个集合的交集
```python
set1 = {1, 2, 3}
set2 = {3, 4, 5}
intersection_set = set.intersection(set1, set2)
print(intersection_set)  # 输出: {3}
```
#### <font class="text-color-61" color="#03a9f4">difference(set1, set2, ...)</font>
- 返回多个集合的差集
```python
set1 = {1, 2, 3}
set2 = {3, 4, 5}
difference_set = set.difference(set1, set2)
print(difference_set)  # 输出: {1, 2}
```
#### <font class="text-color-61" color="#03a9f4">symmetric_difference(set)</font>
- 返回集合与另一个集合的对称差集
```python
set1 = {1, 2, 3}
set2 = {3, 4, 5}
symmetric_difference_set = set1.symmetric_difference(set2)
print(symmetric_difference_set)  # 输出: {1, 2, 4, 5}
```
#### <font class="text-color-61" color="#03a9f4">difference_update()</font>
- 从当前集合中移除与其他集合的交集部分，即求当前集合与其他集合的差集，并将结果更新到当前集合中
```python
set1 = {1, 2, 3, 4, 5}
set2 = {4, 5, 6, 7}
set1.difference_update(set2)
print(set1)  # 输出: {1, 2, 3}
```
### <font class="text-color-141" color="#ff9800">集合遍历</font>
- 使用 `for` 循环遍历集合：
```python
my_set = {1, 2, 3, 4, 5}
for element in my_set:
    print(element)
```
- 将集合转换为列表后遍历：
```python
my_set = {1, 2, 3, 4, 5}
for element in list(my_set):
    print(element)
```
- 使用 `iter()` 和 `next()` 函数遍历集合：
```python
my_set = {1, 2, 3, 4, 5}
iterator = iter(my_set)
while True:
    try:
        element = next(iterator)
        print(element)
    except StopIteration:
        break
```

## <font class="text-color-13" color="#ffeb3b">字典(dictionary)</font>

### <font class="text-color-141" color="#ff9800">字典创建</font>
- 使用花括号 `{}` 定义字典：
```python
my_dict = {'key1': 'value1', 'key2': 'value2', 'key3': 'value3'}
empty_dict = {}
```
- 使用 `dict()` 函数定义字典：
```python
my_dict = dict(key1='value1', key2='value2', key3='value3')
empty_dict = dict()
```
- 使用键值对列表定义字典：
```python
my_dict = dict([('key1', 'value1'), ('key2', 'value2'), ('key3', 'value3')])
```
### <font class="text-color-141" color="#ff9800">字典访问元素</font>
- 可以使用键来访问字典中的元素。字典（Dictionary）是一种键值对（Key-Value）的数据结构，通过键来索引和获取对应的值。
```python
my_dict = {'name': 'John', 'age': 30, 'city': 'New York'}

# 使用键来获取对应的值
name = my_dict['name']
age = my_dict['age']
city = my_dict['city']

print(name)  # 输出: John
print(age)   # 输出: 30
print(city)  # 输出: New York
```
- 如果尝试使用不存在的键来访问字典，将会引发 `KeyError` 异常。因此，在访问字典元素之前，需要确保键存在于字典中。

- 可以使用 `in` 关键字来检查某个键是否存在于字典中。例如：
```python
if 'name' in my_dict:
    print("Key 'name' exists in the dictionary.")
else:
    print("Key 'name' does not exist in the dictionary.")
```

### <font class="text-color-141" color="#ff9800">字典操作</font>

#### <font class="text-color-61" color="#03a9f4">dictionary[key] = value</font>
- 使用键来设置字典中的值，如果键不存在，则会创建新的键值对。
```python
my_dict = {'name': 'John', 'age': 30, 'city': 'New York'}
my_dict['name'] = 'Jane'
my_dict['country'] = 'USA'
print(my_dict)  # 输出: {'name': 'Jane', 'age': 30, 'city': 'New York', 'country': 'USA'}
```

#### <font class="text-color-61" color="#03a9f4">get(key, default)</font>
- 使用键来获取字典中的值，如果键不存在，则返回默认值。
```python
my_dict = {'name': 'John', 'age': 30, 'city': 'New York'}
name = my_dict.get('name', 'Unknown')
address = my_dict.get('address', 'Not Found')
print(name)     # 输出: John
print(address)  # 输出: Not Found
```

#### <font class="text-color-61" color="#03a9f4">del</font>
- 使用 `del` 关键字结合键来删除字典中的元素。
```python
my_dict = {'name': 'John', 'age': 30, 'city': 'New York'}
del my_dict['age']
print(my_dict)  # 输出: {'name': 'John', 'city': 'New York'}
```

#### <font class="text-color-61" color="#03a9f4">pop(key, default)</font>
- 删除并返回指定键的值，同时可以指定一个默认值，如果键不存在则返回默认值。
```python
my_dict = {'name': 'John', 'age': 30, 'city': 'New York'}
age = my_dict.pop('age')
print(age)      # 输出: 30
print(my_dict)  # 输出: {'name': 'John', 'city': 'New York'}
```
#### <font class="text-color-61" color="#03a9f4">clear()</font>
- 删除字典中的所有键值对，使字典变为空字典。
```python
my_dict = {'name': 'John', 'age': 30, 'city': 'New York'}
my_dict.clear()
print(my_dict)  # 输出: {}
```

#### <font class="text-color-61" color="#03a9f4">in</font>
- 检查键是否存在于字典中，返回布尔值。
```python
my_dict = {'name': 'John', 'age': 30, 'city': 'New York'}
has_name = 'name' in my_dict
has_gender = 'gender' in my_dict
print(has_name)    # 输出: True
print(has_gender)  # 输出: False
```
#### <font class="text-color-61" color="#03a9f4">len()</font>
- 返回字典中键值对的个数。
```python
my_dict = {'name': 'John', 'age': 30, 'city': 'New York'}
length = len(my_dict)
print(length)  # 输出: 3
```

#### <font class="text-color-61" color="#03a9f4">keys()</font>
- 返回包含字典中所有键的视图（View）对象。
```python
my_dict = {'name': 'John', 'age': 30, 'city': 'New York'}
keys = my_dict.keys()
print(keys)  # 输出: dict_keys(['name', 'age', 'city'])
```

#### <font class="text-color-61" color="#03a9f4">values()</font>
- 返回包含字典中所有值的视图（View）对象。
```python
my_dict = {'name': 'John', 'age': 30, 'city': 'New York'}
values = my_dict.values()
print(values)  # 输出: dict_values(['John', 30, 'New York'])
```
#### <font class="text-color-61" color="#03a9f4">items()</font>
- 返回包含字典中所有键值对的视图（View）对象。
```python
my_dict = {'name': 'John', 'age': 30, 'city': 'New York'}
items = my_dict.items()
print(items)  # 输出: dict_items([('name', 'John'), ('age', 30), ('city', 'New York')])
```

### <font class="text-color-141" color="#ff9800">字典遍历</font>
1. 遍历键（keys）：
```python
my_dict = {"a": 1, "b": 2, "c": 3}

for key in my_dict:
    print(key)
```
```
a
b
c
```
2. 遍历值（values）：
```python
my_dict = {"a": 1, "b": 2, "c": 3}

for value in my_dict.values():
    print(value)
```
```
1
2
3
```
3. 遍历键值对（items）：
```python
my_dict = {"a": 1, "b": 2, "c": 3}

for key, value in my_dict.items():
    print(key, value)
```
```
a 1
b 2
c 3
```
## <font class="text-color-13" color="#ffeb3b">数据容器类型转换</font>
| 函数   | 描述                                                                                                    |
|--------|---------------------------------------------------------------------------------------------------------|
| set()  | 用于创建集合（set）或将其他可迭代对象转换为集合。集合是一种无序、不重复的数据容器。                                 |
| dict() | 用于创建字典（dictionary）或将其他可迭代对象转换为字典。字典是一种由键值对组成的数据容器。                              |
| list() | 用于创建列表（list）或将其他可迭代对象转换为列表。列表是一种有序、可变的数据容器。                                  |
| tuple()| 用于创建元组（tuple）或将其他可迭代对象转换为元组。元组是一种有序、不可变的数据容器。                                 |
| str()  | 用于将对象转换为字符串（str）。字符串是一种由字符组成的不可变序列。                                                 |

## <font class="text-color-13" color="#ffeb3b">文件</font>

### <font class="text-color-141" color="#ff9800">文件打开</font>
- `open()` 函数是Python内置的用于打开文件的函数，它接受两个参数：文件路径和打开模式，并返回一个文件对象。

- 语法
```python
open(file, mode='r', buffering=-1, encoding=None, errors=None, newline=None, closefd=True, opener=None)
```

- 参数

	- `file`：要打开的文件路径（包括文件名）。
	
	- `mode`（可选）：打开模式，默认为`'r'`（只读模式）。可以使用不同的模式来实现读取、写入、追加等操作。常见的打开模式包括：
	  - `'r'`：只读模式。默认模式。文件指针位于文件开头。
	  - `'w'`：写入模式。如果文件已存在，则会被覆盖；如果文件不存在，则创建新文件。
	  - `'a'`：追加模式。如果文件存在，文件指针位于文件末尾，内容将被追加到文件末尾；如果文件不存在，则创建新文件。
	  - `'x'`：独占创建模式。创建新文件，如果文件已存在，则会引发错误。
	  - `'b'`：二进制模式。用于处理二进制文件。
	  - `'t'`：文本模式（默认）。用于处理文本文件。
	- `buffering`（可选）：缓冲大小，用于控制读取或写入文件时的缓冲行为。默认为`-1`，表示使用系统默认的缓冲大小。
	- `encoding`（可选）：指定文件的编码方式，用于读取或写入文本文件。常见的编码方式包括`'utf-8'`、`'gbk'`等。
	- `errors`（可选）：指定编码错误的处理方式。常见的处理方式包括`'strict'`（默认，抛出异常）、`'ignore'`（忽略错误）、`'replace'`（用特定字符替换错误）等。
	- `newline`（可选）：用于控制文本文件中换行符的处理方式。常见的取值包括`None`（根据平台使用默认换行符）、`''`（不进行转换）和`'\n'`等。
	- `closefd`（可选）：指定是否关闭与文件描述符关联的底层文件。默认为`True`。
	- `opener`（可选）：用于指定自定义的文件打开器（类似于一个工厂函数），用于创建文件对象。默认为`None`。

### <font class="text-color-141" color="#ff9800">文件读取</font>
1. **read()**：
  
	  - 语法：`file.read(size=-1)`
	  - 功能：从文件中读取指定大小的数据或者读取整个文件内容。
	  - 参数：`size`（可选）表示要读取的字节数，默认值为`-1`，表示读取整个文件。
	  - 返回值：返回一个字符串，包含读取的数据。如果文件已经到达末尾，则返回空字符串。

2. **readline()**：
  
	  - 语法：`file.readline(size=-1)`
	  - 功能：从文件中读取一行数据。
	  - 参数：`size`（可选）表示要读取的最大字节数，默认值为`-1`，表示读取整行。
	  - 返回值：返回一个字符串，包含读取的一行数据。如果文件已经到达末尾，则返回空字符串。

3. **readlines()**：
  
	  - 语法：`file.readlines(sizehint=-1)`
	  - 功能：从文件中读取所有行，并将每行作为一个字符串放入列表中返回。
	  - 参数：`sizehint`（可选）表示要读取的最大字节数，默认值为`-1`，表示读取所有行。
	  - 返回值：返回一个包含文件所有行的列表。如果文件已经到达末尾，则返回空列表。
```python
# 打开文件
file_path = "path/to/file.txt"
file = open(file_path, "r")

# 使用read()方法读取文件内容
data = file.read()
print(data)

# 使用readline()方法读取文件一行内容
line = file.readline()
print(line)

# 使用readlines()方法读取文件所有行内容
lines = file.readlines()
print(lines)

# 关闭文件
file.close()
```
- 需要注意的是，这些`read()`方法读取文件内容时都会将文件指针移动到读取的位置，因此连续调用它们将会依次读取文件的内容。如果文件较大，建议逐行读取或者使用适当的缓冲区大小进行读取，以避免占用过多的内存。另外，确保在不再需要访问文件时及时关闭文件，以释放资源。

- `for` 循环读取文件
```python
# 打开文件
file_path = "path/to/file.txt"
file = open(file_path, "r")

# 直接在for循环中迭代文件对象
for line in file:
    # 处理每一行数据
    print(line)

# 关闭文件
file.close()
```
- 在使用 `for` 循环读取文件时，整个文件内容并不会一次性加载到内存中，而是逐行读取，因此适用于处理大文件。同时，在循环结束后，记得关闭文件以释放资源。

### <font class="text-color-141" color="#ff9800">文件关闭</font>
- `close()`方法是用于关闭文件的方法。当你完成对文件的读取、写入或其他操作后，应该使用`close()`方法来关闭文件，以确保释放资源并避免文件的意外修改。以下是对`close()`方法的详细解释：
```python
file.close()
```
- 在调用 `close()` 方法之后，将无法再对该文件进行读取、写入或其他操作。
- 如果在关闭文件之后尝试对文件进行操作，将会引发 `ValueError: I/O operation on closed file` 异常。
```python
# 打开文件
file_path = "path/to/file.txt"
file = open(file_path, "r")

# 读取文件内容
file_contents = file.read()
print(file_contents)

# 关闭文件
file.close()
```
- 使用 `with` 语句可以自动管理文件的打开和关闭，不需要显式调用`close()`方法。`with`语句会在代码块执行完毕后自动关闭文件。
```python
# 打开文件并读取内容
file_path = "path/to/file.txt"
with open(file_path, "r") as file:
    file_contents = file.read()
    print(file_contents)
# 在离开with块后，文件会自动关闭
```

### <font class="text-color-141" color="#ff9800">文件写入</font>
- 使用文件对象的 `write()` 方法将数据写入文件。
```python
# 打开文件
file_path = "path/to/file.txt"
file = open(file_path, "w")

# 写入数据
data = "Hello, World!"
file.write(data)

# 关闭文件
file.close()
```
- 可以使用 `with` 语句来自动管理文件的打开和关闭，无需显式调用`close()`方法。
```python
# 打开文件并写入数据
file_path = "path/to/file.txt"
with open(file_path, "w") as file:
    data = "Hello, World!"
    file.write(data)
# 在离开with块后，文件会自动关闭
```

- `flush()` 方法是用于将文件缓冲区中的数据立即写入文件的方法。在正常情况下，文件的写入操作会将数据先写入缓冲区，然后根据系统的策略将缓冲区的数据刷新到物理文件中。但是有时候我们需要立即将缓冲区中的数据写入文件，这时可以使用 `flush()` 方法。
```python
file.flush()
```
- 使用 `flush()` 方法会强制将缓冲区中的数据写入文件，无论缓冲区是否已满。
- 调用 `flush()` 方法后，文件对象仍然保持打开状态，可以继续对文件进行读取或写入操作。
- 通常情况下，文件对象会在文件关闭时自动刷新缓冲区，但在某些情况下（如程序异常终止），可能需要手动调用 `flush()` 方法以确保数据的持久化。
```python
# 打开文件
file_path = "path/to/file.txt"
file = open(file_path, "w")

# 写入数据
data = "Hello, World!"
file.write(data)

# 刷新缓冲区
file.flush()

# 关闭文件
file.close()
```

#### <font class="text-color-7" color="#03a9f4">追加写入</font>
- 使用追加模式 `"a"` 来打开文件，并通过 `write()` 方法将数据追加写入文件的末尾。
```python
# 打开文件
file_path = "path/to/file.txt"
file = open(file_path, "a")

# 追加写入数据
data = "Hello, World!"
file.write(data)

# 关闭文件
file.close()
```

## <font class="text-color-13" color="#ffeb3b">异常处理</font>
- 使用 `try-except-else-finally` 语句块来捕获、处理和清理异常。

- 语法
```python
try:
    # 可能引发异常的代码块
    # ...
except ExceptionType1:
    # 处理特定类型的异常1
    # ...
except ExceptionType2:
    # 处理特定类型的异常2
    # ...
except:
    # 处理其他异常情况
    # ...
else:
    # 当没有发生异常时执行的代码块
    # ...
finally:
    # 无论是否发生异常，都会执行的代码块
    # ...
```
- 示例
```python
try:
    # 可能引发异常的代码块
    num1 = int(input("请输入第一个数字: "))
    num2 = int(input("请输入第二个数字: "))
    result = num1 / num2
except ValueError:
    print("输入的不是有效的数字")
except ZeroDivisionError:
    print("除数不能为零")
else:
    print("结果:", result)
finally:
    print("程序执行结束")
```

## <font class="text-color-13" color="#ffeb3b">模块导入</font>
- 模块是一种组织和封装代码的方式，它可以包含变量、函数、类和其他可执行的代码。通过导入模块，可以在当前的Python程序中使用该模块中定义的功能。

1. 导入整个模块：
	- 要导入整个模块，可以使用 `import` 语句后跟模块的名称。例如，要导入名为 `math` 的模块，可以使用以下语句：
```python
import math
```
- 然后，可以通过 `模块名.成员` 的方式来访问模块中定义的变量、函数、类等。例如，要使用 `math` 模块中的 `sqrt` 函数计算平方根，可以使用以下语句：
```python
result = math.sqrt(16)
```
2. 导入特定的模块成员
	- 有时候只需要导入模块中的特定成员而不是整个模块。可以使用`from 模块名 import 成员名`的语法来实现。例如，要导入`math`模块中的`sqrt`函数，可以使用以下语句：
```python
from math import sqrt
```
- 现在可以直接使用`sqrt`函数，而无需使用模块名作为前缀：
```python
result = sqrt(16)
```
- 还可以一次导入多个成员，使用逗号分隔它们：
```python
from math import sqrt, sin, cos
```
3. 给导入的模块成员指定别名：
	- 在导入模块成员时，可以为它们指定别名，以便在代码中更方便地使用。使用`as`关键字来为成员指定别名。
```python
from math import sqrt as square_root
result = square_root(16)
```
4. 导入整个模块并给模块指定别名：
	- 可以使用`as`关键字为导入的整个模块指定别名，以简化模块名称的使用。
```python
import math as m
result = m.sqrt(16)
```
### <font class="text-color-141" color="#ff9800">`__mian__` </font>
-  `__main__` 是一个特殊的模块级别名称，用于指示当前执行的脚本是主程序（Main Program）。它在一个Python文件被直接执行时扮演重要的角色，而不是被导入为一个模块。

- 当Python解释器执行一个脚本时，它会将该脚本的全局作用域作为一个模块加载。对于当前执行的脚本，Python将设置内置变量 `__name__` 的值为 `__main__` 。这使得我们可以根据 `__name__` 的值来区分当前脚本是作为主程序执行还是作为模块导入。

1. **入口点判断：** 通过检查 `__name__` 的值，我们可以确定当前脚本是否被直接执行作为主程序入口点。如果 `__name__` 的值是 `__main__` ，则说明当前脚本是主程序，我们可以在其中执行一些初始化操作、调用函数等。如果脚本被作为模块导入，则 `__name__` 的值将是模块的名称，我们可以在其中定义可重用的功能。
```python
if __name__ == "__main__":
    # 主程序入口点的代码
    # ...
```
2. **模块测试：** 在编写模块时，可以将一些测试代码放在 `_main__` 中，以便在模块被直接执行时执行测试。这样可以提供一些简单的测试和示例，以验证模块的功能是否正常工作。
```python
# 模块的功能代码

def some_function():
    # 函数实现

# 测试代码
if __name__ == "__main__":
    # 执行一些测试和示例
    # ...
```

### <font class="text-color-141" color="#ff9800">`__all__` </font>
- `__all__` 是一个特殊的变量名，用于定义模块中应该被导入的公共接口（Public Interface）。它是一个可选的列表，包含了模块中可以被导入的变量、函数、类或其他对象的名称。

- 当我们使用 `from 模块名 import *` 语句导入一个模块时，该模块中所有没有以下划线开头的名称都会被导入到当前命名空间中。但是，如果模块定义了 `__all__` 变量，那么只有 `__all__` 列表中的名称才会被导入，其他名称将不会被导入。

- `__all__` 的主要作用是控制模块的公共接口，避免不必要的名称污染和导入。它提供了一种明确和可控的方式，让模块作者指定哪些名称应该被公开和导入，以及哪些名称应该被保留为内部使用。
```python
# 模块的功能代码

def public_function():
    # 公共函数的实现

def _private_function():
    # 私有函数的实现

class PublicClass:
    # 公共类的实现

class _PrivateClass:
    # 私有类的实现

# 指定公共接口
__all__ = ["public_function", "PublicClass"]
```

## <font class="text-color-13" color="#ffeb3b">包(package)</font>
- 包机制是一种用于组织和管理模块的层次结构。包是一个包含模块和子包的目录，它提供了一种将相关的模块组织在一起的方式。

### <font class="text-color-141" color="#ff9800">1. 包的结构</font>
- 一个包是一个带有特殊文件 `__init__.py` 的目录。这个目录可以包含其他模块文件和子包（即其他包）。 `__init__.py` 文件是一个可以为空的文件，它告诉Python该目录应该被视为一个包。
```python
my_package/
    __init__.py
    module1.py
    module2.py
    subpackage/
        __init__.py
        module3.py
        module4.py
```
### <font class="text-color-141" color="#ff9800">2. 导入包和模块</font>
- 要导入包或模块，可以使用 `import` 语句。例如，要导入包中的模块 `module1.py`
```python
import my_package.module1
```
- 然后，可以通过 `包名.模块名` 的方式来访问模块中定义的变量、函数、类等。
```python
my_package.module1.some_function()
```
- 还可以使用`from`语句导入特定的模块或成员。例如，要导入模块 `module1.py` 中的函数 `some_function()`
```python
from my_package.module1 import some_function
```
### <font class="text-color-141" color="#ff9800">3. 包的相对导入</font>
- 在一个包内部，可以使用相对导入来引用同一包内的其他模块。相对导入使用点（`.`）表示当前包的层次结构。
```python
# 在 my_package.subpackage.module3 中导入 my_package.module1
from ..module1 import some_function
```
- 在上述示例中，`..`表示返回到上一级包（`my_package`），然后通过`module1`导入`some_function()`。

### <font class="text-color-141" color="#ff9800">4. `__init__.py` 的作用</font>
- `__init__.py`文件在包目录中起着重要的作用。它可以包含初始化代码，用于设置包的环境或导入其他模块。此外，它还可以定义`__all__`变量，以控制导入包时的公共接口。
```python
# __init__.py文件中的初始化代码

print("Initializing my_package...")

# 一些初始化代码
# ...

# 定义公共接口
__all__ = ['module1', 'module2']
```

### <font class="text-color-141" color="#ff9800">5. 嵌套包</font>
- 包可以嵌套在其他包中，形成更复杂的层次结构。例如，可以有一个包`my_package`，它包含子包`subpackage`，而`subpackage`又包含更多的子包和模块。

## <font class="text-color-13" color="#ffeb3b">JSON</font>
- JSON（JavaScript Object Notation）是一种轻量级的数据交换格式，常用于将数据从一个应用程序传输到另一个应用程序。它以易于阅读和编写的文本格式表示结构化数据，并且易于解析和生成。JSON格式基于JavaScript语法，但它是独立于编程语言的，因此可以在多种编程语言中使用。

- JSON的主要功能包括：

	1. 数据序列化和反序列化：JSON可以将数据对象序列化为字符串，以便在不同的系统和平台之间传输和存储数据。它还可以将JSON字符串反序列化为数据对象，使其可以在应用程序中进行处理和操作。

	2. 数据交换和通信：JSON广泛用于客户端和服务器之间的数据交换。Web应用程序通常使用JSON来传输数据，例如通过AJAX请求从服务器获取数据，或将数据提交到服务器。

	3. 配置文件：JSON格式非常适合用于配置文件，可以轻松地定义和组织配置选项，并以易读的方式进行编辑和管理。

	4. API数据传输：许多Web服务和API都使用JSON格式作为数据交换的标准。当使用HTTP请求和响应传输数据时，JSON提供了一种通用的格式，使得不同系统之间可以方便地共享和解析数据。

	5. 数据存储：JSON可以用作非关系型数据库（如MongoDB）中的数据存储格式。它提供了一种灵活的方式来表示和查询数据。

### <font class="text-color-141" color="#ff9800">python 操作 JSON</font>
- Python提供了内置的json模块，可以方便地进行JSON数据的解析和生成。使用json模块，你可以将Python数据转换为JSON格式，以及将JSON数据转换为Python数据结构。

- 将Python数据转换为JSON字符串（序列化）：
```python
import json

data = {
    "name": "John",
    "age": 30,
    "city": "New York"
}

json_str = json.dumps(data)
print(json_str)
```
```
{"name": "John", "age": 30, "city": "New York"}
```
- 将Python字典列表转换为JSON字符串（序列化）:
```python
import json

data = [
    {"name": "John", "age": 30},
    {"name": "Alice", "age": 25}
]

json_str = json.dumps(data)
print(json_str)
```
```
[{"name": "John", "age": 30}, {"name": "Alice", "age": 25}]
```

- 对于包含多个JSON对象的列表，可以使用相应的函数进行处理。例如，可以使用`json.dumps()`将多个Python对象列表转换为JSON字符串，或使用`json.loads()`将JSON字符串转换回多个Python对象列表。
```python
import json

data1 = {"name": "John", "age": 30}
data2 = {"name": "Alice", "age": 25}

json_str = json.dumps([data1, data2])
print(json_str)
```
```
[{"name": "John", "age": 30}, {"name": "Alice", "age": 25}]
```

- 将JSON字符串转换为Python数据（反序列化）：
```python
import json

json_str = '{"name": "John", "age": 30, "city": "New York"}'

data = json.loads(json_str)
print(data)
```
```
{'name': 'John', 'age': 30, 'city': 'New York'}
```

- 注意：
	- `ensure_ascii`是`json.dumps()`函数的一个可选参数。它控制着是否将非ASCII字符转义为ASCII字符序列。
	- 默认情况下，`ensure_ascii`的值为`True`，表示将非ASCII字符转义为ASCII字符序列。这意味着，例如，中文字符将被转义为Unicode编码的转义序列，如"\uXXXX"，其中"XXXX"表示字符的Unicode码点。
	- 如果将`ensure_ascii`设置为`False`，则`json.dumps()`函数将保留非ASCII字符，而不进行转义。这在需要保留非ASCII字符的情况下很有用，例如保存包含特殊字符的文本数据。
```python
import json

data = {"name": "张三"}

# 将非ASCII字符转义为ASCII字符序列
json_str = json.dumps(data, ensure_ascii=True)
print(json_str)  # 输出: {"name": "\u5f20\u4e09"}

# 保留非ASCII字符
json_str = json.dumps(data, ensure_ascii=False)
print(json_str)  # 输出: {"name": "张三"}
```

## <font class="text-color-13" color="#ffeb3b">单元测试</font>
* unittest库是一个用于编写单元测试的标准库。它提供了一组用于编写、运行和组织测试用例的工具。

1. 导入unittest库：
	- 首先，您需要导入unittest库。在Python脚本中，可以使用以下语句导入unittest：
```python
import unittest
```

2. 创建测试类：
	- 接下来，您需要创建一个继承自unittest.TestCase的测试类。每个测试用例都是测试类的一个方法。
```python
class MyTestCase(unittest.TestCase):
    def test_something(self):
        # 测试用例的代码
        pass

    def test_another_thing(self):
        # 测试用例的代码
        pass
```

3. 编写测试用例：
 	- 在测试类中，您可以编写测试用例方法。测试用例方法的名称必须以`test_`开头，这样unittest库才能自动识别它们并运行测试。
```python
def test_addition(self):
    result = 2 + 3
    self.assertEqual(result, 5)

def test_subtraction(self):
    result = 5 - 3
    self.assertEqual(result, 2)
```
- 在上面的示例中，我们编写了两个测试用例，一个测试加法，另一个测试减法。使用`self.assertEqual()`断言方法来断言实际结果与预期结果是否相等。

4. 运行测试用例：
	- 要运行测试用例，可以使用 unittest 库提供的测试运行器。最简单的方法是使用`unittest.main()`函数来自动发现并运行所有的测试用例。
```python
if __name__ == '__main__':
    unittest.main()
```

5. 执行测试：
	- 运行脚本后，测试运行器将自动发现并运行测试用例。它将显示测试结果，表明测试是否通过。
```
..
----------------------------------------------------------------------
Ran 2 tests in 0.001s

OK
```
- 其中 `..` 表示两个测试用例都通过了。

### <font class="text-color-141" color="#ff9800">测试方法</font>
- 在unittest库中，有许多常用的测试方法可用于对测试条件进行断言。这些断言方法允许您验证预期结果与实际结果是否相符。

| 断言方法                             | 描述                                                                                     |
|-----------------------------------|-----------------------------------------------------------------------------------------|
| assertEqual(a, b)                  | 断言a等于b。                                                                              |
| assertNotEqual(a, b)               | 断言a不等于b。                                                                             |
| assertTrue(x)                      | 断言x为True。                                                                             |
| assertFalse(x)                     | 断言x为False。                                                                            |
| assertIs(a, b)                     | 断言a是b（即a和b是同一个对象）。                                                            |
| assertIsNot(a, b)                  | 断言a不是b（即a和b不是同一个对象）。                                                          |
| assertIsNone(x)                    | 断言x是None。                                                                             |
| assertIsNotNone(x)                 | 断言x不是None。                                                                           |
| assertIn(a, b)                     | 断言a在b中（例如，a是b的一个元素）。                                                         |
| assertNotIn(a, b)                  | 断言a不在b中。                                                                            |
| assertIsInstance(a, b)             | 断言a是b类型的实例。                                                                       |
| assertNotIsInstance(a, b)          | 断言a不是b类型的实例。                                                                     |
| assertRaises(exception, callable)  | 断言在调用callable时会引发异常。                                                           |
| assertAlmostEqual(a, b, places=7)  | 断言a和b在给定的小数位数上近似相等。                                                         |
| assertNotAlmostEqual(a, b, places=7) | 断言a和b在给定的小数位数上不近似相等。                                                        |
| assertGreater(a, b)                | 断言a大于b。                                                                              |
| assertGreaterEqual(a, b)           | 断言a大于等于b。                                                                           |
| assertLess(a, b)                   | 断言a小于b。                                                                              |
| assertLessEqual(a, b)              | 断言a小于等于b。                                                                           |

### <font class="text-color-141" color="#ff9800">预设操作</font>
1. `setUp()` 方法在测试方法之前执行，用于设置测试环境和数据。
2. 执行具体的测试方法（测试代码）。
3. `tearDown()` 方法在测试方法执行后执行，用于清理测试环境，释放资源或进行必要的收尾工作。

- 这种测试方法执行顺序确保了每个测试方法都在独立的测试环境中运行，不受其他测试方法的影响。
```python
import unittest

class MyTestCase(unittest.TestCase):
    # setUp方法在测试方法之前执行
    def setUp(self):
        # 设置测试环境和数据
        self.x = 10
        self.y = 20

    def test_addition(self):
        result = self.x + self.y
        self.assertEqual(result, 30)

    def test_subtraction(self):
        result = self.y - self.x
        self.assertEqual(result, 10)

    # tearDown方法在测试方法执行后执行
    def tearDown(self):
        # 清理测试环境或释放资源（如果有需要）
        pass

if __name__ == '__main__':
    unittest.main()
```

