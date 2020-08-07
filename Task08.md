# Task08  模块与datetime模块

```python
# 方法一
# import Day10.module1
#
# Day10.module1.info_print1()

# 方法二
# from 包名 import *
# 模块名.目标
# 注意：必须在 __init__.py 文件中添加 __all__ = [] ，控制允许导⼊的模块列表。
from Day10 import *

module1.info_print1()
module2.info_print2()

# 如果一个模块文件中有 __all__ 变量，当使用 from xxx import * 导⼊时，只能导⼊这个列表中的元素。
# 包将有联系的模块组织在一起，即放到同一个文件夹下，并且在这个文件夹创建⼀一个名字为 __init__.py 文件，
# 那么这个文件夹就称之为包。

__all__=['module1','module2']
# 需求：math模块下的sqrt()开平方计算
# 方法一
import math

print(math.sqrt(9))  # 3.0  除法运算返回浮点数
# 方法二
from math import sqrt

# 直接功能调用
print(sqrt(16))
# 方法三
from math import *

print(sin(57.3))
# as定义别名  定义了别名只用别名了，不能再用模块名
import time as tt

tt.sleep(2)
print('hello')

from time import sleep as s1

s1(3)
print('hello word')
# 1.3. 模块定位顺序
'''当导⼊入⼀一个模块， Python解析器器对模块位置的搜索顺序是：
1. 当前目录
2. 如果不在当前目录， Python则搜索在shell变量PYTHONPATH下的每个目录。
3. 如果都找不到， Python会察看默认路径。 UNIX下，默认路径⼀一般为/usr/local/lib/python/

模块搜索路径存储在system模块的sys.path变量中。变量⾥里包含当前⽬目录， PYTHONPATH和由安装过
程决定的默认目录。
注意:
自己的文件名不要和已有模块名重复，否则导致模块功能无法使用
使用from 模块名 import 功能 的时候，如果功能名字重复，调用到的是最后定义或导⼊入的功能。 '''
# import my_module1
from Day09.my_module1 import *



# my_module1.testA(2, 3)
# 如果使用 from .. import .. 或 from .. import * 导⼊多个模块的时候，且模块内有同名功能。
# 当调用这个同名功能的时候，调用到的是后面导⼊的模块的功能。
testB(1,2)
```

