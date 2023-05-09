# *Python的基本语法*

## 编码

默认情况下，Python3源码文件以UTF-8编码，所有的字符串都是unicode字符串。当然也可以为源码文件指定不同的编码：
> ```# -*-coding: cp-1252 -*-```

上述定义允许在源文件中使用Windows-1252字符集中的字符编码，对应适合语言为保加利亚语、白罗斯语、马其顿语、俄语、塞尔维亚语。
___

## 标识符
- 第一个字符必须是字符表中字母或下划线`_`.
- 标识符的其他的部分由字母、数字和下划线组成。
- 标识符对大小写敏感。

在Python3中，可以使用中文作为变量名，非ASC11标识符也是允许的了。
____
## Python保留字(关键字)
保留字即关键字，不能把它们用作任何标识符名称。Python的标准库提供了一个Keyword模块，可以输出当前版本的所有关键字。
> \>>> import keyword

> \>>> keyword kwlist
```python 
['False','None', 'True', 'and', 'as', 'assert', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']
```
___
## 注释

> 单行注释使用#开头
> 多行注释使用多个#或者 
> > `'''` 和 `"""`

___
## 行与缩进
python最具特色的就是使用缩进来表示代码块，不需要使用大括号`{}`。

缩进的空格数是可变的，但是同一个代码块的语句必须包含相同的缩进空格数。
实例：
```python
if True:
    print("True")
else:
    print("False")
```
但是下面的代码最后一行语句缩进的空格数不一致，就会导致运行错误：
```python
if True:
    print("Answer")
    print("True")
else:
    print("Answer")
 print("False")     # 缩进不一致，会导致运行错误
 ```
 以上程序由于缩进不一致，执行后会出现类似以下错误：
 > File "test.py", line 6
    print ("False")    # 缩进不一致，会导致运行错误
                                      ^
IndentationError: unindent does not match any outer indentation level

___
## 多行语句
Python 通常是一行写完一条语句，但如果语句很长，我们可以使用反斜杠```\```来实现多行语句，例如：
```python
total = item_one + \
        item_two + \
        item_three
```
但是在[],{}或()中的多行语句，不需要使用反斜杠`\`，例如：
```python
total = ['item_one', 'item_two', 'item_three',
        'item_four', 'item_five']
```
___
## 数字(Number)类型

python中数字有四种类型：整数、布尔型、浮点数和复数。

- int (整数), 如 1, 只有一种整数类型 int，表示为长整型，没有python2 中的 Long。
- bool(布尔)，如True。
- float(浮点数)，如1.23、3e-2
- complex(复数),如1+2j\1.1+2.2j
___
## 字符串(String)
- Python中的单引号`'`和双引号`'`使用完全相同。
- 使用三引号(`'''`或`"""`)可以指定一个多行字符串，也可以用作多行注释，例如：
```python
"""
这是一个
多行注释
注释
"""
 
data = """name  # 姓名
age   # 年龄
sex   # 性别
"""
print(data)
```
输出结果为：
>name  # 姓名
>age   #年龄
>sex   #性别
- 反斜杠可以用来转义，使用`r` 可以让反斜杠不发生转义。 如 r"this is a line with \n" 则`\n`会显示，并不是换行。
- 按字面意义级联字符串，如 "this " "is " "string" 会被自动转换为 this is string。
- 字符串可以用`+`运算符连接在一起，用`*`运算符重复。
- Python 中的字符串有两种索引方式，从左往右以`0`(下标)开始，从右往左以`-1`开始。
- Python中的字符串不能改变。
- Python 没有单独的字符类型，一个字符就是长度为 1 的字符串。
- 字符串的截取的语法格式如下：`变量[头下标:尾下标:步长]
```python
word = '字符串'
sentence = "这是一个句子。"
paragraph = """这是一个段落，
可以由多行组成"""
```
实例:
```python
str='123456789'
 
print(str)                 # 输出字符串
print(str[0:-1])           # 输出第一个到倒数第二个的所有字符
print(str[0])              # 输出字符串第一个字符
print(str[2:5])            # 输出从第三个开始到第五个的字符
print(str[2:])             # 输出从第三个开始后的所有字符
print(str[1:5:2])          # 输出从第二个开始到第五个且每隔一个的字符（步长为2）
print(str * 2)             # 输出字符串两次
print(str + '你好')         # 连接字符串
 
print('------------------------------')
 
print('hello\npengkun')      # 使用反斜杠(\)+n转义特殊字符
print(r'hello\npengkun')     # 在字符串前面添加一个 r，表示原始字符串，不会发生转义
```
以上实例输出结果:
```
123456789
12345678
1
345
3456789
24
123456789123456789
123456789你好
------------------------------
hello
pengkun
hello\npengkun
```
这里的 r 指 raw，即 raw string，会自动将反斜杠转义，例如：
```python
print('\n')     # 输出空行
print(r'\n')    # 输出 \n
```
___
## 空行

函数之间或类的方法之间用空行分隔，表示一段新的代码的开始。类和函数入口之间也用一行空行分隔，以突出函数入口的开始。
空行与代码缩进不同，空行并不是 Python 语法的一部分。书写时不插入空行，Python 解释器运行也不会出错。但是空行的作用在于分隔两段不同功能或含义的代码，便于日后代码的维护或重构。

>记住：空行也是程序代码的一部分。
___



