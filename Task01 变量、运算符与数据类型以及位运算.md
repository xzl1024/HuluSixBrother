# Task01 变量、运算符与数据类型以及位运算

## 1.1 注释

### 1.1.1 单行注释

在Python中使用#来表示单行注释，#后的内容都属于注释，注释的内容将会被解释器所忽略。

```python
#这是一个注释

print('hello python')
```

### 1.1.2多行注释

```python
'''
这是多行注释 

他也可以用双引号来表示！
'''
"""
这也是多行注释
"""
print('hello world')
```

## 1.2运算符

### 1.2.1算数运算符

```python
#+加法运算符（如果是两个字符串之间进行加法运算，则会进行拼串操作）

#-减法运算符

#*乘法运算符（如果将字符串和数字相乘，则会对字符串进行复制操作，将字符串重复指定次数）

#/ 除法运算符，运算时结果总会返回一个浮点类型

#// 整除，只会保留计算后的整数位，总会返回一个整型

#** 幂运算，求一个值的几次幂

#% 取模，求两个数相除的余数
b = 10 + 5 # 计算
b = 'hello' + ' ' + 'world' # 拼串

b = 10 - 5 # 计算
b = 5 - True 
b = b - 2 # 用变量b的值减去2，然后再赋值给b
# b = 'hello' - 'h' TypeError

b = 5 * 5

b = 5 / 2
# b = 5 / 0 ZeroDivisionError: division by zero
b = 10 / 3
b = 10 // 3

b = 10 ** 5
b = 16 ** 0.5 # 求16的平方根

b = 10 % 5 # 0
b = 10 % 4 # 2
b = 10 % 3 # 1
b = 10 % 2 # 0

print("b =",b)
```

### 1.2.2比较运算符

关系运算符用来比较两个值之间的关系，总会返回一个布尔值，如果关系成立，返回True，否则返回False

| **>**      | **比较左侧值是否大于右侧值**                         |
| ---------- | ---------------------------------------------------- |
| **>=**     | **比较左侧的值是否大于或等于右侧的值**               |
| **<**      | **比较左侧值是否小于右侧值**                         |
| **<=**     | **比较左侧的值是否小于或等于右侧的值**               |
| **==**     | **比较两个对象的值是否相等**                         |
| **!=**     | **比较两个对象的值是否不相等**                       |
| **is**     | **比较两个对象是否是同一个对象，比较的是对象的id**   |
| **is not** | **比较两个对象是否不是同一个对象，比较的是对象的id** |

```python
result = 10 > 20 # False
result = 30 > 20 # True
result = 30 < 20 # False
result = 10 >= 10 # True

result = 2 > True # True
# result = 2 > '1' TypeError: '>' not supported between instances of 'int' and 'str'

# 0032 > 0031
result = '2' > '1' # True
result = '2' > '11' # True

# 在Python中可以对两个字符串进行大于（等于）或小于（等于）的运算，
#   当对字符串进行比较时，实际上比较的是字符串的Unicode编码
#   比较两个字符串的Unicode编码时，是逐位比较的
result = 'a' > 'b' # False
result = 'c' < 'd' # True
result = 'ab' > 'b' # False

# print(int('2') > int('11'))

result = 1 == 1 # True
result = 'hello' == 'hello' # True
result = 'abc' == 'bcd' # False
result = 'abc' != 'bcd' # True
result = 1 == True # True
result = 1 is True # False
result = 1 is not True # True
print('result =',result)
print(id(1),id(True))
```

### 1.2.3逻辑运算符

逻辑运算符主要用来做一些逻辑判断。

- not 逻辑非

not可以对符号右侧的值进行非运算

对于布尔值，非运算会对其进行取反操作，True变False，False变True

对于非布尔值，非运算会先将其转换为布尔值，然后再取反

```python

a = True
a = not a # 对a进行非运算

a = 1
a = ''
a = not a
# print('a =',a)
```

- and 逻辑与

and可以对符号两侧的值进行与运算

只有在符号两侧的值都为True时，才会返回True，只要有一个False就返回False

与运算是找False的

Python中的与运算是短路的与，如果第一个值为False，则不再看第二个值

```python
result = True and True # True
result = True and False # False
result = False and True # False
result = False and False # False
```

- or 逻辑或

or 可以对符号两侧的值进行或运算

或运算两个值中只要有一个True，就会返回True

或运算是找True的

Python中的或运算是短路的或，如果第一个值为True，则不再看第二个值

```python
result = True or True # True
result = True or False # True
result = False or True # True
result = False or False # False
```

- 非布尔值的与或运算

   当我们对非布尔值进行与或运算时，Python会将其当做布尔值运算，最终会返回原值
   **与运算的规则**
      与运算是找False的，如果第一个值是False，则不看第二个值
      如果第一个值是False，则直接返回第一个值，否则返回第二个值
  **或运算的规则**
      或运算是找True的，如果第一个值是True，则不看第二个值
      如果第一个值是True，则直接返回第一个值，否则返回第二个值    

```python

# True and True
result = 1 and 2 # 2
# True and False
result = 1 and 0 # 0
# False and True
result = 0 and 1 # 0
# False and False
result = 0 and None # 0

# True or True
result = 1 or 2 # 1
# True or False
result = 1 or 0 # 1
# False or True
result = 0 or 1 # 1
# False or False
result = 0 or None # None

print(result)
```

-  条件运算符（三元运算符）
   **语法：** 语句1 if 条件表达式 else 语句2
   **执行流程：**
     条件运算符在执行时，会先对条件表达式进行求值判断
         如果判断结果为True，则执行语句1，并返回执行结果
         如果判断结果为False，则执行语句2，并返回执行结果

  ```python
  a = 30
  b = 50
  
  # print('a的值比较大！') if a > b else print('b的值比较大！')
  # 获取a和b之间的较大值
  max = a if a > b else b
  
  print(max)
  ```

  ### 1.2.4运算符优先级

  

  | 运算符                   | 优先级                   |
  | ------------------------ | ------------------------ |
  | **                       | 指数 (最高优先级)        |
  | ~ + -                    | 按位翻转, 一元加号和减号 |
  | * / % //                 | 乘，除，取模和取整除     |
  | + -                      | 加法减法                 |
  | >> <<                    | 右移，左移运算符         |
  | &                        | 位 'AND'                 |
  | ^ \|                     | 位运算符                 |
  | <= < > >=                | 比较运算符               |
  | <> == !=                 | 等于运算符               |
  | = %= /= //= -= += *= **= | 赋值运算符               |
  | is is not                | 身份运算符               |
  | in not in                | 成员运算符               |
  | not and or               | 逻辑运算符               |

### 1.2.5位运算符

| 位运算符 | 说明                                 |
| -------- | ------------------------------------ |
| <<       | 按位左移，左移n位相当于乘以2的n次方  |
| >>       | 按位右移 ，左移n位相当于除以2的n次方 |
| &        | 按位与，二进制位数同且为1结果位为1   |
| l        | 按位或 ，二进制位数或有1结果位为1    |
| ^        | 按位异或 ，二进制位数不同结果位为1   |
| ~        | 按位取反，二进制位0和1结果位互换     |

```python
a = 60            # 60 = 0011 1100 
b = 13            # 13 = 0000 1101 
c = 0
 
c = a & b;        # 12 = 0000 1100
print "1 - c 的值为：", c
 
c = a | b;        # 61 = 0011 1101 
print "2 - c 的值为：", c
 
c = a ^ b;        # 49 = 0011 0001
print "3 - c 的值为：", c
 
c = ~a;           # -61 = 1100 0011
print "4 - c 的值为：", c
 
c = a << 2;       # 240 = 1111 0000
print "5 - c 的值为：", c
 
c = a >> 2;       # 15 = 0000 1111
print "6 - c 的值为：", c
```

## 1.3变量与数据类型

### 1.3.1变量与标识符

- Python中使用变量，不需要声明，直接为变量赋值即可。

- 在Python中所有可以自主命名的内容都属于标识符
  标识符中可以含有字母、数字、_，但是不能使用数字开头，标识符不能是Python中的关键字和保留字， 也不建议使用Python中的函数名作为标识符,因为这样会导致函数被覆盖。

### 1.3.2数据类型

- 数值

  **Python数值分成了三种：整数、浮点数（小数）、复数**
   **在Python中所有的整数都是int类型**

  Python中的整数的大小没有限制，可以是一个无限大的整数，如果数字的长度过大，可以使用下划线作为分隔符

  ```python
  c = 123_456_789
  ```

   也可以通过运算符来对数字进行运算，并且可以保证整数运算的精确

  ```python
  c = -100
  c = c + 3
  ```

   **浮点数（小数），在Python中所有的小数都是float类型**

  ```python
  c = 1.23
  c = 4.56
  ```

   对浮点数进行运算时，可能会得到一个不精确的结果

  ```python
  c = 0.1 + 0.2  0.30000000000000004
  
  print(c)
  ```

- 字符串

  字符串用来表示一段文本信息，字符串是程序中使用的最多的数据类型

  在Python中字符串需要使用引号引起来

  ```python
  s = 'hello'
  pyt
  s = abc # 字符串必须使用引号引起来，不使用不是字符串
  ```

  引号可以是双引号，也可以是单引号，但是注意不要混着用

  ```python
  s = 'hello'
  s = "hello"
  s = 'hello" #引号不能混合使用  SyntaxError: EOL while scanning string literal
  ```

  使用三重引号来表示一个长字符串 ''' """,三重引号可以换行，并且会保留字符串中的格式

  **转义字符**

  可以使用 \ 作为转义字符，通过转义字符，可以在字符串中使用一些特殊的内容

  ![image-20200722211457977](C:\Users\14403\AppData\Roaming\Typora\typora-user-images\image-20200722211457977.png)

- 布尔值

### 1.3.3数据类型的转换

-  int() 可以用来将其他的对象转换为整型

    布尔值：True -> 1   False -> 0
    浮点数：直接取整，省略小数点后的内容
    字符串：合法的整数字符串，直接转换为对应的数字
    如果不是一个合法的整数字符串，则报错 ValueError: invalid literal for int() with base 10: '11.5'
    对于其他不可转换为整型的对象，直接抛出异常 ValueError

- float() 和 int()基本一致，不同的是它会将对象转换为浮点数

- str() 可以将对象转换为字符串

   True -> 'True'
   False -> 'False'
   123 -> '123' 

- bool() 可以将对象转换为布尔值，任何对象都可以转换为布尔值

  对于所有表示空性的对象都会转换为False，其余的转换为True

  ```python
  a = int(a)
  
  a = False
  a = int(a)
  
  a = '123'
  a = int(a)
  
  a = 11.6
  a = int(a)
  
  a = '11.5'
  # a = int(a)
  
  a = None
  # a = int(a)
  
  a = 1
  a = float(a)
  
  a = False
  a = float(a)
  
  a = 123
  a = str(a)
  
  a = None
  a = bool(a)
  
  print('a =',a)
  print('a的类型是',type(a))
  ```

  



### 参考资料：

https://www.runoob.com/python/python-operators.html#ysf8

https://blog.csdn.net/GrofChen/article/details/91374573

http://www.atguigu.com/download_detail.shtml?v=124