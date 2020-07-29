### 21 - 7 - 2020 题目

> 语句 x = (3,) 执行后x的值是什么？
>
> A: 3,
>
> B: 3
>
> C: (3,)
>
> D: 程序报错



这期我的答案是 **C：(3,)**



## 解析过程

题目中的 *(3,)* 其实是一个元组（tuple）。根据 Python 官方文档中的 Tuples 这个章节，下面第二点撷取文字便说明了此事。

> Tuples may be constructed in a number of ways:
>
> - Using a pair of parentheses to denote the empty tuple: `()`
> - Using a trailing comma for a singleton tuple: `a,` or `(a,)`
> - Separating items with commas: `a, b, c` or `(a, b, c)`
> - Using the [`tuple()`](dfile:///Users/Cam/Library/Application Support/Dash/DocSets/Python_3/Python 3.docset/Contents/Resources/Documents/doc/library/stdtypes.html#tuple) built-in: `tuple()` or `tuple(iterable)`

至于为什么特要加一个逗号，是因为加了才能表示这个一定是元组，以下的撷取文字说明了此事。

> Note that it is actually the comma which makes a tuple, not the parentheses. The parentheses are optional, except in the empty tuple case, or when they are needed to avoid syntactic ambiguity. For example, `f(a, b, c)` is a function call with three arguments, while `f((a, b, c))` is a function call with a 3-tuple as the sole argument.

所以将 (3,) 赋值给 x 后，输出 x 后，仍会呈现出我们熟悉的元组的样子，即 (3,)。



## One More Thing

你知道如果不加逗号，然后把这个值赋给 x，那么最后的值会是 (3) 吗？

我们可以找到 Parenthesized forms 这个章节来参考，以下是撷取的文字说明。

> ```
> parenth_form ::=  "(" [starred_expression] ")"
> ```
>
> A parenthesized expression list yields whatever that expression list yields: if the list contains at least one comma, it yields a tuple; otherwise, it yields the single expression that makes up the expression list.

以上说明了如果在括号内的不是元组的话，那么生成的便是括号里原有的对象，意思即是 (3) 等于 3 的意思。下面是演示例子：

```python
x = (3)
print(x)
```

输出结果：

```
3
```



