# 课后作业

【习题 2.1.1】对于下列每种算法，请指出 (i) 其输入规模的合理量度；(ii) 它的基本操作；(iii) 对于规模相同的输入来说，其基本操作的次数是否会有所不同。

<ol type="a">
    <li>计算 \(n\) 个数的和；</li>
    <li>计算 \(n!\)；</li>
    <li>找出包含 \(n\) 个数字的列表中的最大元素；</li>
    <li>欧几里得算法；</li>
    <li>埃拉托色尼筛；</li>
    <li>两个 \(n\) 位十进制整数相乘的笔算算法。</li>
</ol>

【解】

| 序号 | 输入规模量度               | 基本操作                             | \\(C(n)\\) 是否变化  |
| ---- | -------------------------- | ------------------------------------ | -------------------- |
| a    | \\(n\\)                    | 两数之间的加法                       | 无                   |
| b    | \\(n\\) 的体量大小         | 两数之间的乘法                       | 无                   |
| c    | \\(n\\) （使用线性扫描法） | 两数之间的比较                       | 无（使用线性扫描法） |
| d    | 两数中较大者的体量大小     | 取模运算                             | 有                   |
| e    | \\(n\\) 的体量大小         | 从剩余候选项中排除不可能为素数的选项 | 无                   |
| f    | \\(n\\)                    | 两个一位十进制数的乘法               | 无                   |



【习题 2.2.2】请用 \\(O\\),  \\(\Omega\\) 和 \\(\Theta\\) 的非正式定义来判断下列断言是真还是假。

<ol type="a">
    <li>\(n(n+1)/2 \in O(n^3)\)</li>
    <li>\(n(n+1)/2 \in O(n^2)\)</li>
    <li>\(n(n+1)/2 \in \Theta(n^3)\)</li>
    <li>\(n(n+1)/2 \in \Omega(n)\)</li>
</ol>

【解】

<ol type="a">
  <li>真</li>
  <li>真</li>
  <li>假</li>
  <li>真</li>
</ol>

【习题 2.2.3】对于下列每一种函数,指出它们属于哪一种 \\(\Theta(g(n))\\) 类型（尽量使用最简单的 \\(g(n)\\)），并给出证明。

<ol type="a">
    <li>\((n^2+1)^{10}\)</li>
    <li>\(\sqrt{10n^2+7n+3}\)</li>
    <li>\(2n\lg{(n+2)^2}+(n+2)^2\lg{\frac n 2}\)</li>
    <li>\(2^{n+1}+3^{n-1}\)</li>
    <li>\(\lfloor log_2{n} \rfloor\)</li>
</ol>

【解】

<ol type="a">
    <li>
        <p>猜测：\((n^2+1)^{10} \approx (n^2)^{10} = n^{20} \in \Theta(n^{20})\).</p>
        <p>证明：\(
            \lim\limits_{n \to \infty}{ \frac{(n^2+1)^{10}}{n^{20}} }
            = \lim\limits_{n \to \infty}{ \frac{(n^2+1)^{10}}{(n^2)^{10}} }
            = \lim\limits_{n \to \infty}{ (\frac{n^2+1}{n^2})^{10} }
            = \lim\limits_{n \to \infty}{ (1+\frac{1}{n^2})^{10} } = 1 \).
        </p>
        <p>所以 \((n^2+1)^{10} \in \Theta(n^{20})\).</p>
    </li>
    <li>
        <p>猜测：\(\sqrt{10n^2+7n+3} \approx \sqrt{10n^2} = \sqrt{10}n \in \Theta( n ) \).</p>
        <p>证明：\(
            \lim\limits_{n \to \infty}{ \frac{\sqrt{10n^2+7n+3}}{n} } 
            = \lim\limits_{n \to \infty}{ \sqrt{\frac{10n^2+7n+3}{n^2}} }
            = \lim\limits_{n \to \infty}{ \sqrt{10+\frac 7 n + \frac{3}{n^2} } }
            = \sqrt{10} \)</p>
        <p>所以 \(\sqrt{10n^2+7n+3} \in \Theta( n ) \).</p>
    </li>
    <li>
        <p>\(2n\lg{(n+2)^2}+(n+2)^2\lg{\frac n 2} = 4n\lg{(n+2)} + (n+2)^2(\lg{n} - 1)\).</p>
        <p>故原式 \(\in \max\{ \Theta(n\lg n), \Theta(n^2\lg n)\} = \Theta(n^2\lg n)  \).</p>
    </li>
    <li>
        <p>\(2^{n+1}+3^{n-1} = 2\times 2^n + \frac 1 3 3^n \in \max\{\Theta(2^n), \Theta(3^n)\} = \Theta(3^n) \).</p>
    </li>
    <li>
        <p>证明，由 \(x-1 &lt; \lfloor x \rfloor \leq x \).</p>
        <p>得 \(\lfloor log_2{n} \rfloor \leq \log_2{n} \) 且 \(\lfloor log_2{n} \rfloor > \log_2{n} - 1 \).</p>
        <p>又 \(\forall n \geq 4, \lfloor log_2{n} \rfloor > \log_2{n} - 1 \geq \log_2{n} - \frac 1 2 \log_2{n} = \frac 1 2 \log_2{n} \).</p>
        <p>所以 \(\lfloor \log_2{n} \rfloor \in \Theta(\log_2{n}) = \Theta(\log{n}) \).</p>
    </li>
</ol>

【习题 2.2.5】按照下列函数的增长次数对它们进行排列（按照从低到高的顺序）。

- \\((n-2)!          \\)
- \\(5\lg{(n+100)^{10}}\\)
- \\(2^{2n}          \\)
- \\(0.001n^4+3n^3+1 \\)
- \\(\ln^2{n}        \\)
- \\(\sqrt[3]{n}     \\)
- \\(3^n             \\)

【解】

| 函数 | 所属集合 |
| ------------------------ | ------------------- |
| \\((n-2)!            \\) | \\( \\Theta((n-2)!        ) \\) |
| \\(5\lg{(n+100)^{10}}\\) | \\( \\Theta(\\log{n}      ) \\) |
| \\(2^{2n}            \\) | \\( \\Theta(4^n           ) \\) |
| \\(0.001n^4+3n^3+1   \\) | \\( \\Theta(n^4           ) \\) |
| \\(\ln^2{n}          \\) | \\( \\Theta(\\log^2{n}    ) \\) |
| \\(\sqrt[3]{n}       \\) | \\( \\Theta(n^{\\frac 1 3}) \\) |
| \\(3^n               \\) | \\( \\Theta(3^n           ) \\) |

比较 \\(\\log^2{n}\\) 和 \\(\\sqrt[3]{n}\\) 的增长次数：

\\[
\\lim\\limits\_{n \\to \\infty}{ \\frac{\\log^2{n}}{\\sqrt[3]{n}} }
= \\lim\\limits\_{n \\to \\infty}{ \\frac{(\\log^2{n})'}{(\\sqrt[3]{n})'} }
\\]

令 \\( u = \\log{n}\\)，则根据链式法则，

\\[
(\\log^2{n})' = (u^2)' = u' 2u = 2 \\log{n} \\frac{1}{n\\ln 2}
\\]

又

\\[
(\\sqrt[3]{n})' = \\frac {1} {3} n^{-\\frac 2 3} = \\frac{1}{3\\sqrt[3]{n^2}}
\\]

所以，

\\[
  \\lim\\limits\_{n \\to \\infty}{ \\frac{\\log^2{n}}{\\sqrt[3]{n}} }
= \\lim\\limits\_{n \\to \\infty}{
    \\frac {2 \\log{n} \\frac{1}{n\\ln 2}} {\\frac{1}{3\\sqrt[3]{n^2}}}
  }
= \\frac{6}{\\ln{2}} \\lim\\limits\_{n \\to \\infty}{
    \\frac{\\sqrt[3]{n^2} \\log{n}}{n}
  }
= \\frac{6}{\\ln{2}} \\lim\\limits\_{n \\to \\infty}{
    \\frac{\\log{n}}{\\sqrt[3]{n}}
  }
= 0
\\]

故 \\(\\log^2{n}\\) 的增长次数比 \\(\\sqrt[3]{n}\\) 小。

排序可得：

| 函数 | 所属集合 |
| ------------------------ | ------------------- |
| \\(5\lg{(n+100)^{10}}\\) | \\( \\Theta(\\log{n}      ) \\) |
| \\(\ln^2{n}          \\) | \\( \\Theta(\\log^2{n}    ) \\) |
| \\(\sqrt[3]{n}       \\) | \\( \\Theta(n^{\\frac 1 3}) \\) |
| \\(0.001n^4+3n^3+1   \\) | \\( \\Theta(n^4           ) \\) |
| \\(3^n               \\) | \\( \\Theta(3^n           ) \\) |
| \\(2^{2n}            \\) | \\( \\Theta(4^n           ) \\) |
| \\((n-2)!            \\) | \\( \\Theta((n-2)!        ) \\) |
