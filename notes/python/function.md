# 函数笔记

## function

### map()函数

```python
# map(fun,iterable)
map(lambda x,y: x+y,[1,2,3],[4,5,6])  # 结果[5,7,9]可迭代对象
```

### filter()过滤函数

```python
# 只将结果为true的值以对象返回。0=>false,!0=>true
# filter(fun,iterable)
filter(lambda x,y: x+y,[1,2,3],[4,5,6])
filter(None,'abc')  # 使用None不过滤
```

### reduce()函数

```python
#reduce()会对参数中的元素进行积累
reduce(lambda x,y: x+y,[1,2,3,4])  # 结果：10
reduce(lambda x,y: x+y,[1,2,3,4],5)  #结果：15
reduce(lambda x,y: x+y,['a','b','c'],'d')  # 结果：'dabc',(d=>x,['a','b','c']依次=>y)
```

### sort()函数(排序)、sorted()函数

```python
a = [1,5,3,9]
a.sort()  #从小到大排序
a.sort(reverse=True)  # 从大到小排序
sorted([1,53,2])  # sorted排序
```

## functiontools(常用模块，管理工具)

''''''

### count() 统计字符串某个字符出现的次数

```python
str.count(sub, start= 0,end=len(string))
# sub 搜索的子字符串
# start 字符串开始搜索的位置，默认为0
# end 结束搜索的位置，默认len(str)
'abc'.count('ab')  # 1
```