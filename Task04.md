# Task04  字符串、列表、元组

## 1.字符串

```python
a = 'hello world'
b = "abcdefg"
print(type(a))
print(type(b))

name1 = 'Tom'
name2 = "Rose"

name3 = ''' Tom '''
name4 = """ Rose """
a = ''' i am Tom,
nice to meet you! '''
b = """ i am Rose,
nice to meet you! """

print('hello world')
name = 'Tom'
print('我的名字是%s' % name)
print(f'我的名字是{name}')

name = input('请输⼊入您的名字： ')
print(f'您输⼊入的名字是{name}')
print(type(name))
password = input('请输⼊入您的密码： ')
print(f'您输⼊入的密码是{password}')
print(type(password)

name = "abcdef"
print(name[1])
print(name[0])
print(name[2])

name = "abcdefg"
print(name[2:5:1]) # cde
print(name[2:5]) # cde
print(name[:5]) # abcde
print(name[1:]) # bcdefg
print(name[:]) # abcdefg
print(name[::2]) # aceg
print(name[:-1]) # abcdef, 负1表示倒数第⼀一个数据
print(name[-4:-1]) # def
print(name[::-1]) # gfedcba

rfind()： 和find()功能相同，但查找⽅方向为右侧开始。
rindex()：和index()功能相同，但查找⽅方向为右侧开始
count()：返回某个⼦子串串在字符串串中出现的次数
mystr = "hello world and itcast and itheima and Python"
print(mystr.find('and')) # 12
print(mystr.find('and', 15, 30)) # 23
print(mystr.find('ands')) # -1

mystr = "hello world and itcast and itheima and Python"
print(mystr.index('and')) # 12
print(mystr.index('and', 15, 30)) # 23
print(mystr.index('ands')) # 报错

mystr = "hello world and itcast and itheima and Python
print(mystr.count('and')) # 3
print(mystr.count('ands')) # 0
print(mystr.count('and', 0, 20)) # 1

#字符串串序列列.replace(旧⼦子串串, 新⼦子串串, 替换次数)
mystr = "hello world and itcast and itheima and Python"
# 结果： hello world he itcast he itheima he Python
print(mystr.replace('and', 'he'))
# 结果： hello world he itcast he itheima he Python
print(mystr.replace('and', 'he', 10))
# 结果： hello world and itcast and itheima and Python
print(mystr)

#字符串串序列列.split(分割字符, num)
mystr = "hello world and itcast and itheima and Python"
# 结果： ['hello world ', ' itcast ', ' itheima ', ' Python']
print(mystr.split('and'))
# 结果： ['hello world ', ' itcast ', ' itheima and Python']
print(mystr.split('and', 2))
# 结果： ['hello', 'world', 'and', 'itcast', 'and', 'itheima', 'and', 'Python']
print(mystr.split(' '))
# 结果： ['hello', 'world', 'and itcast and itheima and Python']
print(mystr.split(' ', 2))

#join()：⽤用⼀一个字符或⼦子串串合并字符串串，即是将多个字符串串合并为⼀一个新的字符串串
#字符或⼦子串串.join(多字符串串组成的序列列)
list1 = ['chuan', 'zhi', 'bo', 'ke']
t1 = ('aa', 'b', 'cc', 'ddd')
# 结果： chuan_zhi_bo_ke
print('_'.join(list1))
# 结果： aa...b...cc...ddd
print('...'.join(t1))

#capitalize()：将字符串串第⼀一个字符转换成⼤大写。
mystr = "hello world and itcast and itheima and Python"
# 结果： Hello world and itcast and itheima and python
print(mystr.capitalize())

#title()：将字符串串每个单词⾸首字⺟母转换成⼤大写。
mystr = "hello world and itcast and itheima and Python"
# 结果： Hello World And Itcast And Itheima And Python
print(mystr.title())

#lower()：将字符串串中⼤大写转⼩小写。
#upper()：将字符串串中⼩小写转⼤大写。
mystr = "hello world and itcast and itheima and Python"
# 结果： hello world and itcast and itheima and python
print(mystr.lower())
mystr = "hello world and itcast and itheima and Python"
# 结果： HELLO WORLD AND ITCAST AND ITHEIMA AND PYTHON
print(mystr.upper())

#lstrip()：删除字符串串左侧空⽩白字符。
#rstrip()：删除字符串串右侧空⽩白字符。
#strip()：删除字符串串两侧空⽩白字符

#ljust()：返回⼀一个原字符串串左对⻬齐,并使⽤用指定字符(默认空格)填充⾄至对应⻓长度 的新字符串串。
#rjust()：返回⼀一个原字符串串右对⻬齐,并使⽤用指定字符(默认空格)填充⾄至对应⻓长度 的新字符串串，语法和
#ljust()相同。
#center()：返回⼀一个原字符串串居中对⻬齐,并使⽤用指定字符(默认空格)填充⾄至对应⻓长度 的新字符串串，语
#法和ljust()相同。
      
  '''  startswith()：检查字符串串是否是以指定⼦子串串开头，是则返回 True，否
始和结束位置下标，则在指定范围内检查。
语法
字符串串序列列.startswith(⼦子串串, 开始位置下标, 结束位置下标)'''
mystr = "hello world and itcast and itheima and Python "
# 结果： True
print(mystr.startswith('hello'))
# 结果False
print(mystr.startswith('hello', 5, 20))\
      
"""    
endswith()：：检查字符串串是否是以指定⼦子串串结尾，是则返回 True，否则返回 False。如果设置开
始和结束位置下标，则在指定范围内检查。
isalpha()：如果字符串串⾄至少有⼀一个字符并且所有字符都是字⺟母则返回 True, 否则返回 False。
isdigit()：如果字符串串只包含数字则返回 True 否则返回 False。
 字符串串序列列.endswith(⼦子串串, 开始位置下标, 结束位置下标)
 """
mystr = "hello world and itcast and itheima and Python"
# 结果： True
print(mystr.endswith('Python'))
# 结果： False
print(mystr.endswith('python'))
# 结果： False
print(mystr.endswith('Python', 2, 20))
1 2 3 4 5 6 7 8 9
10
mystr1 = 'hello'
mystr2 = 'hello12345'
# 结果： True
print(mystr1.isalpha())
# 结果： False
print(mystr2.isalpha())
1 2 3 4 5 6 7 8
#isalnum()：如果字符串串⾄至少有⼀一个字符并且所有字符都是字⺟母或数字则返 回 True,否则返回False。
#isspace()：如果字符串串中只包含空⽩白，则返回 True，否则返回 False。
mystr1 = 'aaa12345'
mystr2 = '12345'
# 结果： False
print(mystr1.isdigit())
# 结果： False
print(mystr2.isdigit())
1 2 3 4 5 6 7 8
mystr1 = 'aaa12345'
mystr2 = '12345-'
# 结果： True
print(mystr1.isalnum())
# 结果： False
print(mystr2.isalnum())
1 2 3 4 5 6 7 8
mystr1 = '1 2 3 4 5'
mystr2 = ' '
# 结果： False
print(mystr1.isspace())
# 结果： True
print(mystr2.isspace())
1 2 3 4 5 6 7 8
```



## 2.列表

```python
name_list = ['rode', 'cro', 'rose']
print(name_list)
# 1..index()
print(name_list.index('cro'))

# 2..count()
print(name_list.count('rose'))
# 3.len
print(len(name_list))

# 4. in name_list
print('cro' in name_list)
print('cro' not in name_list)

# 5.用户输入账号
name = input('请输入您的邮箱账号名：')
if name in name_list:
    print(f'您输入的名字是{name},名字已经存在')
else:
    print(f'您输入的名字是{name},名字不存在')


```



```python
name_list = ['TOM', 'ROSE', 'LILY']
# 6..append():列尾结尾增加数据
# 追加数据时 如追加的是一个序列 将增加的是整个序列
name_list.append([11, 22])
print(name_list)
# 7..extend()  如追加的是一个序列(字符串也是序列) 将逐一追加
name_list.extend('xiaoming')
name_list.append(['xiaoming', 'xiaohong'])
print(name_list)
# 8..insert() 指定位置新增数据
name_list.insert(1,'aaa')
print(name_list)
```

```python
name_list = ['TOM', 'ROSE', 'LILY']
# 1.del 可以删除整个列表或者指定下表
del name_list
print(name_list)
# 2.pop() 删除指定下标 不指定就是默认最后一个  返回被删除的数据
del_name = name_list.pop()
print(del_name)
print(name_list)

# 3.remove(数据)
name_list.remove('ROSE')
print(name_list)
# 4.clear()清空数据
name_list.clear()
print(name_list)

```

```python
name_list = ['TOM', 'ROSE', 'LILY']
# 1.函数copy()
name_list2 = name_list.copy()
print(name_list2)
# 2.while
# i = 0
# while i < len(name_list):
#     print(name_list[i])
#     i += 1
# 3.for
for i in name_list:
    print(i)

```

```python
import random
from typing import List, Any

teachers = ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', ]
offices = [[], [], []]
for name in teachers:
    num = random.randint(0, 2)
    offices[num].append(name)
# print(offices)
i = 1
for office in offices:
    print(f'办公室{i}人数是{len(office)},老师是：')
    for name in office:
        print(name)
    i += 1

```



## 3.元组

```python
# 元组内的数据是不能修改的
# 1.多个数据元组
t1 = (10, 20, 30)
print(type(t1))  # tuple
# 2.单个数据元组
t1 = (10,)
print(type(t1))  # tuple
# 3.单个数据的元组不加逗号
t1 = (10)
print(type(t1))  # int

print('###########################################')
# 元组的常见操作
t1 = ('aa', 'bb', 'cc', 'dd', 'ee')
# 1.按下标查找
print(t1[0])
# 2.index() 出现的下标
print(t1.index('bb'))
# 3.count() 出现的次数
print(t1.count('aa'))
# 4.len() 元组的长度
print(len(t1))
# 5.修改元组内列表的数据
t2 = ('aa', 'bb', ['cc', 'dd'])
t2[2][0] = 'ff'
print(t2[2][0])

```

