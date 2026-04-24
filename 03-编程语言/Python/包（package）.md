模块的集合

包的例子（sound是包，formats，effects，filters是子包，`echo.py`，`surround.py`是模块）
```
sound/                          Top-level package
      __init__.py               Initialize the sound package
      formats/                  Subpackage for file format conversions
              __init__.py
              wavread.py
              wavwrite.py
              aiffread.py
              aiffwrite.py
              auread.py
              auwrite.py
              ...
      effects/                  Subpackage for sound effects
              __init__.py
              echo.py
              surround.py
              reverse.py
              ...
      filters/                  Subpackage for filters
              __init__.py
              equalizer.py
              vocoder.py
              karaoke.py
              ...
```

```python
// 从sound包中导入effects子包中的单个模块echo，后续使用模块echo必须用完整名称引用
import sound.effects.echo

// 从sound包中导入effects子包中的单个模块echo，后续使用模块echo不需要包前缀
from sound.effects import echo

// 从包中的模块中直接导入所需的函数或变量，后续使用函数echofilter无需带前缀
from sound.effects.echo import echofilter
```


对于`from package import item`的形式，`item`可以是package的submodule（或subpackage），或者是package中定义的其他名称，如函数、类或变量。import语句首先会检查item是否在package中定义，如果没有，它假设这是一个module并尝试加载，如果找不到，会引发ImportError异常

对于`import item.subitem.subsubitem`的形式，除了最后一个item之外，每个item都必须是一个package，最后一个item可以是module或package，但不能是先前item中定义的类、函数或变量


包下必须要有`__init__.py`文件（除非使用命名空间包，这是一个相对高级的功能），内容可以为空，也可以执行包的初始化代码和设置变量

当导入包时，Python会搜索`sys.path`上的目录，寻找包的子目录


`from package import *` 从包中导入`*`时，可以在包下的`__init__.py`代码中定义一个名为`__all__`的列表来限制被导入的模块名称列表



### 相对导入和绝对导入
绝对导入适用所有情况
相对导入用于包内引用：当包被组织成子包（如示例中的sound包），可以使用相对导入来引用兄弟包的子模块。这些导入使用前导点来指示相对导入中涉及的当前包和父包

假设在`surround`模块中，可能有如下代码：
```python
from . import echo
from .. import formats
from ..filters import equalizer
```

由于主模块没有包，打算用作Python应用程序主模块的模块必须始终使用绝对导入




