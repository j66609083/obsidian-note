
创建迭代器的工具

每当需要返回数据时，会使用 `yield`语句。
每次调用 `next()`时，生成器会从上次停止的地方继续执行（它记得所有数据值和最后执行的语句）
```python
def reverse(data):
    for index in range(len(data)-1, -1, -1):
        yield data[index]
```


任何可以用生成器完成的事情，也可以用基于类的迭代器来完成
生成器之所以如此简洁，是因为 `__iter__()` 和 `__next__()` 方法会自动创建
除了自动创建方法和保存程序状态外，当生成器终止时，它们会自动引发 `StopIteration` 。结合这些特性，可以毫不费力地创建迭代器，就像编写普通函数一样。

### 生成器表达式
一些简单的生成器可以用类似列表推导式的语法，但用圆括号代替方括号来简洁地编写。这些表达式是为生成器在包含函数中立即使用的情况设计的。生成器表达式比完整的生成器定义更紧凑，但功能较少，而且通常比等价的列表推导式更节省内存。
```python
>>> sum(i*i for i in range(10))                 # sum of squares
285

>>> xvec = [10, 20, 30]
>>> yvec = [7, 5, 3]
>>> sum(x*y for x,y in zip(xvec, yvec))         # dot product
260

>>> unique_words = set(word for line in page  for word in line.split())

>>> valedictorian = max((student.gpa, student.name) for student in graduates)

>>> data = 'golf'
>>> list(data[i] for i in range(len(data)-1, -1, -1))
['f', 'l', 'o', 'g']
```

