# 算法效率类型

算法效率分析框架主要关心一个算法的基本操作次数的增长级，并将其作为算法效率的主要指标。

现有一基准函数 \\(g(n)\\)，如 \\(g(n) = n^2\\)。为了对不同的增长级进行比较归类，作如下定义：

- \\(O(g(n))\\)：表示增长级数小于等于 \\(g(n)\\) 的函数集合；
- \\(\\Theta(g(n))\\)：表示增长级数等于 \\(g(n)\\) 的函数集合；
- \\(\\Omega(g(n))\\)：表示增长级数大于等于 \\(g(n)\\) 的函数集合。

关于 \\(O\\)、\\(\\Theta\\)、\\(\\Omega\\) 严格的定义如下。

函数 \\(t(n)\\) 包含在 \\(O(g(n))\\) 中，记作 \\(t(n) \\in O(g(n)\\)：

- 对于所有足够大的 \\(n\\)，\\(t(n)\\) 的上界由 \\(g(n)\\) 的常数倍所确定；
- 即，存在大于 0 的常数 \\(c\\) 和非负整数 \\(n\_0\\)，使得对于所有的 \\(n \\geq n\_0\\)，均有 \\(t(n) \\leq c\times g(n)\\)。

函数 \\(t(n)\\) 包含在 \\(\\Omega(g(n))\\) 中，记作 \\(t(n) \in \\Omega(g(n)\\)；

- 对于所有足够大的 \\(n\\)，\\(t(n)\\) 的下界由 \\(g(n)\\) 的常数倍所确定；
- 即，存在大于 0 的常数 \\(c\\) 和非负整数 \\(n\_0\\)，使得对于所有的 \\(n \\geq n\_0\\)，均有 \\(t(n) \\geq c\times g(n)\\)。

函数 \\(t(n)\\) 包含在 \\(\\Theta(g(n))\\) 中，记作 \\(t(n) \in \\Theta(g(n)\\)；

- 对于所有足够大的 \\(n\\)，\\(t(n)\\) 的上界和下界由 \\(g(n)\\) 的常数倍所确定；
- 即，存在大于 0 的常数 \\(c\_1, c\_2\\) 和非负整数 \\(n\_0\\)，使得对于所有的 \\(n \\geq n\_0\\)，均有 \\(c\_1 g(n) \\leq t(n) \\leq c\_2 g(n)\\)。

例：\\(n \in O(n^2)\\)、\\(100n+5 \in O(n^2)\\)、\\(100n+5 \\notin \Omega(n^2)\\)

## 定理

定理：若 \\(t\_1(n) \\in O(g\_1(n))\\) 且 \\(t\_2(n) \\in O(g\_2(n))\\)，则 \\(t\_1(n)+t\_2(n) \\in O(\\max\\{g\_1(n), g\_2(n)\\})\\)。\\(\\Omega\\) 和 \\(\\Theta\\) 同理。

例，算法包含两部分，A 部分 \\(C\_1(n) \\in O(n^2)\\)，B 部分 \\(C\_2(n) \\in O(n^2)\\)，所以算法总体效率 \\(C(n) \in O(\\max(n,n^2) ) = O(n^2)\\)。

## 利用极限比较增长级

求两个函数比率的极限 \\(\\lim\\limits{n \\to \\infty}{\\frac{t(n)}{g(n)}}\\)：

- \\(0\\)：表明 \\(t(n)\\) 的增长级数比 \\(g(n)\\) 小
- \\(c\\)：表明 \\(t(n)\\) 的增长级数和 \\(g(n)\\) 相同
- \\(\\infty\\)：表明 \\(t(n)\\) 的增长级数比 \\(g(n)\\) 大

## 基本的效率类型

|      级数       |  类型   |
| :-------------: | :-----: |
|     \\(c\\)     |  常数   |
| \\(\\log{n}\\)  |  对数   |
|     \\(n\\)     |  线性   |
| \\(n\\log{n}\\) | n-log-n |
|    \\(n^2\\)    |  平方   |
|    \\(n^3\\)    |  立方   |
|    \\(2^n\\)    |  指数   |
|    \\(n!\\)     |  阶乘   |

