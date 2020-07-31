# Task05 字典、集合和序列

```python

# 字典里面的数据是以键值对的形式出现的 ，各个键值对之间用逗号隔开
# 1.{'':'','':''.....} 有数据的字典
dict1 = {'name': 'TOM', 'age': '12', 'gender': '男'}
print(dict1)  # {'name': 'TOM', 'age': '12', 'gender': '男'}
print(type(dict1))  # <class 'dict'>

# 2.创建空字典
dict2 = {}
print(type(dict2))  # <class 'dict'>
dict3 = dict()
print(dict3)  # {}
# 3.字典新增数据
dict1['id'] = 1102
print(dict1)  # 新增
dict1['name'] = 'rose'
print(dict1)  # name已存在 则修改
# 4.字典删除数据
dict4 = {'name': 'TOM', 'age': '12', 'gender': '男'}
del dict4['name']  # 删除的是键值对
print(dict4)
dict4.clear()  # 清空字典
print(dict4)
# 5.字典修改数据 若不存在键值对 则新增
dict5 = {'name': 'Lily', 'age': '12', 'gender': '男'}
print(dict5)  # 修改
dict5['id'] = 1102
print(dict5)  # 新增键值对
# 6.字典数据的查找
dict6 = {'name': 'TOM', 'age': '12', 'gender': '男'}
# [key]
print(dict6['name'])  # TOM
# print(dict6['id'])  # keys error 不存在则报错
# 函数写法
# get()
print(dict6.get('name'))  # TOM
print(dict6.get('id', 110))  # 110
print(dict6.get('id'))  # None
# key() 查找所有的key 返回可迭代的对象
print(dict6.keys())  # dict_keys(['name', 'age', 'gender'])
# values() 查找所有的value 返回可迭代的对象
print(dict6.values())  # dict_values(['TOM', '12', '男'])
# items() 查找所有的键值对 返回可迭代的对象 以元组的形式
print(dict6.items())  # dict_items([('name', 'TOM'), ('age', '12'), ('gender', '男')])
# 7.字典数据的遍历
dict7 = {'name': 'TOM', 'age': '12', 'gender': '男'}
# 遍历字典的key
for key in dict7.keys():
    print(key)
# 遍历字典的value
for value in dict7.values():
    print(value)
# 遍历字典的元素
for item in dict7.items():
    print(item)
# 遍历字典的键值对（拆包）
for key, value in dict7.items():
    print(f'{key}={value}')

```

```python
# 1.创建有数据的集合 集合有去重功能
# 使用{}
s1 = {10, 10, 10, 20, 30, 50, 40}
print(s1)
# 使用set()
s3 = set('abcdefg')
print(s3)
# 创建空集合，只能用set()
s4 = set()
print(type(s4))
s5 = {}
print(type(s5))  # <class 'dict'>
# 2.常见的集合操作
s1 = {10, 10, 10, 20, 30, 50, 40}
# add() ： 增加单一数据，若增加已有数据，则什么都不做
s1.add(100)
print(s1)

# update() ：增加的数据是序列
s1.update([60, 70])
print(s1)

# 删除数据：
# remove() : 如果数据不存在则报错
s6 = {10, 10, 10, 20, 30, 50, 40}
s6.remove(20)
print(s6)
# s6.remove(20)#报错
# discard(): 如果数据不存在也不报错
s6.discard(10)
print(s6)
# pop():随机删除集合中的某个数据，并返回这个数据
del_num = s6.pop()
print(del_num)

# 查找数据
s11 = {10, 20, 30, 40, 50, 60}
# in 或not in 判断数据是否在集合序列
print(10 in s11)
print(10 not in s11)

```

