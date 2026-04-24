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
2. 再查`sys.path`定义的路径
	- 当前目录（当没有指定python脚本时）
	- python脚本所在的目录
	- [`PYTHONPATH`](https://docs.python.org/3/using/cmdline.html#envvar-PYTHONPATH)环境变量，和`PATH`环境变量配置格式差不多
	- 依赖于安装的默认值（按惯例包含`site-packages`目录，由site模块处理）
- 


`builtins`
`__main__`



Python 将每个模块的编译版本缓存到 `__pycache__` 目录下，文件名为 `module._version_.pyc` ，其中版本号编码了编译文件的格式；它通常包含 Python 版本号。这种命名约定允许来自不同版本和不同 Python 版本的编译模块共存。

Python 在两种情况下不会检查缓存。首先，它总是重新编译直接从命令行加载的模块，并且不存储结果。其次，如果没有源模块，它也不会检查缓存。为了支持非源（仅编译）的发行版，编译后的模块必须位于源目录中，并且不能存在源模块。

一个程序从 `.pyc` 文件读取和从 `.py` 文件读取运行速度是一样的； `.pyc` 文件唯一更快的地方是加载的速度。