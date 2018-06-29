# 线程

** 进程默认有主线程（多线程:进程里面创建多个线程） **
进程:正在运行的程序实例(线程的容器)
线程:操作系统调度的单位

- 主线程会等所有子线程结束后退出程序
- 线程调用同一个函数，互不影响
- 线程的执行顺序不确定
- 线程中全局变量是共享的

```python
import threading
import time

def fun():
    print("Hello World")
    time.sleep(1)

for i in range(5):  # for循环创建5个线程
    t = Thread(target=fun)
    t.start()  # 开启线程
# 同时打印5次
```

```python
from threading import Thread
global_num = 0

def add_1():
    global global_num
    for i in range(1000000):
        global_num += 1
    print("add_1global_num:%d"%global_num)

def add_2():
    global global_num
    for i in range(1000000):
        global_num += 1
    print("add_2global_num:%d"%global_num)

t1 = Thread(target=add_1)
t1.start()
t2 = Thread(target=add_2)
t2.start()
print("global_num:%d"global_num)
# 打印的结果远小于2000000(变量共享)
# global_num:347200
# add_1global_num:1065114
# add_2global_num:1194401

```

- 互斥锁
    多线程会抢上锁，一方上锁后，别的就会堵塞，解锁后才能继续

```python
import threading
mutex = threading.Lock()  # 创建锁，默认是开锁的
mutex.acquire([blocking])  # 上锁
mutex.release()  # 释放锁
```

- 死锁
    互相等待

```python
# 添加超时时间
mutex.acquire(2)
# 银行家算法
```

- GIL问题(python多线程并不是真的多线程，当电脑是多cpu时，GIL会控制执行)可以使用c语言来克服GIL问题，部分关键代码用c语言实现，导入使用