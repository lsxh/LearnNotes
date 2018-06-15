# 杂项

- Python可以直接对函数换名

```python
def fun():
    print('this is funnction')
    return
a=fun
a()  # 等价与 fun()
```

- 如果函数重名编译不报错，调用默认执行最后一次申明时的内容(要避免函数重名问题)  
- 在不引入其他变量的情况下，交换两个变量的值  

```python
# 只有Python可以
a,b = b,a
```

适合所以语言  

`
a = a+b;
b = a-b;
a = a-b;
`
