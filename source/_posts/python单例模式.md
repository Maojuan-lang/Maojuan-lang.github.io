---
title: python单例模式
date: 2024-08-17
---

```
1. 使用类的__new__方法
__new__ 是类的构造方法，负责创建实例。你可以通过重写这个方法来确保一个类只能有一个实例。

class Singleton:
    _instance = None  # 用于存储类的唯一实例

    def __new__(cls, *args, **kwargs):
        if cls._instance is None:
            cls._instance = super().__new__(cls)
        return cls._instance

# 测试
singleton1 = Singleton()
singleton2 = Singleton()

print(singleton1 is singleton2)  # 输出 True，表明两个对象是同一个实例
```

```
2. 使用装饰器实现单例
装饰器可以将单例逻辑封装起来，使得实现单例的方式更加灵活和简洁。

def singleton(cls):
    instances = {}

    def get_instance(*args, **kwargs):
        if cls not in instances:
            instances[cls] = cls(*args, **kwargs)
        return instances[cls]

    return get_instance

@singleton
class Singleton:
    def __init__(self):
        self.value = 42

# 测试
singleton1 = Singleton()
singleton2 = Singleton()

print(singleton1 is singleton2)  # 输出 True，表明两个对象是同一个实例
```

```
3. 使用元类实现单例
元类控制类的创建过程。通过重写元类的 __call__ 方法，我们可以确保类只实例化一次。

class SingletonMeta(type):
    _instances = {}

    def __call__(cls, *args, **kwargs):
        if cls not in cls._instances:
            instance = super().__call__(*args, **kwargs)
            cls._instances[cls] = instance
        return cls._instances[cls]

class Singleton(metaclass=SingletonMeta):
    def __init__(self):
        self.value = 42

# 测试
singleton1 = Singleton()
singleton2 = Singleton()

print(singleton1 is singleton2)  # 输出 True，表明两个对象是同一个实例
```

