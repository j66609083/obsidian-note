

```python
d = {"a":1 , "b": 2}  
print(d.get("a"))  
print(d["a"])  

# key不存在返回None或默认值
print(d.get("c"))  # 正常执行，输出None

# key不存在会抛KeyError
print(d["c"]) # 报KeyError异常
```


### 删除
```python
del d["a"]
value = d.pop("b")
item = d.popitem() # 删除并返回最后插入的一对键值
```

copy() 浅拷贝
deepcopy() 深拷贝



### 解包（dict unpacking）
```python
a = {  
"name": "Jason",  
"age": 18  
}  
  
# 把 a 这个 dict 里的所有键值对展开到新 dict 里，属于浅拷贝
b = {  
**a  
}  
  
print(b)
```