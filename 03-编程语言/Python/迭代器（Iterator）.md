

大多数容器对象都可以使用 `for` 语句进行循环
```python
for element in [1, 2, 3]:
    print(element)
for element in (1, 2, 3):
    print(element)
for key in {'one':1, 'two':2}:
    print(key)
for char in "123":
    print(char)
for line in open("myfile.txt"):
    print(line, end='')
```

`for` 语句调用容器对象的 `iter()` 方法
该函数返回一个迭代器对象
该对象定义了 `__next__()` 方法，用于逐个访问容器中的元素
当没有更多元素时， `__next__()` 会引发 `StopIteration` 异常，通知 `for` 循环终止
可以使用 `next()` 内置函数调用 `__next__()` 方法


如何将自己的类改成可迭代的？
必须实现一个__next__()方法
```python
class Reverse:
    """Iterator for looping over a sequence backwards."""
    def __init__(self, data):
        self.data = data
        self.index = len(data)

    def __iter__(self):
        return self

    def __next__(self):
        if self.index == 0:
            raise StopIteration
        self.index = self.index - 1
        return self.data[self.index]
```

