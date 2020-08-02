# Task06 函数与Lambda表达式



```python
# 函数要先定义再使用
def sel_fun():
    print("显示余额：")
    print("存款：")
    print("取款：")


print("恭喜您登陆成功！")
sel_fun()

print("您的余额是100000000")
sel_fun()

print("取了100元钱")
sel_fun()

# 函数要先定义再使用
def info_print():
    print('hello world')


info_print()


def add_num1(num1, num2):
    result = num1 + num2
    print(result)


add_num1(1, 2)


def buy():
    return '烟'


goods = buy()
print(goods)


def add(a, b):
    """求和函数"""
    return a + b


res = add(4, 5)
print(res)


# help() 查看函数的说明文档（函数的说明文档）
# help(len)
# help(add)
# help(add_num1)
def sum_num1(a, b):
    """
    求和函数
    :param a:
    :param b:
    :return:
    """
    return a + b
help(sum_num1)

# 函数嵌套调用
def testB():
    print('------testB-Start------')
    print('testB')
    print('------testB-End------')


def testA():
    print('------testA-Start------')
    testB()
    print('------testA-End------')


testA()


# 1.打印一条横线
def print_line():
    print('-' * 20)


print_line()


# 2.打印多条横线

def print_lines(num):
    i = 0
    while i < num:
        print_line()
        i += 1


print_lines(5)


# 3.函数计算
def sum_num(a, b, c):
    return a + b + c


result = sum_num(1, 2, 3)
print(result)


# 任意三个数求平均值
def average_num(a, b, c):
    sumResult = sum_num(a, b, c)
    return sumResult / 3


averageResult = average_num(1, 2, 3)
print(averageResult)

# 变量的作用域
# 1.局部变量  在函数体内部使用
def testA():
    a = 100
    print(a)


testA()
# print(a)  NameError: name 'a' is not defined
# 2.全局变量 函数体内外都能访问
b = 120
print(b)


def testB():
    print(b)


def testC():
    print(b)


testB()
testC()
# 3.修改全局变量的值
b = 120
print(b)


def testB():
    global b  # 先global声明b为全局变量，然后在重新赋值
    b = 200
    print(b)


def testC():
    print(b)


testB()
testC()
# 多函数程序执行流程
# 1.共享全局变量
glo_num = 0


def test1():
    global glo_num
    glo_num = 100


def test2():
    print(glo_num)


test1()
test2()


# 2.返回值作为参数传递
def test3():
    return 50


def test4(num):
    print(num)


result = test3()
test4(result)

# 函数的多个返回值
'''
def return_num():
    return 1  # 只执行第一个
    return 2


result = return_num()
print(result)
'''


def return_num():
    return 1, 2  # 返回元组(1,2)


'''
return (10, 20)  # 元组
 return [10, 20]  # 列表
 return {'name': 'python'}  # 字典
'''

result = return_num()
print(result)


# 函数的参数
# 1.位置参数 调用函数时根据函数的定义的参数位置来传递参数
def user_info(name, age, gender):
    print(f'您的名字是{name},年龄是{age},性别是{gender}')


user_info('Tom', 20, 'Man')
# 2.关键字参数 通过"键=值"的形式加以指定
user_info('xiaoming', gender='man', age=16)


# 3.缺省参数  调用函数若不传如默认参数，则使用默认，若传入则修改
def user_info1(age, name, gender='Man'):
    print(f'您的名字是{name},年龄是{age},性别是{gender}')


user_info1(13, 'lily')
user_info1(13, 'lily', 'Male')


# 4.不定长参数  都是一个组包的过程 （收集零散返回整体）
# 包裹位置传递
def user_info2(*args):
    print(args)


user_info2('Tom')
user_info2('Tom', 'man', 12)


# 包裹关键字传递
def user_info3(**kwargs):
    print(kwargs)


user_info3(name='LIMING', age=18, id=1003)


# 5.拆包和交换变量值
# 1.拆包
# 元组拆包
def return_num():
    return 100, 200


num1, num2 = return_num()
print(num1)
print(num2)
# 字典拆包
dict1 = {'name': 'Tom', 'age': 18}
a, b = dict1
# 对字典拆包，取出来是字典的key
print(a)  # name
print(b)  # age

print(dict1[a])  # Tom
print(dict1[b])  # 18

# 交换变量
a, b = 1, 2
a, b = b, a
print(a, b)

```

```python
# 引用
# 在python中，值是靠引用来传递的
# 我们可以用id()来判断两个变量是否为同一个值得引用。我们可以将id理解为那块内存地址的地址标识
# 1.int类型 不可变类型  修改值后地址会变
a = 1
b = a
print(b)
print(id(a))  # 140734130689696
print(id(b))  # 140734130689696
a = 2
print(b)
print(id(a))  # 140734126823104
print(id(b))  # 140734126823072
# 2.列表 可变数据类型 地址值是一样的
aa = [10, 20]
bb = aa
print(id(aa))  # 1385583825792
print(id(bb))  # 1385583825792

aa.append(30)
print(id(bb))  # 1385583825792

print(id(aa))  # 1385583825792
print(id(bb))  # 1385583825792


# 3.引用当做实参
def test1(a):
    print(a)
    print(id(a))  # 140734130692864

    a += a
    print(a)
    print(id(a))  # 140734130696064


b = 100
test1(b)

c = [11, 22]
test1(c)
# 可变与不可变类型

'''
数据能够直接进行修改，如果能直接修改那么就是可变的，否则就是不可变的
1.可变类型
列表、字典、集合
2.不可变类型
整形、浮点型、字符串、元组
'''
# 四. ⾼高阶函数
'''把函数作为参数传⼊入，这样的函数称为⾼高阶函数，⾼高阶函数是函数式编程的体现。函数式编程就是指这
种⾼高度抽象的编程范式。'''
# 4.1 体验高阶函数
# 需求：⼀一个函数完成计算任意两个数字的绝对值之和。
abs(-10)  # 10
# 在Python中， abs() 函数可以完成对数字求绝对值计算。
round(1.2)  # 1
round(1.9)  # 2


# 方法一
def add_num(a, b):
    return abs(a) + abs(b)


result = add_num(-1, 2)
print(result)


# 方法二 一个函数作为另一个函数的参数出现
def sum_num(a, b, f):
    return f(a) + f(b)


sum = sum_num(-8, 9, abs)
print(sum)
sum1 = sum_num(2.25, 2.15, round)
print(sum1)
# 4.2 内置高阶函数
# 4.2.1 map()
# map(func, lst)，将传⼊入的函数变量func作用到lst变量的每个元素中，并将结果组成新的列表(Python2)/
# 迭代器(Python3)返回。
# 需求：计算 list1 序列中各个数字的2次方。
list1 = [1, 2, 3, 4, 5]


def fun(x):
    return x ** 2


result = map(fun, list1)
print(result)  # <map object at 0x0000027EACC57FD0>
print(list(result))

# 4.2.2 reduce()
# reduce(func(x,y)， lst)，其中func必须有两个参数。每次func计算的结果继续和序列的下一个元素做累积计算。
# 注意： reduce()传⼊入的参数func必须接受2个参数。
# 需求：计算 list1 序列中各个数字的累加和。
import functools

list2 = [1, 2, 3, 4, 5, 6, 7, 8, 9]


def func(a, b):
    return a + b


result = functools.reduce(func, list2)
print(result)
# 4.2.3 filter()
# filter(func, lst)函数用于过滤序列, 过滤掉不不符合条件的元素, 返回⼀一个 filter 对象,。如果要转换为列表,
# 可以使用 list() 来转换。
list3 = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]


def func1(x):
    return x % 2 == 0


result = filter(func1, list3) #<filter object at 0x0000019DC0DF6100>
print(result)
print(list(result))

```

------

```python
# Lambda表达式：如果一个函数有返回值，并且只有一句代码，可以使用lambda简化
# lambda 参数列表：表达式
# lambda表达式的参数可有可无，函数的参数在lambda表达式中完全适用。
# lambda函数能接收任何数量的参数但只能返回一个表达式的值
# 函数
def fn1():
    return 200


print(fn1)  # <function fn1 at 0x00000192762F2EE0>
print(fn1())

# Lambda表达式  匿名函数
fn2 = lambda: 100  # <function <lambda> at 0x00000192762F2F70>
print(fn2)
print(fn2())
# 计算a+b
fn3 = lambda a, b: a + b
print(fn3(2, 3))
print((lambda a, b: a + b)(1, 23))
# Lambda表达式的参数形式
# 1.无参数
print((lambda: 100)())
# 2.一个参数
fn4 = lambda a: a
print(fn4('hello world'))
# 3. 默认参数(缺省参数)
fn5 = lambda a, b, c=100: a + b + c
print(fn5(100, 200))
print(fn5(100, 200, 900))  # 传入数据则修改
# 4.可变参数 *args
fn6 = lambda *args: args
print(fn6(10, 20, 30))  # 元组
# 5.可变参数 **kwargs
fn7 = lambda **kwargs: kwargs
print(fn7(name='python', age=20))  # 字典

# lambda的应用
# 带判断的lambda
fn8 = lambda a, b: a if a > b else b
print(fn8(100, 600))
# 列表数据按字典key的值排序
students = [
    {'name': 'Tom', 'age': 20},
    {'name': 'Rose', 'age': 21},
    {'name': 'Lily', 'age': 26},
    {'name': 'Jack', 'age': 25},
    {'name': 'Wimth', 'age': 24}
]
# 按name值升序排列
students.sort(key=lambda x: x['name'])
print(students)
# 按name值降序排列
students.sort(key=lambda x: x['name'], reverse=True)
print(students)
# 按age值升序排列
students.sort(key=lambda x: x['age'])
print(students)

```

