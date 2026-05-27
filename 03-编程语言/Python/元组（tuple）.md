

### namedtuple
```python
from collections import namedtuple

User = namedtuple("User", ["name", "age"])

u = User("Jason", 18)
print(u.name)  
print(u.age)
```
