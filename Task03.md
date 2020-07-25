```python
# 1.了解异常
# 检测到一个错误，解释器就无法继续执行了，反而出现了一些错误的提示，这就是所谓的异常
# try:
#   可能发生错误的代码
# except:
#   如果出现异常的代码
# 2.捕获异常
try:
    f = open('../test.txt', 'r')  # 读
except:
    f = open('../test.txt', 'w')  # 写
    # 捕获指定异常类型
try:
    print(num)  # 一般try下面只放一条尝试执行的代码
except NameError:
    print('NameError')  # 尝试执行的代码的异常类型要和捕获的异常类型一致
    #捕获多个指定的异常
try:
    print(1/0)
except (NameError,ZeroDivisionError):#用元组放入可能出现的异常
    print('error')
    #捕获异常的描述信息
try:
    print(num)
except (NameError,ZeroDivisionError) as result:
    print(result)
    #捕获所有的异常,Exception 是所有程序异常类的父类
try:
    print(num)
except Exception as result: #直接捕获异常的父类，不需要指定具体的异常
    print(result)

# 3.异常的else 是如果没有异常要执行的代码
try:
    print(1)
except Exception as result:
    print(result)
else:
    print("no error")

# 4.异常的finally  无论是否有异常都要执行的代码，例如关闭文件
try:
    f = open('Test100.txt', 'r')
except Exception as result:
    f = open('Test100.txt', 'w')
else:
    print("No error")
finally:
    f.close()
import time

# 5.异常的传递  从外层try-except传递到内层 try-except
try:
    f = open('test.txt')
    try:
        while True:
            con = f.readline()
            if len(con) == 0:
                break

            time.sleep(3)
            print(con)
    except:
        print("程序异常终止")
except:
    print("该文件不存在！")
# 6.自定义异常
# 在Python 中 抛出异常的语法为 raise 异常类对象
# 自定义异常类，继承Exception
class ShortInputError(Exception):
    def __init__(self, length, min_len):
        self.length = length
        self.min_len = min_len

    # 设置抛出异常的描述信息
    def __str__(self):
        return f'您输入的长度是{self.length},不能少于{self.min_len}个字符'


def main():
    try:
        password = input('请输入密码：')
        if len(password) < 6:
        # 抛出异常
            raise ShortInputError(len(password), 3)
        # 捕获异常
    except Exception as result:
        print(result)
    else:
        print('没有异常，密码输入完成！')


main()


def main():
    try:
        password = input('请输入密码：')
        if len(password) < 6:
        # 抛出异常
            raise ShortInputError(len(password), 3)
        # 捕获异常
    except Exception as result:
        print(result)
    else:
        print('没有异常，密码输入完成！')


main()

```

