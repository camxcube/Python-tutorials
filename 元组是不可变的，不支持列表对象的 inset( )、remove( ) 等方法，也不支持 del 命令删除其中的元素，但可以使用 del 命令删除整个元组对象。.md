### 22 - 7 - 2020 题目

> 元组是不可变的，不支持列表对象的 inset( )、remove( ) 等方法，也不支持 del 命令删除其中的元素，但可以使用 del 命令删除整个元组对象。这种说法正确吗？
>
> A 正确
>
> B 错误

我的答案是 **A：正确**



## 解析过程

题目中有多个陈述句，我们需要逐一验证。

1. 第一句是：

> 元组是不可变的

这是*对的*，根据 Python 官方文档中的 Tuples 章节显示，的确是不可变的。以下是说明文字的撷取。

> Tuples are immutable sequences

另外，元组有固定的哈希值（Hash Value)，这是可变序列对象（Mutable Sequence Types）所没有的。

2. 接着是的陈述句是：

> 不支持列表对象的 inset( )、remove( ) 等方法

这是*对的*，根据 Python 官方文档中的 Tuples 章节显示，列表只支持基础的序列操作。以下是说明文字的撷取。

> Tuples implement all of the [common](dfile:///Users/Cam/Library/Application Support/Dash/DocSets/Python_3/Python 3.docset/Contents/Resources/Documents/doc/library/stdtypes.html#typesseq-common) sequence operations.

而基础列表操作就只包括以下几种：

> | Operation          | Result                                                 |
> | :----------------- | :----------------------------------------------------- |
> | `x in s`           | `True` if an item of *s* is equal to *x*, else `False` |
> | `x not in s`       | `False` if an item of *s* is equal to *x*, else `True` |
> | `s + t`            | the concatenation of *s* and *t*                       |
> | `s * n` or `n * s` | equivalent to adding *s* to itself *n*times            |
> | `s[i]`             | *i*th item of *s*, origin 0                            |
> | `s[i:j]`           | slice of *s* from *i* to *j*                           |
> | `s[i:j:k]`         | slice of *s* from *i* to *j* with step *k*             |
> | `len(s)`           | length of *s*                                          |
> | `min(s)`           | smallest item of *s*                                   |

3. 再接着是：

> 也不支持 del 命令删除其中的元素

这是*对的*，根据 Python 官方文档中的 The del statement 章节显示，del 函数只是对列表有作用。以下是撷取文字的说明。

> There is a way to remove an item from a list given its index instead of its value: the [`del`](dfile:///Users/Cam/Library/Application Support/Dash/DocSets/Python_3/Python 3.docset/Contents/Resources/Documents/doc/reference/simple_stmts.html#del) statement. This differs from the `pop()` method which returns a value. The `del`statement can also be used to remove slices from a list or clear the entire list (which we did earlier by assignment of an empty list to the slice). 

4. 好了，最后我们看最后一句：

> 但可以使用 del 命令删除整个元组对象

这是*对的*，根据 Python 官方文档中的 The del statement 章节显示，del 函数可以删除变数的，由于元组是储存在变数中的，当变数一当被删除，元组对象就自然消失。以下是利用 del 函数删除元组对象的演示。

```python
x = (1,2,3)
print(x)
del x
print (x)
```

输出结果：

```
(1,2,3)
Traceback (most recent call last):
  File "main.py", line 4, in <module>
    print (x)
NameError: name 'x' is not defined
```
