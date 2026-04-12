> A module is a file containing Python definitions and statements（模块是一个包含Python定义和语句的文件）


模块名称：
1. 普通模块的模块名是文件名
2. 主模块的模块名是固定的`__main__`
3. 将模块作为脚本执行时会变成主模块
4. 主模块一般会添加以下类似代码：
```python
if __name__ == "__main__":
    import sys
    fib(int(sys.argv[1]))
```


导入是指导入到当前命名空间

- 导入模块名称
```python
import fibo
# 模块名称别名
import fibo as fib
```
这种方式要使用模块里的函数或者属性，还是得使用`modName.funcName`的形式

- 导入模块中的名称
```python
# 导入模块中的部分名称
from fibo import fib, fib2
# 导入模块中的所有名称，除了下划线开头的名称。不推荐
from fibo import *
# 导入模块中的名称的别名
from fibo import fib as fibonacci
```
这种方式不会同时导入模块名称


- 运行时重新加载模块（交互式测试模块）
适用于测试一个模块的场景（或者模块不多）
```python
import importlib;
importlib.reload(modulename);	  
```


模块搜索路径：
1. 先查内建模块（built-in module）
	- 内建模块的模块名存储在`sys.builtin_module_names`
2. 


`builtins`
`__main__`

