# Sobolev 空间第二课复盘：教材 1.10-1.34

教材：Robert A. Adams 与 John J. F. Fournier，*Sobolev Spaces*（第二版）
内容：泛函分析基础与连续函数空间

---

第 1.10-1.34 节梳理了后续章节需要用到的很多相关概念和知识。

第一条是泛函分析主线：

$$
\text{内积与 Hilbert 空间}
\longrightarrow
\text{对偶空间}
\longrightarrow
\text{自反性}
\longrightarrow
\text{弱收敛}
\longrightarrow
\text{紧性}.
$$

第二条是函数空间主线：

$$
C^m(\Omega)
\longrightarrow
C_B^m(\Omega)
\longrightarrow
C^m(\overline\Omega)
\longrightarrow
C^{m,\lambda}(\overline\Omega)
\longrightarrow
\text{连续与紧嵌入}.
$$

它们最终服务于 Sobolev 空间中的两个核心问题：

1. 一列近似解能否提取收敛子列？
2. 控制函数的弱导数后，能否推出函数本身连续、Hölder 连续或更光滑？

---

## 0. 一些记号约定

- $X'$：赋范空间 $X$ 的连续对偶空间，也常写作 $X^*$。
- $X''=(X')'$：二次对偶空间。
- $x_n\to x$：范数收敛。
- $x_n\rightharpoonup x$：弱收敛。
- $X\hookrightarrow Y$：$X$ 连续嵌入 $Y$。
- $X\hookrightarrow\hookrightarrow Y$：$X$ 紧嵌入 $Y$。
- $B_1(0)=\{x\in X:\|x\|_X\le 1\}$：闭单位球。
- $D^\alpha$：多重指标 $\alpha$ 对应的偏导数，阶数为 $|\alpha|$。

教材写作 $\|x;X\|$ 的地方，本文采用更常见的 $\|x\|_X$，便于理解和记忆。

---

# 第一部分：赋范空间与泛函分析基础

## 1.10 内积空间与 Hilbert 空间

### 1. 内积是什么？

设 $X$ 是复向量空间。内积是映射

$$
(\cdot,\cdot)_X:X\times X\to\mathbb C,
$$

满足以下性质。采用“对第一个变量线性”的约定：

1. 共轭对称性：

$$
(x,y)_X=\overline{(y,x)_X}.
$$

2. 对第一个变量线性：

$$
(ax+by,z)_X=a(x,z)_X+b(y,z)_X.
$$

由共轭对称性可推出第二个变量是共轭线性的：

$$
(x,ay+bz)_X=\overline a(x,y)_X+\overline b(x,z)_X.
$$

3. 正定性：

$$
(x,x)_X\ge 0,
\qquad
(x,x)_X=0\Longleftrightarrow x=0.
$$

实向量空间中没有复共轭，内积就是熟悉的对称双线性形式。

### 2. 内积怎样产生范数？

定义

$$
\|x\|_X=\sqrt{(x,x)_X}.
$$

三角不等式来自 Cauchy-Schwarz 不等式：

$$
|(x,y)_X|\le \|x\|_X\|y\|_X.
$$

### 3. 什么是 Hilbert 空间？

若 $X$ 在内积诱导的范数下完备，则称 $X$ 为 Hilbert 空间。

$$
\boxed{\text{Hilbert 空间}=\text{完备的内积空间}.}
$$

典型例子是

$$
\ell^2,
\qquad
L^2(\Omega),
$$

其中

$$
(u,v)_{L^2}=\int_\Omega u(x)\overline{v(x)}\,dx.
$$

### 4. 什么范数能来自内积？

内积诱导的范数一定满足平行四边形恒等式：

$$
\|x+y\|_X^2+\|x-y\|_X^2
=2\|x\|_X^2+2\|y\|_X^2.
$$

反过来，如果一个范数满足这个恒等式，那么它可以由某个内积产生。

这给出了判别方法。例如 $\ell^p$ 和 $L^p$ 在 $p\ne2$ 时通常不满足平行四边形恒等式，所以它们虽是 Banach 空间，却通常不是 Hilbert 空间。

### 本节要点

Hilbert 空间比一般 Banach 空间多了“角度、正交、投影”等几何结构。后面的 Riesz 表示定理正是 Hilbert 结构带来的特殊结论。

---

## 1.11 赋范对偶空间

### 1. 对偶空间

$X'$ 是 $X$ 上所有连续线性泛函的集合。对 $x'\in X'$，定义对偶范数

$$
\|x'\|_{X'}
=\sup_{\|x\|_X\le1}|x'(x)|.
$$

它表示：在 $X$ 的单位球上，泛函 $x'$ 最大能输出多大的数。

等价地，

$$
\|x'\|_{X'}
=\sup_{x\ne0}\frac{|x'(x)|}{\|x\|_X}.
$$

因此总有

$$
|x'(x)|\le \|x'\|_{X'}\|x\|_X.
$$

这个不等式非常重要，可以把泛函作用后的标量估计转化为 $X$ 中的范数估计。

### 2. 对偶空间为什么总是 Banach？

无论原空间 $X$ 是否完备，$X'$ 在对偶范数下总是 Banach 空间。

证明思路是：若 $(x_n')$ 在 $X'$ 中是 Cauchy 列，那么对每个固定 $x\in X$，数列 $x_n'(x)$ 在完备的标量域 $\mathbb C$ 中收敛。定义

$$
x'(x)=\lim_{n\to\infty}x_n'(x),
$$

再证明 $x'$ 仍是连续线性泛函，而且 $x_n'\to x'$ 于对偶范数。

### 3. 范数拓扑与弱星拓扑

若 $X$ 是无限维空间，$X'$ 上的范数拓扑通常严格强于弱星拓扑：

$$
\text{对偶范数收敛}
\Longrightarrow
\text{弱星收敛},
$$

反过来一般不成立。

---

## 1.12 Riesz 表示定理

### 定理

设 $X$ 是 Hilbert 空间。一个线性泛函 $x'$ 属于 $X'$，当且仅当存在唯一的 $x\in X$，使得

$$
x'(y)=(y,x)_X,
\qquad y\in X.
$$

而且

$$
\|x'\|_{X'}=\|x\|_X.
$$

### 直观理解

在有限维欧氏空间中，每个线性泛函都可以写成

$$
y\longmapsto y\cdot x
$$

的形式。Riesz 表示定理说：这个结论在任意 Hilbert 空间中仍然成立。

也就是说，Hilbert 空间里的每个连续线性泛函，本质上都是“与某个固定向量做内积”。所以在等距意义下，可以把

$$
X'\cong X.
$$

### 例子

在 $L^2(\Omega)$ 中，每个连续线性泛函都可唯一写为

$$
F(u)=\int_\Omega u(x)\overline{g(x)}\,dx
$$

其中某个唯一的 $g\in L^2(\Omega)$，并且

$$
\|F\|_{(L^2)'}=\|g\|_{L^2}.
$$

### 重要提醒

Riesz 表示定理是 Hilbert 空间的特殊优势，不应误认为一般 Banach 空间都能自然地与自己的对偶空间相同。

---

## 1.13 Hahn-Banach 延拓定理

### 定理

设 $M$ 是赋范空间 $X$ 的向量子空间，$m'\in M'$。那么存在 $x'\in X'$，使得

$$
x'|_M=m'
$$

且

$$
\|x'\|_{X'}=\|m'\|_{M'}.
$$

$m'$ 原本只定义在小空间 $M$ 上。Hahn-Banach 定理保证：可以把它延拓到整个 $X$，同时不增大范数。

“不增大范数”很关键，因为它表示延拓没有破坏原来的连续性强度。

### 重要推论：对偶可以检测向量大小

对每个 $x\in X$，都存在 $x'\in X'$，满足

$$
\|x'\|_{X'}=1,
\qquad
x'(x)=\|x\|_X.
$$

因此

$$
\|x\|_X
=\sup_{\|x'\|_{X'}\le1}|x'(x)|.
$$

这说明：虽然弱拓扑只使用泛函来“观察”向量，但所有连续线性泛函合在一起足以区分不同向量，也足以恢复范数大小。

---

## 1.14 自反空间

### 1. 二次对偶

$X'$ 的对偶记为

$$
X''=(X')'.
$$

$X''$ 中的元素作用在 $X'$ 上。

对每个 $x\in X$，定义 $Jx\in X''$：

$$
(Jx)(x')=x'(x),
\qquad x'\in X'.
$$

于是得到自然映射

$$
J:X\to X''.
$$

这里的“自然”表示不需要人为选择基或坐标。

### 2. $J$ 是等距嵌入

由对偶范数估计，

$$
|(Jx)(x')|=|x'(x)|
\le \|x'\|_{X'}\|x\|_X,
$$

所以

$$
\|Jx\|_{X''}\le\|x\|_X.
$$

Hahn-Banach 定理还能找到一个达到该大小的泛函，因此

$$
\|Jx\|_{X''}=\|x\|_X.
$$

所以 $X$ 总能等距地嵌入 $X''$。

### 3. 自反性的定义

若 $J$ 还是满射，即

$$
J(X)=X'',
$$

则称 $X$ 是自反空间。

直观上：$X''$ 中没有比原空间 $X$ 更多的新元素，每个二次对偶元素都来自某个 $x\in X$。

### 4. 例子

- 每个 Hilbert 空间都是自反的；
- $L^p(\Omega)$ 和 $\ell^p$ 在 $1<p<\infty$ 时自反；
- $L^1$、$\ell^1$、$L^\infty$、$\ell^\infty$ 一般不自反。

自反空间一定完备，因此一定是 Banach 空间。

---

## 1.15 自反性与可分性的关系

给出三个结论。

### 结论一

$$
X\text{ 自反}
\Longleftrightarrow
X'\text{ 自反}.
$$

### 结论二

$$
X'\text{ 可分}
\Longrightarrow
X\text{ 可分}.
$$

这个命题的反方向一般不成立。例如

$$
\ell^1\text{ 可分},
\qquad
(\ell^1)'=\ell^\infty\text{ 不可分}.
$$

### 结论三

若 $X$ 同时可分且自反，则 $X'$ 也可分。

理解方法：因为 $X$ 自反，可以把 $X''$ 与 $X$ 识别，所以 $X''$ 可分；再把结论二应用于空间 $X'$，得到 $X'$ 可分。

---

## 1.16 弱拓扑与弱收敛

### 1. 弱拓扑

$X$ 上的弱拓扑是使每个 $x'\in X'$ 都连续的最弱拓扑，记作

$$
\sigma(X,X').
$$

“最弱”表示：只保留让所有连续线性泛函仍然连续所必需的开集，不额外增加更多开集。

若 $X$ 是无限维空间，弱拓扑通常严格弱于范数拓扑。

### 2. 弱收敛

称 $x_n$ 弱收敛到 $x$，记为

$$
x_n\rightharpoonup x,
$$

如果对每个 $x'\in X'$ 都有

$$
x'(x_n)\to x'(x).
$$

直观上，弱收敛不是直接测量 $\|x_n-x\|_X$，而是让每个连续线性泛函去“测试”它们；所有测试结果都收敛，就称弱收敛。

### 3. 范数收敛一定推出弱收敛

因为

$$
|x'(x_n)-x'(x)|
\le \|x'\|_{X'}\|x_n-x\|_X.
$$

所以

$$
x_n\to x
\Longrightarrow
x_n\rightharpoonup x.
$$

反过来一般不成立。

### 4. 经典反例

在 $\ell^2$ 中令 $e_n$ 为第 $n$ 个标准正交向量。则

$$
\|e_n\|_{\ell^2}=1,
$$

所以 $e_n$ 不可能范数收敛到 $0$。但对任意 $y=(y_k)\in\ell^2$，

$$
(e_n,y)_{\ell^2}=\overline{y_n}\to0.
$$

因此

$$
e_n\rightharpoonup0.
$$

### 5. 闭凸集的重要性质

赋范空间中的凸集如果在范数拓扑下闭，那么它也在弱拓扑下闭。

对一般非凸集，这个结论不一定成立。凸性使 Hahn-Banach 分离定理可以发挥作用。

### 为什么对 PDE 重要？

范数收敛往往太强，近似解序列不容易得到强收敛；弱收敛更容易出现。存在性证明经常先得到有界性，再提取弱收敛子列。

---

## 1.17 紧集、预紧集与弱序列紧性

### 1. 紧集

在赋范空间中，集合 $A$ 紧，等价于：$A$ 中每个序列都存在一个子列，在范数意义下收敛到 $A$ 中的某个点。

即对任意 $(x_n)\subset A$，存在子列 $(x_{n_k})$ 和 $x\in A$，使得

$$
\|x_{n_k}-x\|_X\to0.
$$

### 2. 闭且有界是否足够？

紧集一定闭且有界。但在无限维赋范空间中，闭且有界通常不能推出紧。

例如 $\ell^2$ 的闭单位球包含全部 $e_n$，而

$$
\|e_n-e_m\|_{\ell^2}=\sqrt2
\qquad(n\ne m).
$$

所以 $(e_n)$ 没有范数收敛子列，闭单位球不紧。

只有在有限维空间中，才有熟悉的 Heine-Borel 结论：

$$
\text{闭且有界}\Longleftrightarrow\text{紧}.
$$

### 3. 预紧集

$A$ 称为预紧的，如果其闭包 $\overline A$ 是紧集。

预紧集本身可以不是闭的。例如有限维空间中的开球是预紧的，但不是紧集，因为它不闭。

### 4. 弱序列紧

$A$ 称为弱序列紧的，如果 $A$ 中每个序列都有一个子列弱收敛到 $A$ 中某点。

弱收敛比范数收敛要求低，因此弱序列紧比范数紧更容易成立。

---

## 1.18 自反性的紧性刻画

### 定理

Banach 空间 $X$ 自反，当且仅当其闭单位球

$$
B_1(0)=\{x\in X:\|x\|_X\le1\}
$$

是弱序列紧的。

### 等价的实用说法

在自反 Banach 空间中，每个有界序列都有弱收敛子列。

为什么？若 $(x_n)$ 有界，则存在 $R>0$ 使 $x_n\in RB_1(0)$。单位球弱序列紧，缩放后的球同样弱序列紧。

### PDE 中的标准用法

若能证明近似解满足

$$
\|u_n\|_X\le C,
$$

并且 $X$ 自反，那么存在子列和 $u\in X$，使

$$
u_{n_k}\rightharpoonup u.
$$

这往往是构造弱解的第一步。

---

## 1.19 有限 $\varepsilon$-网与预紧性

### 定理

设 $X$ 是 Banach 空间。集合 $A\subset X$ 预紧，当且仅当对每个 $\varepsilon>0$，都存在有限集合 $N_\varepsilon\subset X$，使得

$$
A\subset\bigcup_{y\in N_\varepsilon}B_\varepsilon(y).
$$

$N_\varepsilon$ 称为 $A$ 的有限 $\varepsilon$-网。

### 直观理解

无论要求多高的精度 $\varepsilon$，都只需要有限个半径为 $\varepsilon$ 的球，就能覆盖整个 $A$。这表示 $A$ 虽可能有无限多个点，却没有无限多彼此分离的“小尺度自由度”。

这个性质也叫完全有界。

### 与普通有界的区别

- 有界：存在一个很大的球覆盖 $A$；
- 完全有界：对任意小的半径，都能用有限多个小球覆盖 $A$。

完全有界远强于有界。无限维空间的闭单位球有界，但通常不完全有界。

---

## 1.20 一致凸性

### 定义

范数 $\|\cdot\|_X$ 称为一致凸的，如果对每个 $0<\varepsilon\le2$，都存在 $\delta(\varepsilon)>0$，使得只要

$$
\|x\|_X=\|y\|_X=1,
\qquad
\|x-y\|_X\ge\varepsilon,
$$

就有

$$
\left\|\frac{x+y}{2}\right\|_X
\le1-\delta(\varepsilon).
$$

### 几何意义

$x,y$ 都在单位球面上。如果它们相距至少 $\varepsilon$，那么中点不能仍然贴近单位球面，而必须向球内部缩进至少 $\delta(\varepsilon)$。

因此一致凸空间的单位球没有平坦边，也不能有越来越接近平坦边的区域。

### 重要提醒

一致凸性是具体范数的性质，而不仅是拓扑性质。一个空间可能存在两个等价范数，其中一个一致凸，另一个不一致凸。

教材也把“存在某个一致凸等价范数”的可赋范空间称为一致凸空间。

### 例子

- Hilbert 空间一致凸；
- $L^p$ 和 $\ell^p$ 在 $1<p<\infty$ 时一致凸；
- $L^1$ 和 $L^\infty$ 通常不一致凸。

Hilbert 空间的一致凸性可由平行四边形恒等式直接看出。

---

## 1.21 一致凸推出自反

### 定理

$$
\boxed{
\text{一致凸 Banach 空间}
\Longrightarrow
\text{自反空间}.
}
$$

这一定理常称为 Milman-Pettis 定理。

结合 1.18 可得：一致凸 Banach 空间中的每个有界序列都有弱收敛子列。

这条链在 Sobolev 空间中非常重要：

$$
1<p<\infty
\Longrightarrow
L^p\text{ 一致凸}
\Longrightarrow
L^p\text{ 自反}
\Longrightarrow
\text{有界序列可提取弱收敛子列}.
$$

以后会利用乘积空间和闭子空间，把这些性质传给 $W^{m,p}(\Omega)$。

---

## 1.22 闭子空间继承性质

设 $X$ 是 Banach 空间，$M\subset X$ 是闭向量子空间。则 $M$ 在继承范数下仍是 Banach 空间。

原因很直接：$M$ 中的 Cauchy 列在 $X$ 中收敛；由于 $M$ 闭，极限仍在 $M$ 中。

此外：

1. 若 $X$ 可分，则 $M$ 可分；
2. 若 $X$ 自反，则 $M$ 自反；
3. 若 $X$ 一致凸，则 $M$ 在继承范数下也一致凸。

### 为什么必须要求 $M$ 闭？

如果 $M$ 不闭，$M$ 中的 Cauchy 列可能收敛到 $X$ 中一个不属于 $M$ 的点，于是 $M$ 不完备。

### 与 Sobolev 空间的联系

以后会把 Sobolev 函数 $u$ 映射成

$$
(D^\alpha u)_{|\alpha|\le m}
$$

这个有限向量，并证明所有这样的向量形成某个 $L^p$ 乘积空间的闭子空间。于是 Sobolev 空间的完备性、自反性等性质就可从乘积空间继承。

---

## 1.23 有限个 Banach 空间的笛卡尔积

设 $X_1,\ldots,X_n$ 是 Banach 空间，定义

$$
X=\prod_{j=1}^nX_j.
$$

元素写成

$$
x=(x_1,\ldots,x_n),
\qquad x_j\in X_j.
$$

向量运算逐分量定义：

$$
x+y=(x_1+y_1,\ldots,x_n+y_n),
$$

$$
cx=(cx_1,\ldots,cx_n).
$$

对 $1\le p<\infty$，定义

$$
\|x\|_{(p)}
=\left(\sum_{j=1}^n\|x_j\|_{X_j}^p\right)^{1/p},
$$

以及

$$
\|x\|_{(\infty)}
=\max_{1\le j\le n}\|x_j\|_{X_j}.
$$

这些范数彼此等价，因为

$$
\|x\|_{(\infty)}
\le\|x\|_{(p)}
\le\|x\|_{(1)}
\le n\|x\|_{(\infty)}.
$$

在任意这些范数下，$X$ 都是 Banach 空间。

此外，有限乘积继承以下性质：

- 每个 $X_j$ 可分，则 $X$ 可分；
- 每个 $X_j$ 自反，则 $X$ 自反；
- 每个 $X_j$ 一致凸，则当 $1<p<\infty$ 时，$\|\cdot\|_{(p)}$ 是一致凸范数。

### 为什么强调“有限”乘积？

有限维向量上的各种 $p$ 型范数自动等价；无限乘积时，$\ell^1$、$\ell^2$、$\ell^\infty$ 会成为真正不同的空间，性质不再能这样简单转移。

---

## 1.24 算子

### 1. 算子是什么？

这里的算子就是空间之间的映射：

$$
f:X\to Y.
$$

它不一定线性。

### 2. 连续性的序列判别

因为赋范空间是度量空间，$f$ 连续当且仅当

$$
x_n\to x
\Longrightarrow
f(x_n)\to f(x).
$$

这称为序列连续性。在赋范空间中，它和通常的连续性等价。

### 3. 有界算子

教材称 $f$ 有界，如果 $X$ 中每个有界集 $A$ 的像 $f(A)$ 在 $Y$ 中仍有界。

对于线性算子 $T:X\to Y$，有界性等价于存在 $C>0$，使

$$
\|Tx\|_Y\le C\|x\|_X
$$

对所有 $x\in X$ 成立；也等价于 $T$ 连续。

### 4. 算子范数

线性算子 $T$ 的范数定义为

$$
\|T\|
=\sup_{\|x\|_X\le1}\|Tx\|_Y
=\sup_{x\ne0}\frac{\|Tx\|_Y}{\|x\|_X}.
$$

于是

$$
\|Tx\|_Y\le\|T\|\|x\|_X.
$$

### 5. 紧算子

$f:X\to Y$ 称为紧算子，如果对 $X$ 中每个有界集 $A$，$f(A)$ 在 $Y$ 中预紧。

对线性算子，等价的序列描述是：任意有界序列 $(x_n)$，其像序列 $(Tx_n)$ 都有一个在 $Y$ 中范数收敛的子列。

紧算子一定有界。教材把同时连续且紧的算子称为完全连续算子；不同教材对“完全连续”的术语可能有不同约定，应以本书为准。

---

## 1.25 连续嵌入与紧嵌入

### 1. 连续嵌入

若 $X$ 是 $Y$ 的向量子空间，并且恒等映射

$$
I:X\to Y,
\qquad Ix=x
$$

连续，就称 $X$ 连续嵌入 $Y$，记作

$$
X\hookrightarrow Y.
$$

由于 $I$ 线性，连续性等价于存在 $M>0$，使

$$
\|x\|_Y\le M\|x\|_X,
\qquad x\in X.
$$

直观上，$X$ 的范数比 $Y$ 的范数更强：控制 $X$ 范数就自动控制 $Y$ 范数。

### 2. 紧嵌入

如果嵌入算子 $I:X\to Y$ 是紧算子，就称 $X$ 紧嵌入 $Y$，记作

$$
X\hookrightarrow\hookrightarrow Y.
$$

等价地：每个在 $X$ 中有界的序列，都存在一个子列在 $Y$ 中强收敛。

### 3. 连续嵌入与紧嵌入的区别

连续嵌入只保证

$$
\|x\|_Y\le M\|x\|_X;
$$

紧嵌入还保证从 $X$ 中有界序列提取出在 $Y$ 中强收敛的子列。

因此紧嵌入比连续嵌入强得多。

### Sobolev 理论中的意义

以后会看到形如

$$
W^{m,p}(\Omega)\hookrightarrow L^q(\Omega)
$$

的 Sobolev 连续嵌入，以及形如

$$
W^{1,p}(\Omega)\hookrightarrow\hookrightarrow L^q(\Omega)
$$

的 Rellich-Kondrachov 紧嵌入。

---

# 第二部分：连续函数与 Hölder 函数空间

## 1.26 $C^m(\Omega)$、$C^\infty(\Omega)$ 与紧支集函数

### 1. $C^m(\Omega)$

对非负整数 $m$，定义

$$
C^m(\Omega)
=\{\varphi:D^\alpha\varphi\text{ 在 }\Omega\text{ 上连续，所有 }|\alpha|\le m\}.
$$

特别地，

$$
C^0(\Omega)=C(\Omega).
$$

$C^m$ 表示函数具有直到 $m$ 阶的连续经典偏导数。

### 2. $C^\infty(\Omega)$

定义

$$
C^\infty(\Omega)
=\bigcap_{m=0}^\infty C^m(\Omega).
$$

也就是函数具有任意阶连续偏导数，称为光滑函数。

### 3. 紧支集子空间

教材中的 $C_0(\Omega)$ 和 $C_0^\infty(\Omega)$ 分别表示 $C(\Omega)$ 和 $C^\infty(\Omega)$ 中具有紧支集的函数。

常见的另一套记号是

$$
C_c(\Omega),
\qquad
C_c^\infty(\Omega).
$$

本文更推荐使用下标 $c$ 来明确表示 compact support，以免和“边界上取零”或“无穷远消失”的其他记号混淆。

$C_c^\infty(\Omega)$ 是分布与弱导数理论中的测试函数空间。

---

## 1.27 有界连续导数空间 $C_B^m(\Omega)$

$C^m(\Omega)$ 中的函数不一定有界，导数也不一定有界。

例如在 $\Omega=(0,1)$ 上，

$$
u(x)=\frac1x
$$

属于 $C^\infty(0,1)$，但它在靠近 $0$ 时无界。

定义

$$
C_B^m(\Omega)
=\{\varphi\in C^m(\Omega):D^\alpha\varphi\text{ 有界，所有 }|\alpha|\le m\}.
$$

范数为

$$
\|\varphi\|_{C_B^m(\Omega)}
=\max_{|\alpha|\le m}
\sup_{x\in\Omega}|D^\alpha\varphi(x)|.
$$

这个范数同时控制函数本身和所有不超过 $m$ 阶的偏导数。

$C_B^m(\Omega)$ 在此范数下是 Banach 空间。

### 为什么它完备？

若 $(\varphi_n)$ 在该范数下是 Cauchy 列，那么对每个 $|\alpha|\le m$，$(D^\alpha\varphi_n)$ 都一致 Cauchy，从而一致收敛到某个有界连续函数。再利用微积分基本定理，可以验证这些极限之间仍保持正确的导数关系。

---

## 1.28 $C^m(\overline\Omega)$：可连续延拓到边界的函数

### 1. 为什么需要单独定义？

函数在开集 $\Omega$ 内连续，不表示它在接近边界时行为良好。

例如 $1/x$ 在 $(0,1)$ 内光滑，却不能连续延拓到 $x=0$。

### 2. 一致连续保证延拓

若 $\varphi\in C(\Omega)$ 有界且一致连续，那么它可以唯一地连续延拓到闭包 $\overline\Omega$。

一致连续是指：

$$
\forall\varepsilon>0,
\ \exists\delta>0,
\quad
|x-y|<\delta
\Longrightarrow
|\varphi(x)-\varphi(y)|<\varepsilon,
$$

其中同一个 $\delta$ 对所有 $x,y\in\Omega$ 都有效。

### 3. 定义

教材定义 $C^m(\overline\Omega)$ 为所有满足下列条件的 $\varphi\in C^m(\Omega)$：对每个 $|\alpha|\le m$，$D^\alpha\varphi$ 在 $\Omega$ 上有界且一致连续。

于是所有这些导数都能唯一连续延拓到 $\overline\Omega$。

范数为

$$
\|\varphi\|_{C^m(\overline\Omega)}
=\max_{|\alpha|\le m}
\sup_{x\in\Omega}|D^\alpha\varphi(x)|.
$$

$C^m(\overline\Omega)$ 是 $C_B^m(\Omega)$ 的闭子空间，因此也是 Banach 空间。

### 4. 记号的细微问题

当 $\Omega$ 无界时，这个记号可能造成歧义。例如集合意义上

$$
\overline{\mathbb R^n}=\mathbb R^n,
$$

但教材中的 $C^m(\overline{\mathbb R^n})$ 还要求各阶导数有界且一致连续，所以它一般严格小于所有 $C^m(\mathbb R^n)$ 函数组成的空间。

---

## 1.29 Hölder 连续函数空间 $C^{m,\lambda}(\overline\Omega)$

### 1. Hölder 条件

设 $0<\lambda\le1$。函数 $f$ 满足指数为 $\lambda$ 的 Hölder 条件，是指存在 $K>0$，使

$$
|f(x)-f(y)|\le K|x-y|^\lambda
$$

对所有 $x,y\in\Omega$ 成立。

最小的这类控制常数由 Hölder 半范数表示：

$$
[f]_{C^{0,\lambda}(\overline\Omega)}
=\sup_{\substack{x,y\in\Omega\\x\ne y}}
\frac{|f(x)-f(y)|}{|x-y|^\lambda}.
$$

当 $\lambda=1$ 时就是 Lipschitz 连续。

### 2. $C^{m,\lambda}$ 的定义

教材定义 $C^{m,\lambda}(\overline\Omega)$ 为 $C^m(\overline\Omega)$ 中满足下列条件的函数：对所有 $|\alpha|\le m$，$D^\alpha\varphi$ 都满足指数 $\lambda$ 的 Hölder 条件。

可写范数

$$
\|\varphi\|_{C^{m,\lambda}(\overline\Omega)}
=\|\varphi\|_{C^m(\overline\Omega)}
+\max_{|\alpha|\le m}
[D^\alpha\varphi]_{C^{0,\lambda}(\overline\Omega)}.
$$

这是 Banach 空间。

### 3. 指数越大，条件越强

若

$$
0<\nu<\lambda\le1,
$$

那么

$$
C^{m,\lambda}(\overline\Omega)
\subsetneq
C^{m,\nu}(\overline\Omega)
\subsetneq
C^m(\overline\Omega)
$$

在通常情形下是严格包含。

原因是当 $|x-y|$ 很小时，较大的指数 $\lambda$ 使 $|x-y|^\lambda$ 更小，从而要求函数振荡得更慢。

例如在 $[0,1]$ 上，

$$
f(x)=x^\lambda
$$

具有 $\lambda$-Hölder 连续性，但一般不具有任何更高指数的 Hölder 连续性。

### 4. Lipschitz 不等于处处可微

函数

$$
f(x)=|x|
$$

是 Lipschitz 连续的，但在 $x=0$ 不可微。因此一般不能断言

$$
C^{m,1}(\overline\Omega)
\subset C^{m+1}(\overline\Omega).
$$

反方向 $C^{m+1}\subset C^{m,1}$ 也需要区域几何条件；在凸区域上可以用中值定理得到，见 1.34。

---

## 1.30 有界区域上的两个核心问题

从这里开始假设 $\Omega$ 有界。由于 $\overline\Omega$ 闭且有界，它在 $\mathbb R^n$ 中是紧集。

本节引出两个问题：

1. 哪些简单函数族在 $C(\overline\Omega)$ 中稠密？
2. $C(\overline\Omega)$ 的哪些子集是预紧的？

前者由 Stone-Weierstrass 定理回答，后者由 Ascoli-Arzelà 定理回答。

---

## 1.31 Stone-Weierstrass 定理

设 $\Omega\subset\mathbb R^n$ 有界，$\mathcal A\subset C(\overline\Omega)$。若 $\mathcal A$ 满足：

1. 对加法、乘法和复数数乘封闭：若 $\varphi,\psi\in\mathcal A$、$c\in\mathbb C$，则

$$
\varphi+\psi,
\qquad
\varphi\psi,
\qquad
c\varphi
\in\mathcal A;
$$

2. 对复共轭封闭：

$$
\varphi\in\mathcal A
\Longrightarrow
\overline\varphi\in\mathcal A;
$$

3. 能分离不同点：若 $x\ne y$，存在 $\varphi\in\mathcal A$ 使

$$
\varphi(x)\ne\varphi(y);
$$

4. 在每个点不同时全部为零：对每个 $x\in\overline\Omega$，存在 $\varphi\in\mathcal A$ 使

$$
\varphi(x)\ne0.
$$

那么 $\mathcal A$ 在 $C(\overline\Omega)$ 的一致范数下稠密。

即对任意 $f\in C(\overline\Omega)$ 和 $\varepsilon>0$，存在 $\varphi\in\mathcal A$，使

$$
\|f-\varphi\|_\infty<\varepsilon.
$$

### 条件的直观含义

- 代数封闭：函数族足够稳定，能组合出复杂函数；
- 共轭封闭：处理复值函数所需；
- 分离点：函数族能区分不同位置；
- 处处非退化：没有某个点被整个函数族共同忽略。

若 $\mathcal A$ 包含常数函数 $1$，第四条自动成立。

---

## 1.32 多项式稠密与 $C(\overline\Omega)$ 的可分性

设 $P$ 是所有具有“有理复系数”的多项式集合。所谓有理复系数，是形如

$$
a+ib,
\qquad a,b\in\mathbb Q
$$

的数。

Stone-Weierstrass 定理首先说明所有复系数多项式在 $C(\overline\Omega)$ 中稠密。

任意复系数多项式又可以在紧集 $\overline\Omega$ 上被有理复系数多项式一致逼近。因此 $P$ 仍然稠密。

由于：

- 单项式只有可数多个；
- 有理复数集合可数；
- 每个多项式只有有限项；

所以 $P$ 是可数集。于是 $C(\overline\Omega)$ 存在可数稠密子集，即

$$
\boxed{C(\overline\Omega)\text{ 是可分 Banach 空间}.}
$$

---

## 1.33 Ascoli-Arzelà 定理

设 $\Omega$ 有界，$K\subset C(\overline\Omega)$。如果满足以下两点，则 $K$ 在一致范数下预紧。

### 条件一：一致有界

存在 $M>0$，使得对所有 $\varphi\in K$ 和 $x\in\overline\Omega$，都有

$$
|\varphi(x)|\le M.
$$

注意这里同一个 $M$ 对整个函数族都有效。

### 条件二：等度连续

对每个 $\varepsilon>0$，存在 $\delta>0$，使得对所有 $\varphi\in K$ 和所有 $x,y\in\overline\Omega$，只要

$$
|x-y|<\delta,
$$

就有

$$
|\varphi(x)-\varphi(y)|<\varepsilon.
$$

关键仍是：同一个 $\delta$ 必须同时适用于所有 $\varphi\in K$。

### 结论的序列形式

任取序列 $(\varphi_n)\subset K$，都能选出一个子列，在 $\overline\Omega$ 上一致收敛到某个连续函数。

### 单个函数一致连续与函数族等度连续

- 一致连续：对一个固定函数，$\delta$ 不依赖点 $x,y$；
- 等度连续：$\delta$ 不仅不依赖点，还不依赖函数族中的 $\varphi$。

### 为什么重要？

Ascoli-Arzelà 定理把两种容易验证的估计

$$
\text{统一控制函数大小}
+
\text{统一控制函数振荡}
$$

转化为强收敛子列。这正是证明紧嵌入的基本工具。

---

## 1.34 连续函数空间之间的嵌入

设 $m$ 是非负整数，并且

$$
0<\nu<\lambda\le1.
$$

### 一、总是成立的连续嵌入

#### 1. 少控制一阶导数

$$
C^{m+1}(\overline\Omega)
\hookrightarrow
C^m(\overline\Omega).
$$

因为 $C^{m+1}$ 范数已经包含所有 $|\alpha|\le m$ 的导数控制：

$$
\|\varphi\|_{C^m}
\le
\|\varphi\|_{C^{m+1}}.
$$

#### 2. Hölder 控制蕴含连续控制

$$
C^{m,\nu}(\overline\Omega)
\hookrightarrow
C^m(\overline\Omega),
$$

因为 $C^{m,\nu}$ 范数本身包含 $C^m$ 范数。

#### 3. 较高 Hölder 指数嵌入较低指数

$$
C^{m,\lambda}(\overline\Omega)
\hookrightarrow
C^{m,\nu}(\overline\Omega).
$$

证明时把点对分成两类。

当 $0<|x-y|<1$ 时，因为 $\lambda>\nu$，

$$
|x-y|^\lambda\le|x-y|^\nu.
$$

因此 $\lambda$-Hölder 控制自动给出 $\nu$-Hölder 控制。

当 $|x-y|\ge1$ 时，利用有界性：

$$
\frac{|D^\alpha\varphi(x)-D^\alpha\varphi(y)|}{|x-y|^\nu}
\le
2\sup_{z\in\Omega}|D^\alpha\varphi(z)|.
$$

所以存在常数 $C$ 使

$$
\|\varphi\|_{C^{m,\nu}}
\le C\|\varphi\|_{C^{m,\lambda}}.
$$

教材的范数约定下可取类似 $C=2$ 的统一常数。

### 二、$\Omega$ 有界时的紧嵌入

若 $\Omega$ 有界，则

$$
C^{m,\nu}(\overline\Omega)
\hookrightarrow\hookrightarrow
C^m(\overline\Omega),
$$

以及

$$
C^{m,\lambda}(\overline\Omega)
\hookrightarrow\hookrightarrow
C^{m,\nu}(\overline\Omega).
$$

第一条的核心是 Ascoli-Arzelà：$C^{m,\nu}$ 中有界的函数族，其各阶导数一致有界且等度连续，所以可以逐阶抽取一致收敛子列。

第二条表示：较高 Hölder 指数不仅连续控制较低指数，还会产生紧性。直观上，额外的 Hölder 正则性消除了越来越剧烈的小尺度振荡。

### 三、$\Omega$ 凸时的嵌入

若 $\Omega$ 凸，则任意 $x,y\in\Omega$ 之间的线段完全位于 $\Omega$ 中，可以沿线段使用中值定理。

对 $|\alpha|\le m$，

$$
|D^\alpha\varphi(x)-D^\alpha\varphi(y)|
\le C_n|x-y|\|\varphi\|_{C^{m+1}(\overline\Omega)}.
$$

因此

$$
C^{m+1}(\overline\Omega)
\hookrightarrow
C^{m,1}(\overline\Omega).
$$

再结合

$$
C^{m,1}(\overline\Omega)
\hookrightarrow
C^{m,\lambda}(\overline\Omega),
$$

得到

$$
C^{m+1}(\overline\Omega)
\hookrightarrow
C^{m,\lambda}(\overline\Omega).
$$

### 四、$\Omega$ 同时凸且有界时

有紧嵌入

$$
C^{m+1}(\overline\Omega)
\hookrightarrow\hookrightarrow
C^m(\overline\Omega).
$$

当 $0<\lambda<1$ 时，还有

$$
C^{m+1}(\overline\Omega)
\hookrightarrow\hookrightarrow
C^{m,\lambda}(\overline\Omega).
$$

这里不能把最后的 $\lambda<1$ 随意改成 $\lambda=1$。有界的 $C^{m+1}$ 序列虽然在 $C^{m,1}$ 中有界，但不一定在同一个 Lipschitz 范数中具有强收敛子列；降低一点 Hölder 指数才获得紧性。

### 1.34 的核心逻辑

可以浓缩为：

$$
\text{多一阶连续导数}
\Longrightarrow
\text{低阶导数 Lipschitz 连续}
\Longrightarrow
\text{低阶导数 Hölder 连续}.
$$

如果区域有界，再配合 Ascoli-Arzelà 定理，就能把连续嵌入升级为紧嵌入。

---

# 第三部分：整章逻辑串联

## 1. 为什么 1.10-1.23 要讲这些抽象空间？

Sobolev 空间 $W^{m,p}(\Omega)$ 可以通过映射

$$
u\longmapsto(D^\alpha u)_{|\alpha|\le m}
$$

放进有限个 $L^p(\Omega)$ 的乘积空间。

于是：

- $L^p$ 是 Banach，乘积空间也是 Banach；
- 若 Sobolev 空间的像是闭子空间，则 $W^{m,p}$ 也是 Banach；
- 当 $1<p<\infty$ 时，$L^p$ 一致凸、自反，有限乘积和闭子空间继承这些性质；
- 因而 $W^{m,p}$ 中的有界序列可以提取弱收敛子列。

这就是抽象泛函分析定理在 Sobolev 理论中的用途。

## 2. 为什么 1.24-1.34 要讲嵌入和紧性？

弱收敛对线性问题很好用，但处理非线性项时往往不够。例如

$$
u_n\rightharpoonup u
$$

通常不能直接推出

$$
u_n^2\rightharpoonup u^2.
$$

如果通过紧嵌入得到某个较弱空间中的强收敛，非线性极限就更容易处理。

所以 PDE 存在性证明常见结构是：

$$
\text{先验估计}
\Longrightarrow
\text{有界序列}
\Longrightarrow
\text{弱收敛子列}
\Longrightarrow
\text{紧嵌入给出强收敛}
\Longrightarrow
\text{通过非线性项并得到解}.
$$

---

# 第四部分：最容易混淆的概念

## 1. Banach 与 Hilbert

$$
\text{Hilbert}=\text{内积诱导范数}+\text{完备},
$$

$$
\text{Banach}=\text{范数}+\text{完备}.
$$

Hilbert 一定是 Banach；Banach 不一定是 Hilbert。

## 2. 弱收敛与范数收敛

$$
x_n\to x
\Longrightarrow
x_n\rightharpoonup x,
$$

反向一般不成立。

## 3. 有界、预紧与紧

- 有界：一个大球能覆盖；
- 预紧：任意小尺度都能用有限多个球覆盖，闭包紧；
- 紧：每个序列都有收敛到集合内点的子列。

## 4. 连续嵌入与紧嵌入

- 连续嵌入：$X$ 范数控制 $Y$ 范数；
- 紧嵌入：$X$ 中有界序列在 $Y$ 中有强收敛子列。

## 5. 一致连续与等度连续

- 一致连续针对一个函数；
- 等度连续针对整个函数族，同一个 $\delta$ 要适用于所有函数。

## 6. $C^m$ 与 $C^{m,\lambda}$

- $C^m$：直到 $m$ 阶导数连续；
- $C^{m,\lambda}$：还定量控制这些导数的振荡速度；
- $\lambda$ 越大，正则性越强。

---

# 第五部分：本节必须记住的十条结论

1. Hilbert 空间是完备的内积空间。
2. 范数来自内积，当且仅当满足平行四边形恒等式。
3. 对偶空间 $X'$ 总是 Banach，即使 $X$ 不完备。
4. Hilbert 空间中的连续线性泛函都由内积唯一表示。
5. Hahn-Banach 定理可以保持范数地延拓线性泛函。
6. 自反 Banach 空间中的有界序列都有弱收敛子列。
7. 一致凸 Banach 空间一定自反。
8. 预紧等价于对每个 $\varepsilon>0$ 存在有限 $\varepsilon$-网。
9. 紧嵌入意味着有界序列在较弱空间中具有强收敛子列。
10. Ascoli-Arzelà 定理用“一致有界+等度连续”产生一致收敛子列。

---

# 第六部分：建议复习顺序

第一次复习先掌握：

$$
1.10, 1.11, 1.12, 1.14, 1.16, 1.17, 1.18, 1.24, 1.25.
$$

它们组成“Hilbert—对偶—自反—弱收敛—紧性—嵌入”的骨架。

第二次复习再掌握：

$$
1.19-1.23,\qquad 1.26-1.34.
$$

重点理解有限 $\varepsilon$-网、一致凸性、连续函数空间、Hölder 空间和 Ascoli-Arzelà 定理。

最后尝试不看笔记说出下面这条完整逻辑：

$$
\boxed{
\text{有界性}
\overset{\text{自反性}}{\Longrightarrow}
\text{弱收敛子列}
\overset{\text{紧嵌入}}{\Longrightarrow}
\text{较弱空间中的强收敛子列}.
}
$$

理解这条逻辑，就抓住了本节课对后续 Sobolev 空间和 PDE 最重要的贡献。

