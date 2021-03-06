# 算法分析框架

- 时间效率：指正在讨论的算法运行得有多快
- 空间效率：指算法需要的额外存储空间情况

## 输入规模的度量

几乎所有的算法，对于规模更大的输入都需要运行更长的时间。常见的例子就是求和
、排序等。

可以使用一个以算法输入规模 \\(n\\) 为参数的函数，来研究的算法效率。

具体来说，参数 \\(n\\) 可以是：

- 排序、查找时，列表或集合的长度；
- 输入数据的大小、数量；
- 字符串处理时，字符的个数（以字符为单位）或词组的个数（以词组为单位）。

## 运行时间的度量单位

受计算机运行速度、程序及其编译质量等影响，直接使用算法程序的运行时间来判定算法的时间效率是不可取的。

我们可以通过统计算法中**元运算**的执行次数，来对算法的效率进行度量。元运算执行次数多，则算法的时间效率低。

通常，元运算指的是算法中重复执行，且最为耗时的操作。

常见问题中的元运算如下：

|问题|元运算|
|---|---|
|基于比较的数组查找|键值比较|
|矩阵乘法|乘法|
|计算 a 的 n 次幂|乘法|
|图问题|对结点或边的访问|

我们可以定义 \\(T(n)\\) 为输入规模 \\(n\\) 下算法的预计执行时间，\\(C(n)\\) 表示输入规模 \\(n\\) 下元运算的执行次数，\\(c\_{op}\\) 为元运算执行的单位时间，则有下列等式：

\\[T(n) \\approx c\_{op} C(n)\\]

如，对于某问题，有算法 A 和 算法 B。假设二者的 \\(c\_{op} = 1\\)，而算法  A 的 \\(C(n) = 5n\\)、算法 B 的 \\(C(n) = n^2\\)。

则 A、B 算法的效率与 \\(n\\) 的大小有关。

## 增长级

执行时间与 \\(n\\) 的关系，要考虑 \\(C(n)\\) 的增长级。

当输入规模较小时，在运行时间上的差别不足以将高效的算法和低效的算法区分开来。

不同增长级数的典型函数：

| \\(\\log_2{n}\\) |   \\(n\\)  |   \\(n\\log_2{n}\\)   |   \\(n^2\\)   |  \\(n^2\\)    | \\(2^n\\) | \\(n!\\)  |
| :--------------: | :--------: | :-------------------: | :-----------: | :-----------: | :-------: | :-------: |
| \\(3.3\\)        | \\(10^1\\) | \\(3.3 \\times 10^1\\) | \\(10^2\\)    | \\(10^3\\)    | \\(10^3\\)              | \\(3.6 \\times 10^6\\)     |
| \\(6.6\\)        | \\(10^2\\) | \\(6.6 \\times 10^2\\) | \\(10^4\\)    | \\(10^6\\)    | \\(1.3 \\times 10^{30}\\)| \\(9.3 \\times 10^{157}\\) |
| \\(10\\)         | \\(10^3\\) | \\(1.0 \\times 10^4\\) | \\(10^6\\)    | \\(10^9\\)    |  |  |
| \\(13\\)         | \\(10^4\\) | \\(1.3 \\times 10^5\\) | \\(10^8\\)    | \\(10^{12}\\) |  |  |
| \\(17\\)         | \\(10^5\\) | \\(1.7 \\times 10^6\\) | \\(10^{10}\\) | \\(10^{15}\\) |  |  |
| \\(20\\)         | \\(10^6\\) | \\(2.0 \\times 10^7\\) | \\(10^{12}\\) | \\(10^{18}\\) |  |  |

这些函数通常被用来描述算法的增长级数。大致可以分为“线性”“多项式”或“指数级”增长。

由于 \\(2^n\\) 和 \\(n!\\) 增长都非常快，虽然二者也有区别，但都可以称为“呈指数级增长的函数”。指数级算法只能解决输入规模很小的问题，很多困难问题目前只具有相应的指数级算法，实际上并没有被解决。

## 最优、最差和平均效率

许多算法的运行时间不仅取决于输入的规模，而且与**特定的输入**有关。

顺序查找是这样一种查找算法——与列表中的元素逐一比较，直到发现了匹配键值的元素或者到达了列表的终点。

最差情况下（访问了所有元素才找到/都没有找到键值匹配的元素），顺序查找的元运算执行次数 \\(C(n)\\) 为 \\(n\\)，而最优情况（第一次比较就找到了键值匹配的元素）下的 \\(C(n)\\) 仅为 1。

那么如何计算平均情况下的顺序查找的 \\(C(n)\\) 呢？

我们假设：

- 成功查找的概率为 \\(p\\)，\\(0 \\leq p \\leq 1\\)；
- 对于任意 \\(i\\)，首次成功匹配发生在第 \\(i\\) 个位置的概率都是相同的，都为 \\(\\frac{p}{n}\\)

则，平均查找次数可以表示为：

\\[
C\_{avg}(n) 
= \\sum\\limits\_{i=1}^{n} i \\times \\frac{p}{n} + n (1-p) \\
= \\frac{p}{n} \\times \\frac{n(n+1)}{2} + n (1-p) \\
= \\frac{(n+1)}{2} \\times p + n (1-p)
\\]

- \\(p=0\\) 意味着查找不成功，此时 \\(C(n) = n\\);
- \\(p=1\\) 意味着查找一定能成功，此时 \\(C(n) = \\frac{n+1}{2}\\)。

最差效率 \\(W(n)\\)：指当输入规模为 \\(n\\) 时，算法在最坏情况下的效率。研究最差效率可以探究算法运行时间上限；

最优效率 \\(B(n)\\)：指当输入规模为 \\(n\\) 时，算法在最优情况下的效率。

平均效率 \\(A(n)\\)：指当输入规模为 \\(n\\) 时，算法在随机输入情况下的效率。平均效率的分析难度大，但能更全面描述算法的效率。

## 总结

算法的时间效率可以用输入规模 \\(n\\) 的函数进行度量；

具体来说，使用算法中基本操作的执行次数来度量算法的时间效率；

在输入规模相同的情况下，有些算法的效率根据输入的不同，会有显著的差异。对于这样的算法，需要区分最差效率、平均效率和最优效率；

算法效率分析框架主要关心的是：当算法的输入规模趋向于无限大的时候，其运行时间函数的增长级。
