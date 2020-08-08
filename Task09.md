# Task09 文件与文件系统

```python
# 文件的基本操作
import time

# 1.1 打开

"""在python，使用open函数，可以打开一个已经存在的文件，或者创建一个新文件，语法如下：
 open(name, mode)
name：是要打开的目标文件名的字符串(可以包含文件所在的具体路径)。
mode：设置打开文件的模式(访问模式)：只读、写入、追加等。"""
f = open('test.txt', 'w')
# 1.2读写
f.write("aaaaa")
# 1.3关闭文件
f.close()
# r  以只读方式打开⽂文件。文件的指针将会放在文件的开头。这是默认模式。不支持写入操作
f = open('test.txt', 'r')

f.close()
# w 打开一个⽂文件只用于写⼊入。如果该文件已存在则打开⽂文件，并从开头开始编辑，即原有内容会被删除。
# 如果该文件不不存在，创建新⽂件。
f = open('1.txt', 'w')
f.write('bbb')
f.close()
# 打开⼀一个⽂文件用于追加。如果该⽂件已存在，文件指针将会放在文件的结尾。也就是说，
# 新的内容将会被写入到已有内容之后。如果该文件不存在，创建新文件进行写⼊。
f = open('2.txt', 'a')
f.write('def')
f.close()
# 访问模式可以省略，如果省略表示访问模式为 r
f = open('1.txt')
f.close()
##########################################################################
# read() 文件内容如果换行，底层有\n，会有字节的占位，导致read书写参数读取出来的参数个数和参数值不匹配
f = open('test.txt', 'r')
print(f.read())
print(f.read(10))
# readlines()可以按照⾏行行的方式把整个文件中的内容进⾏一次性读取，并且返回的是一个列表，其中每⼀行的数据为⼀个元素
f = open("3.txt", 'w')
f.write('hello world\n')
f.write('python\n')
f.write('javaScript\n')
f = open('3.txt', 'r')
con = f.readlines()
print(con)  # ['hello world\n', 'python\n', 'javaScript\n']
f.close()
# readline() 一次读取一行内容
f = open("3.txt", 'w')
f.write('hello world\n')
f.write('python\n')
f.write('javaScript\n')
f = open('3.txt', 'r')
con = f.readline()
print(con) #hello world
f.close()

# r+ 打开⼀个文件⽤于读写。文件指针将会放在文件的开头,文件不存在则报错
# f = open('test3.txt', 'r+') FileNotFoundError: [Errno 2] No such file or directory: 'test3.txt'
f = open('test.txt', 'r+')
con = f.read()
print(con)
f.close()

# w+  打开一个文件用于读写。如果该文件已存在则打开文件，并从开头开始编辑，即原有内容会被删除。
# 如果该⽂文件不不存在，创建新⽂文件。
f = open('test.txt', 'w+')
con = f.read()
print(con)
f.close()

# a+  打开一个文件用于读写。如果该文件已存在，文件指针将会放在文件的结尾。
# 文件打开时会是追加模式。如果该文件不存在，创建新文件用于读写。
f = open('test100.txt', 'a+')
con = f.read()
print(con)
f.close()

# seek() 用来移动文件指针
# 语法：文件对象.seek(偏移量，起始位置 0：文件开头 1：当前位置 2：文件结尾)
f = open('test1.txt', 'r+')
# 改变读取位置数据的开始位置
# f.seek(0, 2) 无数据
con = f.read()
print(con)
f.close()

f = open('test1.txt', 'a+')
# 改变读取位置数据的开始位置
f.seek(0)
con = f.read()
print(con)
f.close()
# 文件备份
# 需求：用户输⼊当前目录下任意文件名，程序完成对该文件的备份功能(备份文件名为xx[备份]后缀，例如： test[备份].txt
# 1. 接收用户输⼊入的文件名
# 2. 规划备份文件名
# 3. 备份文件写入数据

# 1. 接收用户输⼊入的文件名
old_name = input('请输入您要备份的文件名：')
print(old_name)
# print(type(old_name))
# 2. 规划备份文件名
# 2.1 提取目标文件后缀
index = old_name.rfind('.')
if index > 0:
    postfix = old_name[index:]
# print(index)
# 2.2 组织备份的文件名， xx[备份]后缀
# print(old_name[:index]) 文件名
# print(old_name[index:]) 后缀
new_name = old_name[:index] + '[备份]' + postfix
print(new_name)
# 3. 备份文件写入数据
# 3.1 打开源文件 和 备份文件
old_f = open(old_name, 'rb')
new_f = open(new_name, 'wb')

# 3.2 将源文件数据写入备份文件
while True:
    con = old_f.read(1024)
    if len(con) == 0:
        break
    new_f.write(con)
# 3.3 关闭文件
old_f.close()
new_f.close()
# 文件和文件夹的操作
import os

# 1.rename()重命名
# os.rename('1.txt', 'qo.txt')
# 2.remove()删除
# os.remove('sound.mp3[备份].txt')
# 3.mkdir() 创建文件夹
# os.mkdir('Day08')
# 4.rmdir() 删除文件夹
# os.rmdir('Day08')
# 5.getcwd() 返回当前文件所在的文件路径
print(os.getcwd())
# 6.chdir() 改变默认目录
# os.mkdir('aa') 在aa里面创建bb
# os.chdir('aa')
# os.mkdir('bb')
# 7.listdir() :获取某个文件夹下所有的文件，返回一个列表
print(os.listdir())

"""需求：批量修改文件名，既可添加指定字符串，又能删除指定字符串。
步骤
1. 设置添加删除字符串的的标识
2. 获取指定目录的所有文件
3. 将原有文件名添加/删除指定字符串，构造新名字
4. os.rename()重命名
"""
flag = 2
file_list = os.listdir()
print(file_list)

for i in file_list:
    if flag == 1:
        new_name = 'Python_' + i
    elif flag == 2:
        num = len('Python_')
        new_name = i[num:]
    os.rename(i, new_name)

```

