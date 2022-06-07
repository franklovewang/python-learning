# 1 python的基本数据类型

## 1.1 Number(数字)



## 1.2 String(字符串)

### 1.2.1 %占位符格式化字符串

| 占位符 | 描述                             |
| ------ | -------------------------------- |
| %s     | 字符串(采用 str()的显示)         |
| %r     | 字符串(采用 repr()的显示)        |
| %c     | 单个字符                         |
| %b     | 二进制整数                       |
| %d     | 十进制整数                       |
| %i     | 十进制整数                       |
| %o     | 八进制整数                       |
| %x     | 十六进制整数                     |
| %e     | 指数 (基底写为 e)                |
| %E     | 指数 (基底写为 E)                |
| %f     | 浮点数                           |
| %F     | 浮点数，与上相同                 |
| %g     | 指数(e)? 或浮点数 (根据显示长度) |
| %G     | 指数(E)或浮点数 (根据显示长度)   |

```python
# %s: 字符串占位符
print('my name is %s.' % 'frank') ---> my name is frank.
# %d：十进制整数
print('my age is %d.' % 20) ---> my age is 20.
# %f: 浮点数
print('my salary is %f.' % 10000.2) ---> my salary is 10000.200000.
#%f: 保留一位小数
print('my salary is %.1f.' % 10000.2) ---> my salary is 10000.2.

```

### 1.2.2 str.format()格式化字符串

```python
# {[index][:[[fill]align][sign][#][m][,][.n][type]]}
index: 参数的序号或者键
fill: 填充的字符
align: 对齐方式：< 左对齐；> 右对齐；^ 居中对齐；= 右对齐符号在最左侧，需要配合占位宽度使用
sign: 符号选项：+ 正数正号，负数负号；- 正数不变，负数负号；'' 空格，正数加空格，负数负号
#: 0x 十六进制;0o 八进制；0b 二进制
m: 占位宽度
.n: 小数位数
type: 格式化字符串类型 s d b x o f
```

#### 1.2.2.1 字符串类型

```python
# index
print('格式化内容为：{0} {1} {0}'.format(1, 2)) ---> 格式化内容为：1 2 1

# fill: * ^: 居中对齐 20：占位宽度 s: 字符串类型
print('{:*^20s}'.format(' hello world ')) ---> *** hello world ****

# 20: 占位宽度 s：字符串类型，默认是左对齐
print('|{:20s}|'.format('Hello World')) ---> |Hello World         |

# >: 右对齐 20: 占位宽度 s：字符串类型
print('|{:>20s}|'.format('Hello World')) ---> |         Hello World|

# 20: 占位宽度 .2: 截取2位 s：字符串类型，默认是左对齐
print('|{:20.2s}|'.format('Hello World')) ---> |He                  |
```

#### 1.2.2.2 整数

```python
# 20：占位宽度 d: 整数类型，默认是右对齐
print('格式化整数为：|{:20d}|'.format(23)) ---> 格式化整数为：|                  23|
# 0：填充符 20：占位宽度 d: 整数类型，默认是右对齐
print('格式化整数为：|{:020d}|'.format(23)) ---> 格式化整数为：|00000000000000000023|
# d: 十进制 x: 十六进制 o: 八进制 b: 二进制
print('|{0:d}|{0:x}|{0:o}|{0:b}|'.format(13)) ---> |13|d|15|1101|
# #: 显示对应的进制
print('|{0:d}|{0:#x}|{0:#o}|{0:#b}|'.format(13)) ---> |13|0xd|0o15|0b1101|
# + - ' '
# 默认情况，正数不显示，负数显示
print('|{:d}|{:d}|'.format(13, -14)) ---> |13|-14|
# +：正数正号，负数负号
print('|{:+d}|{:+d}|'.format(13, -14)) ---> |+13|-14|
# -：正数不显示，负数负号，等同于默认情况
print('|{:-d}|{:-d}|'.format(13, -14)) ---> |13|-14|
# ' '：正数加空格，负数负号
print('|{: d}|{: d}|'.format(13, -14)) ---> | 13|-14|
```

#### 1.2.2.3 浮点数

```python
# f: 浮点数，默认保存6位小数
print('{:f}'.format(123.456)) ---> 123.456000
# .2: 保留2位小数 f: 浮点类型
print('{:.2f}'.format(123.456)) ---> 123.46
# 20: 占位宽度 .2: 保留2位小数 f: 浮点类型 默认是右对齐
print('|{:20.2f}|'.format(123.456)) ---> |              123.46|
# <: 左对齐 20: 占位宽度 .2: 保留2位小数 f: 浮点类型
print('|{:<20.2f}|'.format(123.456)) ---> |123.46              |
# 0: 填充符 >: 右对齐 20: 占位宽度 .2: 保留2位小数 f: 浮点类型 
print('|{:0>20.2f}|'.format(123.456)) ---> |00000000000000123.46|
```

#### 1.2.2.4 参数传递

```python
# index: 位置参数
print('位置参数：{2} {1} {0}'.format(1, 2, 3)) ---> 位置参数：3 2 1
# index: 关键字参数
print('关键字参数：{name} {age} {sex}'.format(name='frank', age=22, sex='male')) ---> 关键字参数：frank 22 male

# 案例
par = (1, 2, 3)
print('tuple类型：{0[0]} {0[1]} {0[2]}'.format(par)) ---> tuple类型：1 2 3

d = {'name': 'frank', 'age': 22, 'sex': 'male'}
print('dict类型：{0[name]} {0[age]} {0[sex]}'.format(d)) ---> dict类型：frank 22 male

# 千分位案例
# ,：千分位自动加逗号
print('{:,.2f}'.format(1223453.456)) ---> 1,223,453.46
```

### 1.2.3 f-string

```python
name = 'frank'
age = 18
sex = 'male'
salary = 28000.300
print('姓名：{}，年龄：{}，性别：{}'.format(name, age, sex)) ---> 姓名：frank，年龄：18，性别：male
print(f'姓名：{name}，年龄：{age}，性别：{sex}') ---> 姓名：frank，年龄：18，性别：male
print(f'姓名：{name:s}，年龄：{age:010d}，性别：{sex:.2s}，薪水：{salary:,.2f}') ---> 姓名：frank，年龄：0000000018，性别：ma，薪水：28,000.30
# f-string的功能增强，可以直接调用方法
print(f'姓名：{name.capitalize():s}，年龄：{age:010d}，性别：{sex:.2s}，薪水：{salary:,.2f}') ---> 姓名：Frank，年龄：0000000018，性别：ma，薪水：28,000.30
```

### 1.2.4 python 转义字符

| 转移字符 | 描述                                     |
| -------- | ---------------------------------------- |
| \        | (在尾行时)续行符                         |
| \        | 反斜杠符号                               |
| \\'      | 单引号                                   |
| \\"      | 双引号                                   |
| \\a      | 响铃                                     |
| \\b      | 退格(Backspace)                          |
| \\e      | 转义                                     |
| \\000    | 空                                       |
| \\n      | 换行                                     |
| \\v      | 纵向制表符                               |
| \\t      | 横向制表符                               |
| \\r      | 回车                                     |
| \\f      | 换页                                     |
| \\oyy    | 八进制，yy代表字符，例如：\012代表换行   |
| \\xyy    | 十六进制，yy代表字符，例如：\x0a代表换行 |
| \\other  | 其它的字符以普通格式输出                 |

```python
>>> print('hello \
... world')
hello world

>>> print('hello \ world')
hello \ world

>>> print("Who's it?")
Who's it?

>>> print('he said "Hello?"')
he said "Hello?"

>>> print('hello \a world')
hello  world # 电脑会发出声音

>>> print('hello\bworld')
hellworld # 少了个o

>>> print('hello\000world')
hello world

>>> print('hello\nworld')
hello
world

>>> print('hello\tworld')
hello   world

>>> print('hello\rworld')
world # world把hello覆盖掉了
```

### 1.2.5 常用的字符串方法

```python
>>> dir(str)
['__add__', '__class__', '__contains__', '__delattr__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__getitem__', '__getnewargs__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__iter__', '__le__', '__len__', '__lt__', '__mod__', '__mul__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__rmod__', '__rmul__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', 'capitalize', 'casefold', 'center', 'count', 'encode', 'endswith', 'expandtabs', 'find', 'format', 'format_map', 'index', 'isalnum', 'isalpha', 'isascii', 'isdecimal', 'isdigit', 'isidentifier', 'islower', 'isnumeric', 'isprintable', 'isspace', 'istitle', 'isupper', 'join', 'ljust', 'lower', 'lstrip', 'maketrans', 'partition', 'replace', 'rfind', 'rindex', 'rjust', 'rpartition', 'rsplit', 'rstrip', 'split', 'splitlines', 'startswith', 'strip', 'swapcase', 'title', 'translate', 'upper', 'zfill']
```

```python
# S.split(seq): 根据分割符进行切割，得到一个列表
>>> string = 'I love Python'
>>> string.split(' ')
['I', 'love', 'Python']

>>> site = 'www.baidu.com'
>>> site.split('.')
['www', 'baidu', 'com']
```

```python
# S.strip(): 去掉字符串两头的空格
# S.lstrip(): 去掉字符串左边的空格
# S.rstrip(): 去掉字符串右边的空格
>>> S = ' Hello World '
>>> S.strip()
'Hello World'

>>> S = ' Hello'
>>> S.lstrip()
'Hello'

>>> S = 'Hello '
>>> S.rstrip()
'Hello'
```

```python
# S.upper()：将字符转换成大写
>>> S = 'frank'
>>> S.upper()
'FRANK'
```

```python
# S.lower(): 将字符转换成小写
>>> S = 'HELLO'
>>> S.lower()
'hello'
```

```python
# S.capitalize(): 首字母大写
>>> S = 'frank'
>>> S.capitalize()
'Frank'
```

```python
# S.isupper()： 判断S中的字母是否全是大写
>>> S = 'FRANK'
>>> S.isupper()
True

>>> S = 'frank'
>>> S.isupper()
False
```

```python
# S.islower(): 判断S中的字母是否全小写
>>> S = 'FRANK'
>>> S.islower()
False

>>> S = 'frank'
>>> S.islower()
True
```

```python
# S.istitile(): 判断S中的字母是否大写开头，其他字母都是小写
>>> S = 'Frank'
>>> S.istitle()
True

>>> S = 'FRANK'
>>> S.istitle()
False
```

```python
# join: 拼接字符串
>>> lst = ['I', 'love', 'Python']
>>> ' '.join(lst)
'I love Python'
```



## 1.3 List(列表)



## 1.4 Tuple(元组)



## 1.5 Set(集合)



## 1.6 Dictionary(字典)