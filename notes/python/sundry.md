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

- pycharm破解(deepin)  

 在hosts文件最后一行加上：0.0.0.0 account.jetbrains.com

```bash
sudo vi /etc/hosts
```

- type()测试数据类型，***可用于创建类***

```python
class A(object):
    pass
# 用type创建类(动态创建类)
B = type("B",(),{})  # ()内填继承的类，{}内填属性和方法，以字典
```

- 引用([-5,257)),intern共用机制id()查看地址

```python
# 在[-5,257)之间的整数，申明不同的变量也会指向相同的对象。intern针对不含空格的字符串，共用对象
# id(a)==id(b)
import sys
a = 1
b = 1
# id(a)==id(b)
a = 1
b = a
# 在超过[-5,257),id(a)!=id(b)
a = 1000
b = 1000
# 引用，id(a)==id(b)
a = 1000
b = a
sys.getrefcount(a)  # 查看a被引用的次数
```

- time.tiem() #记录当前时间  1529924632.6713235

## Garbage collection(GC模块垃圾回收)

c,c++使用malloc
申请内存，使用free释放内存，没有垃圾回收机制，Python，Java，c#有自己的垃圾回收机制。  
***Python以引用计数机制为主，隔代回收为辅来实现GC***  
引用计数机制能释放引用数为0的内存，但是对循环引用进行管理，所以使用链表进行隔代回收管理  
GC模块

```python
import gc
gc.disable()  # 关闭gc垃圾回收，默认是打开的
gc.enable()  # 开启gc
gc.isenable()  # 查看是否开启
gc.get_count()  # 获取当前自动执行垃圾回收的计数器，返回一个长度为三的列表
gc.get_threshold()  # 获取gc模块自动执行垃圾回收的频率(固定值(700,10,10))
```

- Tkinter 安装(deepin)
    ```bash
    sudo apt-get install python3-tk
    ```

- Tcp/ip：协议簇(eg:Tcp/ip/udp/arp...),四层模型，七层模型