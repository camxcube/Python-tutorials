### 14 - 7 - 2020 投稿

> 打印一串字符串 “Hello, world! Hello, python!”

## 解题思路

简单来说，这题目就是要求你输出（注釋 1）"Hello, world! Hello, python!" 这一串句子。

如果你从这本书的开头开始看，你能在 1.5.1 入口章节中，间竭地看到使用了一个叫 print() 的函数把想要的结果输出。

print 函数最基础用法是:

```python
#版本 1
print("1. 你想打印的文字")

#版本 2
print('2. 你想打印的文字')

#版本 3
print('''3. 你想打印的文字''')
```

輸出結果：

```
1. 你想打印的文字
2. 你想打印的文字
3. 你想打印的文字
```

## 正解

你能看到以上使用 ' 号、" 号和''' 号都可以做到相同的效果（注釋 2）。 所以随便使用以上其中一个方法，输入以下代码，便能得到题目所要的答案:

```
print("Hello, world! Hello, python!")
Hello, world! Hello, python!
```


好了，其实到这里这题也就结束了，基本上你懂得以上的用法也就很足够了(最少必要的知识)，下面接着的部分是其他特别一点的解法，有兴趣可以接着看。

## 其他解题方式

关于 print 函数的细节，你可以参考 Python 官方文档的 print 函数章节([中文版](https://docs.python.org/zh-cn/3/library/functions.html#print)、[英文版](https://docs.python.org/3/library/functions.html#print))，里边有提到 print 函数的更多用法。

以下是其他的解题方式：

```python
# 版本 1
print("Hello,", "world!", "Hello, python!")

# 版本 2
print("Hello, world" + "! Hello," + " python!")

# 版本 3
print("Hello, world! Hello" ',' ''' python!''')

# 版本 4
print("Hello, world! Hello" ',' + ''' python!''')
```

輸出結果：

```
Hello, world! Hello, python!
Hello, world! Hello, python!
Hello, world! Hello, python!
Hello, world! Hello, python!
```

以上这几种用法，你分别可以查看 print 函数章节([中文版](https://docs.python.org/zh-cn/3/library/functions.html#print)、[英文版](https://docs.python.org/3/library/functions.html#print)) 和"字符串字面值拼接"章节([中文版](https://docs.python.org/zh-cn/3/reference/lexical_analysis.html#string-literal-concatenation)、[英文版](https://docs.python.org/3/reference/lexical_analysis.html#string-literal-concatenation))

------

注釋 1：题目使用了"打印"一词，而不是"输出"一词。这是因为 print 函数中的 print 一词直译为"打印"，所以简单来说，你可以理解"打印"即"输出"。

注釋 2：其实 print ("你想打印的文字") 是由两个部分组成，分别是 print 函数和字串符(string)(即 "你想打印的文字")组成，' 号、" 号和 ''' 号是出自字串符(string)的用法，而不是 print 函数。如果你是新手，可以先忽略这个知识点，以后会再深入讲到。