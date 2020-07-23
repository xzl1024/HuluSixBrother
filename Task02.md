# Task02 条件循环结构

## 2.1 if语句

### 2.1.1 简单的if语句

最简单的if语句只有一个测试和一个操作：  

```python
if conditional_test:
do something  
```

### 2.1.2 if -else语句

经常需要在条件测试通过了时执行一个操作，并在没有通过时执行另一个操作；在这种情况下，可使用Python提供的if-else语句。 if-else语句块类似于简单的if语句，但其中的else语句让你能够指定条件测试未通过时要执行的操作。  

```python
age = 17
 if age >= 18:
print("You are old enough to vote!")
print("Have you registered to vote yet?")
else:
print("Sorry, you are too young to vote.")
print("Please register to vote as soon as you turn 18!")
```



### 2.1.3 if-else-else 语句

经常需要检查超过两个的情形，为此可使用Python提供的if-elif-else结构。 Python只执行if-elif-else结构中的一个代码块，它依次检查每个条件测试，直到遇到通过了的条件测试。测试通过后， Python将执行紧跟在它后面的代码，并跳过余下的测试。  

```python
age = 12
 if age < 4:
print("Your admission cost is $0.")
 elif age < 18:
print("Your admission cost is $5.")
 else:
print("Your admission cost is $10.")
```

### 2.1.4 assert 关键字

Python assert（断言）用于判断一个表达式，在表达式条件为 false 的时候触发异常。断言可以在条件不满足程序运行的情况下直接返回错误，而不必等待程序运行后出现崩溃的情况。

```python
#语法
assert expression
assert expression [, arguments]
```

## 2.2 循环语句

### 2.2.1while 循环

for循环用于针对集合中的每个元素都一个代码块，而while循环不断地运行，直到指定的条件不满足为止。  

```python
current_number = 1
while current_number <= 5:
  print(current_number)
  current_number += 1
```

### 2.2.2while- else循环

​	当while循环正常结束后执行else后面的语句，非正常结束时不执行else

```python
i = 1
while i <= 5:
    if i == 3:
        print("try again")
        break
    print("sorry")
    i += 1
else:
    print("hahahh")
```

### 2.2.3 for循环

```python
"""
for 临时变量 in 序列
"""

str1 = 'itheima'
for i in str1:
    print(i)

```

### 2.2.4 for -else 循环

​	当for循环正常结束后执行else后面的语句，非正常结束时不执行else

```python
str1 = 'itheima'
for i in str1:
    if i == 'e':
        continue
    print(i)
else:
    print("end")
```

### 2.2.5 range()函数

python range() 函数可创建一个整数列表，一般用在 for 循环中。

```python
range(start, stop[, step])
```

参数说明：

- start: 计数从 start 开始。默认是从 0 开始。例如range（5）等价于range（0， 5）;
- stop: 计数到 stop 结束，但不包括 stop。例如：range（0， 5） 是[0, 1, 2, 3, 4]没有5
- step：步长，默认为1。例如：range（0， 5） 等价于 range(0, 5, 1)

### 2.2.6 enumerate()函数

enumerate() 函数用于将一个可遍历的数据对象(如列表、元组或字符串)组合为一个索引序列，同时列出数据和数据下标，一般用在 for 循环当中。

```python
enumerate(sequence, [start=0])
```

- sequence -- 一个序列、迭代器或其他支持迭代对象。

- start -- 下标起始位置。

  ```python
  seq = ['one', 'two', 'three']
  for i, element in enumerate(seq):
      print i, element
      
  ###########
  0 one
  1 two
  2 three
  ```

### 2.2.7 break语句

Python break语句，就像在C语言中，打破了最小封闭for或while循环。

break语句用来终止循环语句，即循环条件没有False条件或者序列还没被完全递归完，也会停止执行循环语句。

break语句用在while和for循环中。

如果您使用嵌套循环，break语句将停止执行最深层的循环，并开始执行下一行代码。

### 2.2.8 continue 语句

Python continue 语句跳出本次循环，而break跳出整个循环。

continue 语句用来告诉Python跳过当前循环的剩余语句，然后继续进行下一轮循环。

continue语句用在while和for循环中。

### 2.2.9 pass语句

Python pass 是空语句，是为了保持程序结构的完整性。

**pass** 不做任何事情，一般用做占位语句。

## 2.3推导式

### 2.3.1列表推导式

```python
#[ expr for value in collection [if condition] ]
x = [i ** 2 for i in range(1, 10)]
print(x)
# [1, 4, 9, 16, 25, 36, 49, 64, 81]
```

### 2.3.2 集合推导式

```python
#{ expr for value in collection [if condition] }
c = {i for i in [1, 2, 3, 4, 5, 5, 6, 4, 3, 2, 1]}
print(c)
# {1, 2, 3, 4, 5, 6}
```

### 2.3.3 元组推导式

```python
#( expr for value in collection [if condition] )
a = (x for x in range(10))
print(a)
print(tuple(a))

# (0, 1, 2, 3, 4, 5, 6, 7, 8, 9)
```

### 2.3.4 字典推导式

```python
#{ key_expr: value_expr for value in collection [if condition] }
b = {i: i % 2 == 0 for i in range(10) if i % 3 == 0}
print(b)
# {0: True, 3: False, 6: True, 9: False}
```

## 参考资料：

https://www.runoob.com/python3/python3-assert.html

https://github.com/datawhalechina/team-learning-program/blob/master/Python-Language/04.%20%E5%BE%AA%E7%8E%AF%E8%AF%AD%E5%8F%A5.md

Python编程：从入门到实践/（美） 埃里克-马瑟斯（Eric Matthes）著