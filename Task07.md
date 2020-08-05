# Task07  类、对象和魔法方法

```python
# 面向对象实现方法
"""
class 类名()：
"""


class Washer():
    def wash(self):  # 打印对象和self得到的结果是⼀一致的，所以self 指的是调用该函数的对象
        print('洗衣服')
        # print(self)

    def print_info(self):
        print(f'洗衣机的宽度是{self.width}')
        print(f'洗衣机的高度是{self.height}')


# 创建对象
# 对象名=类名
haier = Washer()
print(haier)  # q<__main__.Washer object at 0x0000019117197400>
# 调用实例方法
haier.wash()  # <__main__.Washer object at 0x000002A760DF5580> #洗衣服
haier1 = Washer()
haier1.wash()  # <__main__.Washer object at 0x000001F49DC85B50>
# 添加和获取对象属性
# 对象属性既可以在类外面添加和获取，也能在类里面添加和获取。
# 类对象外面添加属性
haier1.width = 200
haier1.height = 500
# 类外面获取对象属性    对象名.属性名
# print(f'洗衣机的宽度是{haier1.width}')
# print(f'洗衣机的高度是{haier1.height}')
# 类里面获取对象属性
haier1.print_info()
# 类方法
"""类方法特点
第一个形参是类对象的方法
需要用装饰器 @classmethod 来标识其为类方法，对于类方法， 第一个参数必须是类对象，一般以cls 作为第一个参数。"""


# 当方法中 需要使用类对象 (如访问私有类属性等)时，定义类方法,类方法一般和类属性配合使用

class Dog(object):
    __tooth = 10

    @classmethod
    def get_tooth(cls):  # 获取类属性的值
        return cls.__tooth


wangcai = Dog()
result = wangcai.get_tooth()
print(result)

# 4.2 静态方法
"""静态方法特点
需要通过装饰器 @staticmethod 来进行修饰， 静态方法既不需要传递类对象也不需要传递实例对象（形参没有self/cls） 。
静态方法也能够通过实例对象和类对象去访问。
 静态方法使用场景
当方法中 既不需要使用实例对象(如实例对象，实例属性)， 也不需要使用类对象 (如类属性、类⽅法、创建实例等)时，
定义静态方法取消不需要的参数传递，有利于减少不必要的内存占用和性能消耗"""


class Dog1(object):
    @staticmethod
    def info_print():
        print('这是一个静态方法')


wangcai = Dog1()
# 静态方法既可以使用对象访问又可以使用类访问
wangcai.info_print()
Dog1.info_print()

# 类属性
# 1.设置和访问类属性
# 类属性就是 类对象 所拥有的属性，它被 该类的所有实例对象 所共有。
# 类属性可以使用 类对象 或 实例对象 访问。


class Dog(object):
    tooth = 10


wangcai = Dog()
xiaohei = Dog()

print(Dog.tooth)
print(wangcai.tooth)
print(xiaohei.tooth)

"""类属性的优点
类的实例记录的某项数据 始终保持一致时，则定义类属性。
实例属性要求每个对象为其单独开辟一份内存空间来记录数据，而类属性为全类所共有，仅占用一份内存，更加节省内存空间。
"""
# 2.修改类属性
# 类属性只能通过类对象修改，不能通过实例对象修改，如果通过实例对象修改类属性，表示的是创建了一个实例属性。
# 通过类去修改
Dog.tooth = 12
print(Dog.tooth)
print(wangcai.tooth)
print(xiaohei.tooth)
# 不能通过对象修改属性，如果这样操作，实则是创建了一个实例属性
xiaohei.tooth = 20
print(Dog.tooth)  # 12
print(wangcai.tooth)  # 12
print(xiaohei.tooth)  # 20


# 实例属性
class Dog(object):
    def __init__(self):
        self.age = 5

    def info_print(self):
        print(self.age)


wangcai = Dog()
print(wangcai.age)  # 5
print(Dog.age)  # 报错：实例属性不能通过类访问 type object 'Dog' has no attribute 'age'
wangcai.info_print()  # 5

```

```python
# 在Python中， __xx__() 的函数叫做魔法方法，指的是具有特殊功能的函数。
# __init__() 方法的作用：初始化对象。
class Washer():
    def __init__(self):
        # 添加实例属性
        self.width = 500
        self.height = 200

    def print_info(self):
        print(f'洗衣机的宽度是{self.width}')
        print(f'洗衣机的高度是{self.height}')


haier = Washer()
# haier.print_info()
"""
注意：
__init__() 方法，在创建一个对象时默认被调用，不需要手动调用
__init__(self) 中的self参数，不需要开发者传递， python解释器会自动把当前的对象引用传递过去
"""


# 带参数的__init__()
class Washer1():
    def __init__(self, width, height):
        self.width = width
        self.height = height

    def print_info1(self):
        print(f'洗衣机的宽度是{self.width}')
        print(f'洗衣机的高度是{self.height}')


haier1 = Washer1(10, 20)


# haier1.print_info1()


# __str__()
# 当使用print输出对象的时候，默认打印对象的内存地址。如果类定义了 __str__ ⽅法，
# 那么就会打印从在这个方法中 return 的数据。
class Washer2():
    def __init__(self, width, height):
        self.width = width
        self.height = height

    def __str__(self):
        return '解释说明：类的说明或者对象的说明'


haier2 = Washer2(20, 30)


# print(haier2)


# __del__()
# 当删除对象时， python解释器也会默认调用 __del__() 方法
class Washer3():
    def __init__(self, width, height):
        self.width = width
        self.height = height

    def __str__(self):
        return '解释说明：类的说明或者对象的说明'

    def __del__(self):
        print(f'{self}对象已经删除')


haier3 = Washer3(20, 30)
# print(haier3)
del haier3  # <__main__.Washer3 object at 0x00000192ABD492E0>对象已经删除

```

