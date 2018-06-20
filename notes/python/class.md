# class的相关笔记

- 给class添加属性  

```python
class A(object):
    def __init__(self,age,name):
        self.age = age
        self.name = name
a = A()
# 给 a 添加属性
a.addr = "江西"
```

- 给class添加方法

```python
import types
class A(object):
    def __init__(self,age,name):
        self.age = age
        self.name = name
    def display(self):
        print("display:{}".format(self.name))
def fun(xx):
    print("fun:{}".format(xx))
a = A()
# 将fun方法添加到类a中,如果是不带参数的方法可以直接使用下面的语句添加。本例中fun含有参数
# a.addfun = fun
# 将fun方法添加到a.addfun
a.addfun = type.MethodType(fun,a)
```

- slots 限制class添加属性

```python
class A(object):
# A将不能添加("name","age")以外的其他属性
    __slots__ = ("name","age")
```

## 内建属性

| 常用专有属性 | 说明 | 触发方法 |
| - | :-: | -: |
| `__init__` | 初始化构造函数 | 创建实例时，在`__new__`后 |
| `__new__` | 生成实例所需的属性 | 创建实例时 |
| `__class__` | 实例所在的类 | 实例`.__class__` |
| `__str__` | 实例字符串表示，可读性 | print(类实例)，如没实现将调用repr结果 |
| `__repr__` | 实例字符串表示，可读性 | 类实例 |
| `__del__` | 析构 | 删除实例 |
| `__dict__` | 实例自定义属性 | vars(实例`.__dict__`) |
| `__doc__` | 类文档，子类不能继承 |  |
| `__getattribute__` | 属性访问拦截器 | 访问实例属性时 |
| `__bases__` | 类的所有父类构成元素 | 类名`.__bases__` |
|

- class的__call__方法：

```python
class Test(object):
    def __call__(self):
        print("Function:call")
T = Test()
# 直接调用T对象，将会调用类里面的__call__方法
T()
```

- __str__方法(魔方函数)

```python
class A(object)：
    def __str__(self):
    return ""
a = A()
print(a)  # print(class对象)打印 srt 函数的返回值
```