


[TOC]
## python
### nonlocal和global
一个用于可以修改嵌套函数中外部函数的变量，另一个可以用来修改全局变量
```python
def outer():
    x = 1
    def inner():
        nonlocal x
        x = 2
    inner()
    print(x)  # 输出：2
outer()
```
### map()函数
第一个参数接受一个函数名，后面的参数接受一个或多个可迭代的序列，返回的是一个集合。

把函数依次作用在list中的每一个元素上，得到一个新的list并返回。注意，map不改变原list，而是返回一个新list。
```python
map(function,iterable,...)
```
```python
del square(x):
    return x ** 2
 
map(square,[1,2,3,4,5])
# 结果如下:
[1,4,9,16,25]

map(lambda x, y: x+y,[1,3,5,7,9],[2,4,6,8,10])
# 结果如下：
[3,7,11,15,19]

map(lambdax, y : (x**y,x+y),[2,4,6],[3,2,1])
# 结果如下
[(8,5),(16,6),(6,7)]
```
当不传入function时，map()就等同于zip()，将多个列表相同位置的元素归并到一个元组：
```python
map(None,[2,4,6],[3,2,1])
# 结果如下
[(2,3),(4,2),(6,1)]
```
通过map还可以实现类型转换
将元组、字符串转换为list：
```python
map(int,(1,2,3))
# 结果如下：
[1,2,3]
```
### lambda函数
lambda函数与def函数的区别

1.lambda可以立即传递（无需变量），自行返回结果

2.lambda在内部只能包含一行代码

3.lambda是一个为编写简单函数而设计的，而def用来处理更大的任务

4.lambda可以定义一个匿名函数，而def定义的函数必须有一个名字

lambda函数的优势：

1.对于单行函数，使用lambda表达式可以省去定义函数的过程，让代码更加简洁

2.对于不需要多次复用的函数，用lambda表达式可以在用完后立即释放，提高程序执行的性能。
```python
# def函数写法
def add(a, b):
    return a + b
 
print(add(10, 20))
print("-" * 50)
 
# lambda函数写法
add_lambda = lambda a, b: a + b
print(add_lambda(10, 20))

# 使用if判断奇偶性
def get_odd_even(x):
    if x % 2 == 0:
        return "偶数"
    else:
        return "奇数"
 
print(get_odd_even(10))
 
# lambda函数写法
get_odd_even1 = lambda x: "偶数" if x % 2 == 0 else "奇数"
print(get_odd_even1(10))
```
使用lambda函数对按列表的第二个元素进行排序
```python
a = [[1, 2], [2, 4], [1, 3], [3, 4]]
a.sort(key=lambda x: x[1])
print(a) # [[1, 2], [1, 3], [2, 4], [3, 4]]
```
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
### collections.deque()
创建双端队列
```python
from collections import deque

d = deque()

# 在右侧添加元素
d.append('a')
d.append('b')
print(d)  # 输出：deque(['a', 'b'])

# 在左侧添加元素
d.appendleft('c')
print(d)  # 输出：deque(['c', 'a', 'b'])

# 从右侧删除元素
right = d.pop()
print(right)  # 输出：'b'
print(d)  # 输出：deque(['c', 'a'])

# 从左侧删除元素
left = d.popleft()
print(left)  # 输出：'c'
print(d)  # 输出：deque(['a'])
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

set()中增加元素
```python
s = set()
s.add(1)
print(s) # {2}
```
### .lower()将字符串中的大写字符转换为小写
.upper()将小写转为大写
```python
s = "Hello, World!"
lower_s = s.lower()
print(lower_s)  # 输出：'hello, world!'
```
### 正则表达式
.replace()字符串替换
re.sub()字符串替换
```python
import re

s = "Hello, World!"

# 使用 re.sub 替换所有的大写字母
s1 = re.sub(r"[A-Z]", "*", s) # 用*替换所有的大写字母
print(s1)  # 输出：'*ello, *orld!'

# 使用 .replace 替换 "Hello"
s2 = s.replace("Hello", "Hi")
print(s2)  # 输出：'Hi, World!'
```
使用re.findall()来匹配字符
```python
import re

s = "Hello, I am 25 years old and I live in number 123 street."
numbers = re.findall(r'\d+', s)
print(numbers)  # 输出：['25', '123']
```
### python中字典的一些操作
删除操作：.pop()和del
```python
a = {}
a["fasd"] = 1
a["dsfa d"] = 2
print(a)
#{'fasd': 1, 'dsfa d': 2}
del a["fasd"]
a.pop("dsfa d")
print(a)
#{}
```
使用len(),key(),value(),items()分别返回字典长度、键列表、值列表、键值对元组
```python
a = {}
a["fasd"] = 1
a["dsfa d"] = 2
for key in a.keys():
    print(key)
# fasd dsfa d
```
添加键值对，若该键存在则将值加一，常用于统计
get(key, 0)的作用是返回该键对应的值，若没有该键则返回零
```python
dict = {}
dict["new_key"] = dict.get(new_key, 0) + 1
```
collections.Counter()用法，输入一个列表，输出字典，值为键数字出现的次数
```python
import collections
nums = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 1, 2, 3, 4, 5]
nums = collections.Counter(nums)
print(nums)#Counter({1: 2, 2: 2, 3: 2, 4: 2, 5: 2, 6: 1, 7: 1, 8: 1, 9: 1, 10: 1})
```
### 将整数转为二进制
```python
num = 10
binary_str = bin(num)
print(binary_str)  # 输出：'0b1010'

num = 10
binary_str = bin(num)[2:]
print(binary_str)  # 输出：'1010'
```
### python向上取整
python默认无法整除时向下取整，使用math.ceil可以向上取整
```python
import math
print(int(1.6)) # 1
print(int(1.4)) # 1
print(math.ceil(4.2))  # 输出：5
print(math.ceil(-4.2))  # 输出：-4
```

### 列表与字符串的继承
python中列表是可变的，简单将列表复制，在对列表进行改动的时候，复制的列表内容也会随之改动
```python
a = [1, 2, 3]
b = a
b[2] = 4
print(a) # [1, 2, 4]
```
可以使用copy
```python
from copy import copy
a = [1, 2, 3]
b = copy(a)
b[2] = 4
print(a)# [1, 2, 3]
```
或者内置的list()函数
```python
a = [1, 2, 3]
b = list(a)
b[2] = 4
print(a)# [1, 2, 3]
```
而字符串属于不可变类型，可以直接复制
### 反向遍历一个数组
reverse()
```python
for i in reversed(range(1, 3)):
    print(i)#2,1
```
### 迭代器与生成器
在Python中，迭代器是一个可以记住遍历的位置的对象。迭代器对象从集合的第一个元素开始访问，直到所有的元素被访问完结束。迭代器只能往前不会后退。

在Python中，生成器是一种特殊的迭代器，它的特点是可以在运行时生成值，而不是一次性生成所有值并保存在内存中。这使得生成器在处理大规模数据时非常高效。
```python
def fibonacci():
    a, b = 0, 1
    while True:
        yield a
        a, b = b, a + b

gen = fibonacci()
for i in gen:
    if i > 1000:
        break
    print(i, end=' ')# 0 1 1 2 3 5 8 13 21 34 55 89 144 233 377 610 987 
```
## 数据结构及算法
### 栈(stack)和队列(queue)
栈：后进先出
队列：先进先出
```python
# 栈
stack = []
stack.append('a')  # push 'a'
stack.append('b')  # push 'b'
print(stack.pop())  # pop and print 'b'

# 队列
from collections import deque
queue = deque()
queue.append('a')  # enqueue 'a'
queue.append('b')  # enqueue 'b'
print(queue.popleft())  # dequeue and print 'a'
```
### 异或（^）操作
异或是一种二进制的位运算，符号以 XOR 或 ^ 表示。
相同为0，不同为1，即
1 ^ 1 = 0
0 ^ 0 = 0
1 ^ 0 = 1

可以用于将两个变量值互换
```python
// 常规方法
int temp = a;  // temp = 3
a = b;         // a = 7
b = temp;      // b = 3
 
// 异或方法
a = a ^ b;  // a = 3 ^ 7
b = a ^ b;  // b = (3 ^ 7) ^ 7 = 3 ^ (7 ^ 7) = 3
a = a ^ b;  // a = (3 ^ 7) ^ (3 ^ 7 ^ 7) = (3 ^ 3) ^ (7 ^ 7) ^ 7 = 7
```


异或还满足以下规律
（1）交换律： A ^ B = B ^ A

（2）结合律： ( A ^ B ) ^ C = A ^ ( B ^ C )

（3）自反性： A ^ B ^ B = A （由结合律可推： A ^ B ^ B = A ^ ( B ^ B ) = A ^ 0 = A）

由运算规则可知，任何二进制数与零异或，都会等于其本身，即 A ^ 0 = A。
因此可以用来筛选偶数次重复的变种
0 ^ A = A, A ^ B ^ A = B
### & 按位与操作
a&b表示a和b的二进制数在每一位上进行“与”操作，可以用于判断一个数的奇偶性，每个数与1进行&操作，若为偶数则输出0，若为奇数则为1
```python
print(bin(10)[2:]) # 1010
print(bin(1)[2:]) # 1
print(bin(10 & 1)[2:]) # 0

num = 10
if num & 1:
    print("Odd")
else:
    print("Even")
```
### 位运算
将二进制数第n位改为1或0
```python
num = 0b1001  # 二进制数 1001，十进制数 9
n = 1  # 我们要将第1位改为1
# 使用位运算符将第n位改为1
num = num | (1 << n)
print(bin(num))  # 输出：0b1011

num = 0b1011  # 二进制数 1011，十进制数 11
n = 1  # 我们要将第1位改为0
# 使用位运算符将第n位改为0
num = num & ~(1 << n)

print(bin(num))  # 输出：0b1001
```
生成一个长度为n的全为1的二进制数
```python
n = 6
mask = (1 << n) - 1
print(bin(mask))# 0b111111
```
### any()逻辑表达式
```python
print(any([0, 1, 2]))  # 输出：True
print(any([0, '', None]))  # 输出：False
print(any([]))  # 输出：False
```
### 16进制
![图片](16.png)
### 堆
将一个数组元素按照完全二叉树的顺序储存在一维数组中，且满足所有双亲节点都比子节点数值小（大）的叫做小（大）堆
![图片](dui1.png)
python中将一个列表创建为堆，默认为小堆，即堆顶的为最小元素，可对所有元素进行取相反数操作获得大堆
```python
import heapq
nums = [1,3,-1,-3,5,3,6,7]
heapq.heapify(nums)
print(nums)#[-3, 1, -1, 3, 5, 3, 6, 7]
heapq.heappush(nums, -5)#[-5, 1, -3, 3, 5, 3, 6, 7, -1]
a = heapq.heappop(nums)
print(a)#-5


nums = [1,3,-1,-3,5,3,6,7]
nums = [-x for x in nums]
heapq.heapify(nums)
print(nums)#[-7, -3, -6, -1, -5, -3, -1]
a = -heapq.heappop(nums)
print(a)#7
```

也可以以元组或列表为元素创建为堆，元组中第一个元素用于确定元组在堆中的位置
```python
nums = [42,325,214,5426,32,54,1235,23,53,2,57,3]
q = [(-nums[i], i) for i in range(len(nums))]
heapq.heapify(q)
print(q) # [-5426, 3, -1235, 6, -325, 1, -214, 2, -53, 8, -54, 5, -42, 0, -32, 4, -23, 7, -3, 10, -2, 9, -57, 11]
```
堆中元素的删除：删除堆顶，然后总是从堆尾将某个数先放置到堆顶，然后依次下调到符合完全二叉树的要求，即每个子树的两个子节点都比父节点大（最小堆）
### 链表
链表的创建和实例化
```python
class ListNode:
    def __init__(self, x):
        self.val = x
        self.next = None

head = ListNode(1)
head.next = ListNode(2)
head.next.next = ListNode(3)
# 此时head为该链表的头节点
```
从列表创建链表
```python
list = [1, 2, 3, 4, 5]
dummy = ListNode(list[0])
dummy = ListNode(0)  # 创建一个哑节点作为链表的头节点
ptr = dummy
for i in list:
    ptr.next = ListNode(i)
    ptr = ptr.next
ptr = dummy.next # dummy的下一个节点为真正的头节点
```
对节点及节点后节点非空的判断
```python
head = Listnode() # 假设head为链表最后一位节点
head = head.next # 此时head为None
if not head or not head.next:
    print("head is None")
# 此时条件式成立
if not head.next or not head:
    print("head is None")
# 此时条件式不成立
```
### 二叉树的遍历
前序遍历：根、左、右
中序遍历：左、根、右
搜索二叉树：每个节点的右子树值都比其大，左子树所有节点数值都比其小。
搜索二叉树的中序遍历为升序列表