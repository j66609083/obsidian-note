
区分2个概念：
1. 可迭代对象：能被 `for` 遍历的对象，叫**可迭代对象**。必须实现`__iter__`方法
2. 迭代器：可以不断调用 `next()` 取值的对象。必须实现`__iter__`方法和`__next__`方法

```python

# nums是可迭代对象
nums = [1, 2, 3]

# it是迭代器
it = iter(nums)

print(next(it))  # 1
print(next(it))  # 2
print(next(it))  # 3
print(next(it))  # StopIteration
```


### 迭代器协议由两个方法组成
```python
__iter__()
__next__()
```


iter()：从一个可迭代对象中拿到迭代器
```python
nums = [1, 2, 3]

# 以下2种写法效果一样
it = iter(nums)
it = nums.__iter__()
```

next()：从迭代器中取下一个元素
```python
it = iter([1, 2, 3])

# 以下2种写法效果一样
print(next(it))
it.__next__()
```

在python中，`for` 循环本质就是不断调用 `iter()` 和 `next()`




生成器是迭代器的一种
```python
def gen():
    yield 1
    yield 2

# g是生成器，也是迭代器
g = gen()
```
可以通过以下代码证明：
```python
def gen():
    yield 1
    yield 2

g = gen()

print(hasattr(g, "__iter__"))   # True
print(hasattr(g, "__next__"))   # True
print(iter(g) is g)             # True
```



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

