16 - 7 - 2020 题目

> len ( [ i for i in range ( 10 ) ] ) 的输出结果是什么？
>
> A. 1
>
> B. 10
>
> C. 9
>
> D. 11



这题我的答案是 **B: 10**



*目錄*

[toc]

## 解题思路

这题比较复杂，我们需要先把题目拆分成以下几个部分：

- len ( )
- []
- i
- for i in range (10)



### len ( ) 函数说明

先说 len ( ) 函数，这个最简单，我们可以找到 Python 官方文档的 len(s) 这个小节查看说明，以下为说明文字撷取。

> Return the length (the number of items) of an object. The argument may be a sequence (such as a string, bytes, tuple, list, or range) or a collection (such as a dictionary, set, or frozen set).

len ( ) 函数中的 len 是 length 的缩写，字面意思即“长度”。这个函数的用途是计算一个序列或集合的长度，序列包括字串 (string)、元组 (tuple) 或 range 生成器等等，而集合则包括字典 (dictionary)、集合 (set)、冻结集合 (frozen set) 等等。

例子：

```
>> len([1,2,3])
```

输出结果：

```
3
```

以上例子表示 [1, 2, 3] 这个列表 (list) 有 3 个元素存在。



### [] 说明

**警告：这个章节挺复杂的，可以跳过不看，反正不会太影响理解题目。**

这里我们可以通过一番在 General Index 中搜寻到有关 [] 符号在 List displays 的这个小章节，以下是说明文字撷取。

>```
>list_display ::=  "[" [starred_list | comprehension] "]"
>```
>
>A list display yields a new list object, the contents being specified by either a list of expressions or a comprehension. When a comma-separated list of expressions is supplied, its elements are evaluated from left to right and placed into the list object in that order. When a comprehension is supplied, the list is constructed from the elements resulting from the comprehension.

以上大概意思就是说这是一个列表展示器，它会根据内部的 [starred_list | comprehension] 运算出另一个列表。列表的样子如下：

```
[1, 2, 3, 4, 5]
```

根据上面的 BNF 说明[^1]，[1, 2, 3, 4, 5] 这个样子的列表属于 starred_list，

而题目却是 [i for i in range (10) ] 这个样子，所以我们肯定不是看 starred_list 这个解释，而是看 comprehension 这个解释，随之我们就前往 Displays for lists, sets and dictionaries 这个章节查看，以下是说明文字撷取。

> For constructing a list, a set or a dictionary Python provides special syntax called “displays”, each of them in two flavors:
>
> - either the container contents are listed explicitly, or
> - they are computed via a set of looping and filtering instructions, called a *comprehension*.
>
> Common syntax elements for comprehensions are:
>
> ```
> comprehension ::=  assignment_expression comp_for
> comp_for      ::=  ["async"] "for" target_list "in" or_test [comp_iter]
> comp_iter     ::=  comp_for | comp_if
> comp_if       ::=  "if" expression_nocond [comp_iter]
> ```

我们看看 BNF 里的 comprehension 和 comp_for，样子是否很像 [i for i in range (10) ] 这个样子？

对的，是很像，但还有一点不确定，主要是第一个 i 跟 comprehension 中的  assignment_expression 不太像，于是我们再前往 assignment_expression 查看，以下是说明文字撷取。

> ```
> assignment_expression ::=  [identifier ":="] expression
> ```

嗯? 样子还不像﹗为什么呢？于是我们再继续往死里找，以下是我找的路径：

*assignment_expression* -> *expression* -> *conditional_expression* -> *or_test* -> *and_test* -> *not_test* -> *comparison* -> *or_expr*  -> *xor_expr* -> *and_expr* -> *shift_expr* -> *a_expr* -> *m_expr* -> *u_expr* -> *power* -> *primary* -> *atom* -> *identifier* -> *xid_start* -> *identifier*

终于在 Identifiers and keywords 这个章节里找到这个确实的证据了，以下是说明文字撷取。

> ```
> identifier   ::=  xid_start xid_continue*
> id_start     ::=  <all characters in general categories Lu, Ll, Lt, Lm, Lo, Nl, the underscore, and characters with the Other_ID_Start property>
> id_continue  ::=  <all characters in id_start, plus characters in the categories Mn, Mc, Nd, Pc and others with the Other_ID_Continue property>
> xid_start    ::=  <all characters in id_start whose NFKC normalization is in "id_start xid_continue*">
> xid_continue ::=  <all characters in id_continue whose NFKC normalization is in "id_continue*">
> ```
>
> The Unicode category codes mentioned above stand for:
>
> - *Lu* - uppercase letters
> - *Ll* - lowercase letters
> - *Lt* - titlecase letters
> - *Lm* - modifier letters
> - *Lo* - other letters
> - *Nl* - letter numbers
> - *Mn* - nonspacing marks
> - *Mc* - spacing combining marks
> - *Nd* - decimal numbers
> - *Pc* - connector punctuations
> - *Other_ID_Start* - explicit list of characters in [PropList.txt](http://www.unicode.org/Public/12.1.0/ucd/PropList.txt) to support backwards compatibility
> - *Other_ID_Continue* - likewise

从以上的 BNF 中的 identifier 和 id_start 中，已经可以看出题目中的第一个 i 即是 comprehension 中的 assignment_expression。

好了，确定就好，那我们就继续下一部分吧。



### i for i in range (10) 说明

在上面 “[] 说明“ 章节里提到 comprehension 的样子即是像题目中的 i for i in range (10) 样子。所以我们在这才把 i 和 for i in range(10) 合并在一起看的，我们再看看 [] 列表展示器的官方文档说明吧。

> For constructing a list, a set or a dictionary Python provides special syntax called “displays”, each of them in two flavors:
>
> - either the container contents are listed explicitly, or
> - they are computed via a set of looping and filtering instructions, called a *comprehension*.

根据以上第二点说明，大概意思就是说可以把 i 后面的迭代 (即 for i in range (10))产生的每个值放进 i，然后 i 再和 [] 列表展示器一起作用下，会扩展为一个新的列表。

那么 [i for i in range (10)] 最后产生的值便为： 

```
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```



### 最后步骤说明

那么将以上章节最后产生的值跟 len ( ) 函数相结合，便是：

```
len([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])
```

那么经过一番运算后，得出以上的列表元素数目为 10。

所以最后的答案为 *B: 10*



[^1]:BNF 的长写是 Backus–Naur form，是一套用来说明程序语言该如何使用的标示方法。这是另一个有点大的课题，如果你有兴趣，你可以前 Python 官方文档的 1.2. Notation 章节查看。但在这次我的讲解中，你基本可以不用学这个，因为我会用最简单的方法去说。

---

$答题者：Cam(雨 鹿 白 生)$