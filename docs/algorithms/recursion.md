![1.png](https://pic.leetcode-cn.com/86c8ce53d2a91f3d710fdba825333be582a15bd661e9f05a10278bf558fbf1ef-1.png)

文章目录：

1. 什么是递归
2. 



**什么是递归**

递归的基本思想是某个函数直接或者间接地调用自身，这样就把原问题的求解转换为许多性质相同但是规模更小的子问题。我们只需要关注如何把原问题划分成符合条件的子问题，而不需要去研究这个子问题是如何被解决的。递归和枚举的区别在于：枚举是横向地把问题划分，然后依次求解子问题，而递归是把问题逐级分解，是纵向的拆分。

**简单地说，就是如果在函数中存在着调用函数本身的情况，这种现象就叫递归。**

你以前肯定写过递归，只是不知道这就是递归罢了。

![Recursion example technology nested virtualization](https://www.noction.com/wp-content/uploads/2018/10/Recursion-example-technology-nested-virtualization.png)

以阶乘函数为例,如下, 在 factorial 函数中存在着 factorial(n - 1) 的调用，所以此函数是递归函数

```
public int factorial(int n) {
    if (n < =1) {
        return1;
    }
    return n * factorial(n - 1)
}
int fibonacci(int n) {
   // Base case
   if (n == 0 || n == 1) return n;

   // Recursive step
   return fibonacci(n-1) + fibonacci(n-2);
}
```

进一步剖析「递归」，先有「递」再有「归」，「递」的意思是将问题拆解成子问题来解决， 子问题再拆解成子子问题，...，直到被拆解的子问题无需再拆分成更细的子问题（即可以求解），「归」是说最小的子问题解决了，那么它的上一层子问题也就解决了，上一层的子问题解决了，上上层子问题自然也就解决了,....,直到最开始的问题解决,文字说可能有点抽象，那我们就以阶层 f(6) 为例来看下它的「递」和「归」。

![img](https://mmbiz.qpic.cn/mmbiz_jpg/OyweysCSeLWvDS0Xny7l5kj0Nj4znUDibKqgKHPzVqr7eXnSbuR7icf21OrBa8Fzcc0gF2XP9licCFkG6iaibrC5cgA/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

求解问题 f(6), 由于 f(6) = n * f(5), 所以 f(6) 需要拆解成 f(5) 子问题进行求解，同理 f(5) = n * f(4) ,也需要进一步拆分,... ,直到 f(1), 这是「递」，f(1) 解决了，由于 f(2) =  2 f(1) = 2 也解决了,.... f(n)到最后也解决了，这是「归」，所以递归的本质是能把问题拆分成具有**相同解决思路**的子问题，。。。直到最后被拆解的子问题再也不能拆分，解决了最小粒度可求解的子问题后，在「归」的过程中自然顺其自然地解决了最开始的问题。



 递归原理

------

> 递归是一种解决问题的有效方法，在递归过程中，函数将自身作为子例程调用

你可能想知道如何实现调用自身的函数。诀窍在于，每当递归函数调用自身时，它都会将给定的问题拆解为子问题。递归调用继续进行，直到到子问题无需进一步递归就可以解决的地步。

为了确保递归函数不会导致无限循环，它应具有以下属性：

1. 一个简单的`基本案例（basic case）`（或一些案例） —— 能够不使用递归来产生答案的终止方案。
2. 一组规则，也称作`递推关系（recurrence relation）`，可将所有其他情况拆分到基本案例。

注意，函数可能会有多个位置进行自我调用。



递归的基本思想是某个函数直接或者间接地调用自身，这样就把原问题的求解转换为许多性质相同但是规模更小的子问题。我们只需要关注如何把原问题划分成符合条件的子问题，而不需要去研究这个子问题是如何被解决的。递归和枚举的区别在于：枚举是横向地把问题划分，然后依次求解子问题，而递归是把问题逐级分解，是纵向的拆分。

递归代码最重要的两个特征：结束条件和自我调用。自我调用是在解决子问题，而结束条件定义了最简子问题的答案。

```
int func(你今年几岁) {
    // 最简子问题，结束条件
    if (你1999年几岁) return 我0岁;
    // 自我调用，缩小规模
    return func(你去年几岁) + 1;   
}
```





### 反转字符串(344)

>  编写一个函数，其作用是将输入的字符串反转过来。输入字符串以字符数组 `char[]` 的形式给出。
>
> 不要给另外的数组分配额外的空间，你必须**原地修改输入数组**、使用 O(1) 的额外空间解决这一问题。
>
> 你可以假设数组中的所有字符都是 ASCII 码表中的可打印字符。
>
> **示例 1：**
>
> ```
> 输入：["h","e","l","l","o"]
> 输出：["o","l","l","e","h"]
> ```

