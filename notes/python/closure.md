# 闭包、装饰器

## 闭包

***函数中定义新的函数，并且定义的函数使用了外面函数的参数***

```python
def fun(num):
    print("fun")
    def fun_in(num):
        print(num+1)
    return fun_in
```

```python
# 定义直线ax+b
def line(a,b):
    def fun(x):
        print(a*x+b)
    return fun
# 调用
line1 = line(1,2) # line1相当于fun
# 直接多次调用
line1(2) # 结果1x2+2
line1(3) # 结果1x3+2
```

## 装饰器

***在不改变原来函数的条件下，增加函数的功能***

```python
# 原函数f1(),f2()。现增加功能调用前先验证
def f1():
    print("f1函数")
def f2():
    print("f2函数")

# 增加功能(使用闭包)
def w(func):
    def inner():
        if True:
            func()  # 调用函数
        else:
            pass
    return inner
# 调用原函数
f1 = w(f1)
f2 = w(f2)
f1()
f2()
# 函数f1,f2不发生改变，调用方式也不变，但函数功能增加
```

代码等价与(@语法糖)  
*当代码解释器运行到有装饰器的地方，解释器就开始装饰，而不是等调用的时候在进行装饰。若有多个装饰器，先执行内层的装饰*

```python
# 原函数f1(),f2()。现增加功能调用前先验证
@w
def f1():
    print("f1函数")
@w
def f2():
    print("f2函数")

# 增加功能(使用闭包)
def w(func):
    def inner():
        print("此处验证")
        if True:
            func()  # 调用函数
        else:
            pass
    return inner
# 调用原函数
f1()
f2()
# 函数f1,f2不发生改变，调用方式也不变，但函数功能增加
```

### 类装饰器

```python
class A(object):
    pass
# class 装饰器
@A
def fun():
    pass
```