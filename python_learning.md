# 标题
### collections中defaultdict：一种内置字典子类
```python
from collections improt defaultdict
# 使用list作为default_factory
d = defaultdict(list)

# 当key不存在时，defaultdict会自动为这个key创建一个新的空列表
d['a'].append(1)
d['a'].append(2)
d['b'].append(3)

print(d)  # 输出：defaultdict(<class 'list'>, {'a': [1, 2], 'b': [3]})

# 使用int作为default_factory
d = defaultdict(int)

# 当key不存在时，defaultdict会自动为这个key创建一个新的实例
d['a'] = 1
d['b'] = 3

print(d)  # 输出：defaultdict(<class 'int'>, {'a': 1, 'b': 3})
```
### set()函数的用法：创建一个无序但不含重复元素的集合
```python
# 创建一个空的集合
s = set()
print(s)  # 输出：set()

# 从列表创建集合，自动去除重复元素
s = set([1, 2, 3, 2, 1])
print(s)  # 输出：{1, 2, 3}

# 从字符串创建集合，自动去除重复字符
s = set('hello')
print(s)  # 输出：{'e', 'h', 'l', 'o'}
```
set()对象中的元素是可哈希的，可以在O（1）的时间复杂度进行增删查改


为了交到github上改点东西
