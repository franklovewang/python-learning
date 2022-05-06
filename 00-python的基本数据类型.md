# 1 python的基本数据类型

## 1.1 Number(数字)



## 1.2 String(字符串)



## python 转义字符

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

## 1.3 List(列表)



## 1.4 Tuple(元组)



## 1.5 Set(集合)



## 1.6 Dictionary(字典)