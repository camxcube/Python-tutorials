### 20 - 7 - 2020 题目

> 假设 x 为列表对象，那么 x.pop() 和 x.pop(-1) 的作用是一样的。
> 这种说法正确吗？
>
> A 正确
>
> B 错误

我的答案是 **A：正确**



## 解析过程

由于 x 为列表对象，即属于数组 (array)。因此我们可以找到 Python 官方文档中的 Array 章节。在底下我们能找到 pop 方法的用法，以下为撷取的文字说明。

>`array.pop`([*i*])
>
>Removes the item with the index *i* from the array and returns it. The optional argument defaults to `-1`, so that by default the last item is removed and returned.

意思就是说该方法用作移除特定位置的项目，如果没有提供任何移除特定位置的参数，那么默认的参数则为 *-1*，即移除数组最后位置的项目。

我们再看看题目，x.pop() 因没填写任何参数，所以默认值为 *-1*，所以和 x.pop(-1) 为同一个意思。 
