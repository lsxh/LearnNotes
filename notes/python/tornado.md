# tornado

## 引入模块  

```python
import tornado.web  # tornado 基础web框架  
import tornado.ioloop  # tornado核心I/O循环模块，封装了Linux的epoll，BSD的kqueue,是tornado高效的基础  
import tornado.httpserver  # 创建服务器对象
```

## 函数

- listen()  
  app.listen(port)  # 只能在单进程中使用
  多进程使用 bind(port)

## 多进程

- 不建议使用下面的方式启动多进程，而是手动启动多进程，并可以绑定不同的端口。  

```python
app = tornado.web.Application([
        (r"/", IndexHandler)
    ])
    # tornado 默认启动单进程
    httpServer = tornado.httpserver.HTTPServer(app)  # 创建服务器对象
    # httpServer.listen(8000)
    # 多进程不能使用listen，使用bind()
    httpServer.bind(8000)
    httpServer.start(5)  # 默认开启一个进程。若为None或负数，开启对应硬件机器的CPU核心个进程
    tornado.ioloop.IOLoop.current().start()
```

