
# Tornado 源码研读

> 大致流程，底层`ioloop`、`iostream`开始，然后`tcp`层`TcpServer`，
然后是`http`层`HttpServer`, 最后是`Web`部分，`RequestHandler`、`Application`、`Template`等

## 核心部分

### 一个大大的`IOLoop`

+ `Configurable`和`IOLoop`的关系


```python
                Configurable
                    ^^
                    ||
                    ||
                  IOLoop
                    ^^
                    ||
                    ||
                PollIOLoop
              ^^    ^^    ^^
             //     ||     \\
            //      ||      \\
           //       ||       \\
          //        ||        \\
  EPollIOLoop  KQueueIOLoop  SelectIOLoop
    (epoll)     (kqueue)        (select)

```

>  `Configurable`通过`__new__`构造函数的方式让子类自定义实例，`__new__`
可以根据需求返回不同的子类实例`（继承object的新式类）`，覆盖重写`configurable_base()`生成直接子类
`configurable_default()`生成具体的子类实例，`initialize()`初始化函数类似`__init__`由子类覆盖实现初始化.
下面是一段模拟IOLoop.instance()运行的`Demo`:

```python
# encoding: utf-8
class Configurable(object):
    """
        模拟Configurable
    """
    def __new__(cls):
        instance = super(Configurable, cls).__new__(EPollIOPloop)
        print('*'*10)
        instance.init()
        print('='*10)
        return instance
    def init(self):
        print('conf ...')

class IOPloop(Configurable):
    def init(self):
        print('IOPloop ...')
    @staticmethod
    def instance():
        return IOPloop()

class PollIOPloop(IOPloop):
    def init(self):
        super(PollIOPloop, self).init()
        print('PollIOPloop ...')

class EPollIOPloop(PollIOPloop):
    def init(self):
        super(EPollIOPloop, self).init()
        print('EPollIOPloop ...')

if __name__ == "__main__":
    demo = IOPloop.instance()
    print(demo.__class__)
    print(demo.__class__.__mro__)

运行结果：
**********
IOPloop ...
PollIOPloop ...
EPollIOPloop ...
==========
<class '__main__.EPollIOPloop'>
(<class '__main__.EPollIOPloop'>, <class '__main__.PollIOPloop'>, <class '__main__.IOPloop'>, <class '__main__.Configurable'>, <type 'object'>)
```


### 协议部分

### Web功能部分

### 其他辅助部分

