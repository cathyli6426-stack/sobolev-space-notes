# Sobolev 空间第三课复盘：教材 1.29-1.59

教材：Robert A. Adams 与 John J. F. Fournier，*Sobolev Spaces*（第二版）
本节主线：Hölder 空间与紧嵌入、Lebesgue 测度与积分、测试函数与分布

---

## 0. 本节课的整体结构

本节课内容可以分成三组。

### 第一组：连续函数空间与紧嵌入

$$
C^{m,\lambda}(\overline\Omega)
\longrightarrow
C^{m,\nu}(\overline\Omega)
\longrightarrow
C^m(\overline\Omega),
\qquad 0<\nu<\lambda\le1.
$$

核心问题是：正则性更强的函数空间能否连续地、甚至紧地嵌入正则性较弱的空间？

### 第二组：Lebesgue 测度与积分

$$
\sigma\text{-代数}
\longrightarrow
\text{测度}
\longrightarrow
\text{可测函数}
\longrightarrow
\text{Lebesgue 积分}
\longrightarrow
\text{积分与极限交换}.
$$

### 第三组：测试函数与分布

$$
\mathcal D(\Omega)=C_c^\infty(\Omega)
\longrightarrow
\mathcal D'(\Omega)
\longrightarrow
\text{弱导数与 Sobolev 空间}.
$$

这三部分共同服务于 Sobolev 理论：先确定函数空间，再建立积分工具，最后把经典导数推广为分布导数。

---

# 第一部分：Hölder 空间与紧嵌入

## 1.29 Hölder 连续函数空间

设 $m$ 是非负整数，$0<\lambda\le1$。若 $u\in C^m(\overline\Omega)$，并且对每个 $|\alpha|\le m$，存在常数 $K$ 使

$$
|D^\alpha u(x)-D^\alpha u(y)|
\le K|x-y|^\lambda,
\qquad x,y\in\Omega,
$$

则称 $u$ 属于 Hölder 空间 $C^{m,\lambda}(\overline\Omega)$。

### Hölder 半范数

对函数 $v$ 定义

$$
[v]_{C^{0,\lambda}(\overline\Omega)}
=
\sup_{\substack{x,y\in\Omega\\x\ne y}}
\frac{|v(x)-v(y)|}{|x-y|^\lambda}.
$$

于是可以把 $C^{m,\lambda}$ 范数写成

$$
\boxed{
\|u\|_{C^{m,\lambda}(\overline\Omega)}
=
\|u\|_{C^m(\overline\Omega)}
+
\max_{|\alpha|\le m}
[D^\alpha u]_{C^{0,\lambda}(\overline\Omega)}.
}
$$

第一项控制函数及其导数的大小，第二项控制它们的振荡速度。$C^{m,\lambda}(\overline\Omega)$ 在这个范数下是 Banach 空间。

### $\lambda=1$ 的含义

当 $\lambda=1$ 时，Hölder 条件变为

$$
|v(x)-v(y)|\le K|x-y|,
$$

这就是 Lipschitz 连续。因此 $C^{m,1}$ 是最高阶导数具有 Lipschitz 控制的空间。

### 例子：$u(x)=x^\alpha$

在 $[0,1]$ 上，当 $0<\alpha\le1$ 时，

$$
|x^\alpha-y^\alpha|\le|x-y|^\alpha,
$$

所以

$$
x^\alpha\in C^{0,\alpha}([0,1]).
$$

如果 $\beta>\alpha$，令 $y=0$，则

$$
\frac{|x^\alpha-0|}{|x-0|^\beta}
=x^{\alpha-\beta}\to\infty
\qquad(x\downarrow0),
$$

因此 $x^\alpha\notin C^{0,\beta}([0,1])$。这说明 Hölder 指数越大，要求越强。

### 空间之间的包含关系

若 $0<\nu<\lambda\le1$，则

$$
C^{m,\lambda}(\overline\Omega)
\subset
C^{m,\nu}(\overline\Omega)
\subset
C^m(\overline\Omega).
$$

一般而言这些包含都是严格的。

---

## 1.30 两个后续定理的作用

当 $\Omega$ 有界时，$\overline\Omega$ 是紧集。接下来的两个定理分别解决：

- Stone–Weierstrass 定理：什么函数族在 $C(\overline\Omega)$ 中稠密？
- Ascoli–Arzelà 定理：什么函数族在 $C(\overline\Omega)$ 中预紧？

“稠密”用于逼近，“预紧”用于提取强收敛子列。

---

## 1.31 Stone–Weierstrass 定理

设 $\Omega\subset\mathbb R^n$ 有界，$\mathcal A\subset C(\overline\Omega)$。若：

1. $\mathcal A$ 对加法、乘法和数乘封闭；
2. 若 $u\in\mathcal A$，则复共轭 $\overline u\in\mathcal A$；
3. $\mathcal A$ 能分离点：若 $x\ne y$，存在 $u\in\mathcal A$ 使 $u(x)\ne u(y)$；
4. 对每个 $x\in\overline\Omega$，存在 $u\in\mathcal A$ 使 $u(x)\ne0$；

则 $\mathcal A$ 在一致范数下稠密于 $C(\overline\Omega)$。

也就是说，对任意 $f\in C(\overline\Omega)$ 和 $\varepsilon>0$，存在 $u\in\mathcal A$ 使

$$
\|f-u\|_\infty<\varepsilon.
$$

---

## 1.32 $C(\overline\Omega)$ 的可分性

设 $P$ 是所有具有有理复系数的多项式组成的集合。有理复数形如

$$
a+ib,
\qquad a,b\in\mathbb Q.
$$

由 Stone–Weierstrass 定理，多项式在 $C(\overline\Omega)$ 中稠密。任意复系数多项式又能被有理复系数多项式一致逼近，所以 $P$ 仍然稠密。

另一方面：

- 单项式只有可数多个；
- 有理复数集合可数；
- 每个多项式只有有限项。

因此 $P$ 是可数稠密集，从而

$$
\boxed{C(\overline\Omega)\text{ 是可分空间}.}
$$

---

## 1.33 Ascoli–Arzelà 定理

设 $\Omega$ 有界，$K\subset C(\overline\Omega)$。若 $K$ 满足下面两个条件，则 $K$ 在 $C(\overline\Omega)$ 中预紧。

### 条件一：一致有界

存在同一个常数 $M>0$，使

$$
|u(x)|\le M,
\qquad u\in K, x\in\overline\Omega.
$$

### 条件二：等度连续

对每个 $\varepsilon>0$，存在 $\delta>0$，使得对所有 $u\in K$，只要 $|x-y|<\delta$，就有

$$
|u(x)-u(y)|<\varepsilon.
$$

这里的关键是：同一个 $M$ 和同一个 $\delta$ 必须对整个函数族同时有效。

### 序列语言

任取 $(u_j)\subset K$，都存在一个子列 $(u_{j_k})$ 和 $u\in C(\overline\Omega)$，使

$$
\|u_{j_k}-u\|_\infty\to0.
$$

这一定理把“统一控制函数的大小和振荡”转化成“一致收敛子列”。它是定理 1.34 中所有紧嵌入的核心工具。

---

## 1.34 连续嵌入与紧嵌入定理（本节重点）

设 $m\ge0$，并且

$$
0<\nu<\lambda\le1.
$$

### 1. 两种嵌入的区别

写作

$$
X\hookrightarrow Y
$$

表示连续嵌入：$X\subset Y$，并且存在 $C>0$ 使

$$
\|u\|_Y\le C\|u\|_X.
$$

写作

$$
X\hookrightarrow\hookrightarrow Y
$$

表示紧嵌入：$X$ 中每个有界序列都能选出一个在 $Y$ 中强收敛的子列。

紧嵌入比连续嵌入强得多：连续嵌入只传递估计，紧嵌入还能制造强收敛子列。

### 2. 定理的全部结论

总有连续嵌入

$$
C^{m+1}(\overline\Omega)
\hookrightarrow
C^m(\overline\Omega),
\qquad\text{(3)}
$$

$$
C^{m,\nu}(\overline\Omega)
\hookrightarrow
C^m(\overline\Omega),
\qquad\text{(4)}
$$

$$
C^{m,\lambda}(\overline\Omega)
\hookrightarrow
C^{m,\nu}(\overline\Omega).
\qquad\text{(5)}
$$

若 $\Omega$ 有界，则 (4)、(5) 是紧嵌入。

若 $\Omega$ 凸，则还有连续嵌入

$$
C^{m+1}(\overline\Omega)
\hookrightarrow
C^{m,1}(\overline\Omega),
\qquad\text{(6)}
$$

$$
C^{m+1}(\overline\Omega)
\hookrightarrow
C^{m,\lambda}(\overline\Omega).
\qquad\text{(7)}
$$

若 $\Omega$ 同时有界且凸，则 (3) 是紧嵌入；当 $\lambda<1$ 时，(7) 也是紧嵌入。

### 3. (3)、(4) 为什么连续？

直接比较范数：

$$
\|u\|_{C^m}
\le
\|u\|_{C^{m+1}},
$$

以及

$$
\|u\|_{C^m}
\le
\|u\|_{C^{m,\nu}}.
$$

所以 (3)、(4) 立即成立。

### 4. (5) 为什么连续？

固定 $|\alpha|\le m$。将点对分成两种情况。

若 $0<|x-y|<1$，则因为 $\lambda>\nu$，

$$
|x-y|^{\lambda-\nu}\le1,
$$

所以

$$
\frac{|D^\alpha u(x)-D^\alpha u(y)|}{|x-y|^\nu}
\le
[D^\alpha u]_{C^{0,\lambda}}.
$$

若 $|x-y|\ge1$，则

$$
\frac{|D^\alpha u(x)-D^\alpha u(y)|}{|x-y|^\nu}
\le
2\|D^\alpha u\|_\infty.
$$

因此

$$
\|u\|_{C^{m,\nu}}
\le C\|u\|_{C^{m,\lambda}},
$$

从而 (5) 连续。

### 5. (6) 为什么需要凸性？

设 $\Omega$ 凸。对任意 $x,y\in\Omega$，线段

$$
y+t(x-y),
\qquad 0\le t\le1,
$$

全部位于 $\Omega$ 内。于是对 $|\alpha|\le m$，沿线段使用微积分基本定理：

$$
\begin{aligned}
D^\alpha u(x)-D^\alpha u(y)
&=
\int_0^1
\nabla D^\alpha u\bigl(y+t(x-y)\bigr)
\cdot(x-y)\,dt.
\end{aligned}
$$

所以

$$
|D^\alpha u(x)-D^\alpha u(y)|
\le
C_n|x-y|\|u\|_{C^{m+1}},
$$

其中 $C_n$ 只依赖维数。于是

$$
\|u\|_{C^{m,1}}
\le C\|u\|_{C^{m+1}}.
$$

这就证明了 (6)。再将 (6) 与

$$
C^{m,1}\hookrightarrow C^{m,\lambda}
$$

复合，即得到 (7)。

### 6. (4) 为什么在有界区域上是紧嵌入？

设 $(u_j)$ 在 $C^{m,\nu}(\overline\Omega)$ 中有界，即

$$
\|u_j\|_{C^{m,\nu}}\le M.
$$

对每个 $|\alpha|\le m$，函数族 $(D^\alpha u_j)$ 都满足：

$$
\|D^\alpha u_j\|_\infty\le M,
$$

以及

$$
|D^\alpha u_j(x)-D^\alpha u_j(y)|
\le M|x-y|^\nu.
$$

所以它们一致有界且等度连续。由 Ascoli–Arzelà 定理，对每个 $\alpha$ 都可以抽取一致收敛子列。

满足 $|\alpha|\le m$ 的多重指标只有有限多个，因此反复抽取后，可以得到同一个子列 $(u_{j_k})$，使

$$
D^\alpha u_{j_k}
\longrightarrow v_\alpha
\quad\text{在 }C(\overline\Omega)\text{ 中},
\qquad |\alpha|\le m.
$$

特别地，$u_{j_k}\to u$ 一致。由“函数及其导数都一致收敛”的标准结论，极限满足

$$
v_\alpha=D^\alpha u.
$$

于是

$$
\|u_{j_k}-u\|_{C^m}\to0.
$$

因此

$$
\boxed{
C^{m,\nu}(\overline\Omega)
\hookrightarrow\hookrightarrow
C^m(\overline\Omega).
}
$$

### 7.  Hölder 插值估计

这是证明 (5) 为紧嵌入的关键：

令 $0<\nu<\lambda\le1$，并设

$$
\theta=\frac{\nu}{\lambda}\in(0,1).
$$

对任意函数 $v$，有恒等变形

$$
\begin{aligned}
\frac{|v(x)-v(y)|}{|x-y|^\nu}
&=
\left(
\frac{|v(x)-v(y)|}{|x-y|^\lambda}
\right)^{\nu/\lambda}
|v(x)-v(y)|^{1-\nu/\lambda}.
\end{aligned}
$$

第一部分由 $\lambda$-Hölder 半范数控制，第二部分满足

$$
|v(x)-v(y)|
\le2\|v\|_\infty.
$$

因此

$$
\boxed{
[v]_{C^{0,\nu}}
\le
2^{1-\theta}
[v]_{C^{0,\lambda}}^\theta
\|v\|_\infty^{1-\theta},
\qquad
\theta=\frac{\nu}{\lambda}.
}
$$

它体现了“中间正则性可以由高阶正则性和低阶大小共同控制”：

$$
C^{0,\nu}
\quad\text{位于}\quad
C^{0,\lambda}
\quad\text{和}\quad
C^0
\quad\text{之间}.
$$

对所有 $|\alpha|\le m$ 应用该估计，就得到相应的 $C^{m,\nu}$ 插值控制。

### 8. 用插值估计证明 (5) 的紧性

设 $(u_j)$ 在 $C^{m,\lambda}$ 中有界。由刚证明的

$$
C^{m,\lambda}
\hookrightarrow\hookrightarrow
C^m,
$$

可以选出子列，仍记为 $(u_j)$，使其在 $C^m$ 中收敛。特别地，它在 $C^m$ 中是 Cauchy 列：

$$
\|u_j-u_k\|_{C^m}\to0
\qquad(j,k\to\infty).
$$

令

$$
w_{j,k}=u_j-u_k.
$$

由于 $(u_j)$ 在 $C^{m,\lambda}$ 中有界，存在 $M>0$ 使

$$
[D^\alpha w_{j,k}]_{C^{0,\lambda}}
\le2M.
$$

插值估计给出

$$
[D^\alpha w_{j,k}]_{C^{0,\nu}}
\le
C(2M)^\theta
\|D^\alpha w_{j,k}\|_\infty^{1-\theta}.
$$

右端趋于零，因为 $u_j$ 在 $C^m$ 中是 Cauchy 列。因此

$$
\|u_j-u_k\|_{C^{m,\nu}}\to0.
$$

$C^{m,\nu}$ 是 Banach 空间，所以该子列在 $C^{m,\nu}$ 中收敛。这就证明

$$
\boxed{
C^{m,\lambda}(\overline\Omega)
\hookrightarrow\hookrightarrow
C^{m,\nu}(\overline\Omega).
}
$$

这一步不能只说“在 $C^m$ 中收敛，所以在 $C^{m,\nu}$ 中也收敛”。真正发挥作用的是：

$$
\text{高阶 Hölder 范数一致有界}
+
\text{低阶 }C^m\text{ 范数趋于零}
\Longrightarrow
\text{中间 Hölder 范数趋于零}.
$$

### 9. 紧嵌入的复合规则

若

$$
A\hookrightarrow B
$$

连续，并且

$$
B\hookrightarrow\hookrightarrow C
$$

紧，则

$$
A\hookrightarrow\hookrightarrow C.
$$

同样，若 $A\hookrightarrow\hookrightarrow B$ 紧而 $B\hookrightarrow C$ 连续，则 $A\hookrightarrow\hookrightarrow C$。

原因是：先在紧嵌入对应的空间中抽取收敛子列，再用连续嵌入把收敛传递到下一个空间。

因此，当 $\Omega$ 有界且凸时，

$$
C^{m+1}
\hookrightarrow
C^{m,1}
\hookrightarrow\hookrightarrow
C^m,
$$

从而 (3) 紧；当 $\lambda<1$ 时，

$$
C^{m+1}
\hookrightarrow
C^{m,1}
\hookrightarrow\hookrightarrow
C^{m,\lambda},
$$

从而 (7) 紧。

### 10. 为什么端点嵌入 (6) 一般不紧？

在区间 $(0,2\pi)$ 上取

$$
u_n(x)=\frac{\sin(nx)}{n}.
$$

则 $(u_n)$ 在 $C^1$ 中有界，因为

$$
\|u_n\|_\infty\le\frac1n,
\qquad
\|u_n'\|_\infty=1.
$$

而 $u_n\to0$ 一致，但

$$
[u_n]_{C^{0,1}}=\|u_n'\|_\infty=1.
$$

所以它不可能有子列在 $C^{0,1}$ 中收敛。这说明

$$
C^1\hookrightarrow C^{0,1}
$$

一般只是连续嵌入，不是紧嵌入。紧性通常需要损失一点正则性，例如嵌入到 $C^{0,\lambda}$，其中 $\lambda<1$。

---

## 1.35 对区域几何条件的放宽

凸性只是一个方便使用的充分条件，并非必要条件。若 $\Omega$ 中任意两点都可以由一条位于 $\Omega$ 内的可求长曲线连接，并且曲线长度不超过

$$
C|x-y|,
$$

那么仍能沿曲线积分，得到类似于 (6) 的估计。因此某些非凸区域上也成立相同的连续嵌入与紧嵌入结论。

---

# 第二部分：Lebesgue 测度与积分

## 1.36 为什么要回顾 Lebesgue 理论？

Sobolev 空间的元素通常只是可积函数的等价类，其导数也只在弱意义下存在。因此后续必须使用：

- Lebesgue 测度；
- 几乎处处成立；
- 可测函数与 $L^p$ 空间；
- 极限和积分交换；
- 多重积分换序。

---

## 1.37 $\sigma$-代数

集合族 $\Sigma\subset2^{\mathbb R^n}$ 称为 $\sigma$-代数，如果：

1. $\mathbb R^n\in\Sigma$；
2. $A\in\Sigma$ 蕴含 $A^c\in\Sigma$；
3. 若 $A_j\in\Sigma$，则 $\bigcup_{j=1}^\infty A_j\in\Sigma$。

由此还可推出：

$$
\varnothing\in\Sigma,
\qquad
\bigcap_{j=1}^\infty A_j\in\Sigma,
\qquad
A-B=A\cap B^c\in\Sigma.
$$

$\sigma$-代数就是允许我们进行测量的集合系统。

---

## 1.38 测度

正测度是映射

$$
\mu:\Sigma\to[0,+\infty],
$$

并满足可列可加性：若 $A_j$ 两两不交，则

$$
\mu\left(\bigcup_{j=1}^\infty A_j\right)
=
\sum_{j=1}^\infty\mu(A_j).
$$

正测度还具有单调性：若 $A\subset B$，则

$$
\mu(A)\le\mu(B).
$$

若 $A_1\subset A_2\subset\cdots$，则

$$
\mu\left(\bigcup_{j=1}^\infty A_j\right)
=
\lim_{j\to\infty}\mu(A_j).
$$

---

## 1.39 Lebesgue 测度的存在

$\mathbb R^n$ 上存在一个 $\sigma$-代数 $\Sigma$ 和正测度 $\mu$，满足：

1. 所有开集均可测；
2. 零测集的任意子集也可测且测度为零；
3. 长方体
   
   $$
   A=\prod_{j=1}^n[a_j,b_j]
   $$
   
   的测度为
   
   $$
   \mu(A)=\prod_{j=1}^n(b_j-a_j);
   $$
4. 平移不改变测度：
   
   $$
   \mu(x+A)=\mu(A).
   $$

这个测度就是 Lebesgue 测度。

---

## 1.40 几乎处处

若某性质在 $A-B$ 上成立，并且

$$
\mu(B)=0,
$$

则称该性质在 $A$ 上几乎处处成立，简写为 a.e.

在 $L^p$ 空间中，相差仅为零测集的两个函数被视为同一个元素。

---

## 1.41 可测函数

定义在可测集上的函数 $f$ 称为可测函数，如果对每个 $a\in\mathbb R$，集合

$$
\{x:f(x)>a\}
$$

都是可测集。

直观上，可测性保证函数的各个“高度层”能够被测量，从而可以定义积分。

---

## 1.42 可测函数的基本性质

需要记住：

- $f$ 可测则 $|f|$ 可测；
- $f,g$ 可测则 $f+g$、$fg$ 可测；
- 可测函数列的上确界、下确界、上极限和下极限可测；
- 连续函数可测；
- 连续函数与可测函数的复合仍可测。

Lusin 定理大意是：有限测度集上的可测函数，除去任意小测度的坏集合后，可以表现得像连续函数。

---

## 1.43 特征函数与简单函数

集合 $A$ 的特征函数定义为

$$
\chi_A(x)=
\begin{cases}
1,&x\in A,\\
0,&x\notin A.
\end{cases}
$$

只取有限多个值的函数称为简单函数。它可以写成

$$
s(x)=\sum_{j=1}^m a_j\chi_{A_j}(x).
$$

若各 $A_j$ 可测，则 $s$ 可测。简单函数是 Lebesgue 积分的基础积木。

---

## 1.44 用简单函数逼近一般函数

任意实值函数都可以由简单函数列逐点逼近。进一步：

- 若 $f$ 有界，可以选择简单函数列一致收敛到 $f$；
- 若 $f$ 可测，可以选择可测简单函数；
- 若 $f\ge0$ 且可测，可以选择
  
  $$
  0\le s_1\le s_2\le\cdots\uparrow f.
  $$

最后一条正是单调收敛定理的基础。

---

## 1.45 Lebesgue 积分的定义

### 简单函数

若

$$
s=\sum_{j=1}^m a_j\chi_{A_j},
$$

则定义

$$
\int_A s(x)\,dx
=
\sum_{j=1}^m a_j\mu(A_j).
$$

### 非负可测函数

若 $f\ge0$，则定义

$$
\int_A f(x)\,dx
=
\sup\left\{
\int_A s(x)\,dx:
0\le s\le f, s\text{ 为可测简单函数}
\right\}.
$$

### 一般实值函数

写成

$$
f=f^+-f^-,
$$

其中

$$
f^+=\max\{f,0\},
\qquad
f^-=\max\{-f,0\}.
$$

若

$$
\int_A f^+<\infty,
\qquad
\int_A f^-<\infty,
$$

则称 $f$ 可积，并定义

$$
\int_A f
=
\int_A f^+-\int_A f^-.
$$

等价地，

$$
f\in L^1(A)
\quad\Longleftrightarrow\quad
\int_A|f(x)|\,dx<\infty.
$$

---

## 1.46 Lebesgue 积分的基本性质

在相应积分存在时：

1. 有界函数在有限测度集上可积；
2. 若 $a\le f\le b$，则
   
   $$
   a\mu(A)
   \le
   \int_Af
   \le
   b\mu(A);
   $$
3. $f\le g$ 蕴含 $\int_Af\le\int_Ag$；
4. 积分具有线性；
5. 有估计
   
   $$
   \left|\int_Af\right|
   \le
   \int_A|f|;
   $$
6. 若 $B\subset A$ 且 $f\ge0$，则 $\int_Bf\le\int_Af$；
7. 零测集上的积分等于零。

如果 $f=g$ a.e.，则

$$
\int_Af=\int_Ag.
$$

这也是为什么 $L^1$ 的元素严格说是“几乎处处相等”的函数等价类。

---

## 1.47 可积函数产生测度

若 $f\in L^1(\mathbb R^n)$，或 $f\ge0$ 可测，则

$$
\lambda(A)=\int_Af(x)\,dx
$$

关于集合 $A$ 是可列可加的，因此定义了一个测度。

这说明函数可以充当相对于 Lebesgue 测度的“密度”。1.52 的 Radon–Nikodym 定理将在适当条件下给出反方向。

---

## 1.48 单调收敛定理

若 $f_j$ 是非负可测函数，并且

$$
0\le f_1(x)\le f_2(x)\le\cdots,
$$

则

$$
\boxed{
\lim_{j\to\infty}\int_Af_j(x)\,dx
=
\int_A\left(\lim_{j\to\infty}f_j(x)\right)dx.
}
$$

它允许在“非负且单调增加”的条件下交换极限与积分，不需要统一的可积控制函数。

---

## 1.49 Fatou 引理

若 $f_j\ge0$ 可测，则

$$
\boxed{
\int_A\liminf_{j\to\infty}f_j(x)\,dx
\le
\liminf_{j\to\infty}\int_Af_j(x)\,dx.
}
$$

Fatou 引理只给出一个方向的不等式。它常用于证明范数和能量的下半连续性。

---

## 1.50 控制收敛定理（重点）

设 $f_j$ 可测，并且

$$
f_j(x)\to f(x)
$$

逐点成立。若存在同一个 $g\in L^1(A)$，使对所有 $j$ 都有

$$
|f_j(x)|\le g(x),
$$

则 $f\in L^1(A)$，并且

$$
\boxed{
\lim_{j\to\infty}\int_Af_j(x)\,dx
=
\int_Af(x)\,dx.
}
$$

事实上还能得到更强的结论：

$$
\int_A|f_j-f|\,dx\to0,
$$

即 $f_j\to f$ 在 $L^1(A)$ 中强收敛。

### 使用时必须检查的三件事

1. $f_j\to f$ 逐点或几乎处处；
2. 存在一个与 $j$ 无关的控制函数 $g$；
3. $g$ 必须可积。

仅仅知道每个 $f_j$ 可积，并不足以交换极限与积分。

---

## 1.51 复值函数的积分

若

$$
f=u+iv,
$$

其中 $u,v$ 为实值函数，则 $f$ 可积当且仅当 $|f|\in L^1$，也等价于 $u,v\in L^1$。定义

$$
\int_Af
=
\int_Au+i\int_Av.
$$

前面的线性、绝对值估计和控制收敛定理都可以推广到复值函数。

---

## 1.52 Radon–Nikodym 定理（重点）

设 $\lambda$ 是定义在 Lebesgue 可测集上的复测度。如果

$$
\mu(A)=0
\quad\Longrightarrow\quad
\lambda(A)=0,
$$

则称 $\lambda$ 关于 Lebesgue 测度 $\mu$ 绝对连续，记作

$$
\lambda\ll\mu.
$$

Radon–Nikodym 定理说明：存在 $f\in L^1(\mathbb R^n)$，使对每个可测集 $A$，

$$
\boxed{
\lambda(A)=\int_Af(x)\,dx.
}
$$

并且 $f$ 在几乎处处相等的意义下唯一。记作

$$
f=\frac{d\lambda}{d\mu},
$$

称为 $\lambda$ 关于 $\mu$ 的 Radon–Nikodym 导数或密度。

1.47 说“函数 $f$ 可以生成测度”，1.52 说“绝对连续的测度必定来自某个密度函数”。两者正好互为正反方向。

---

## 1.53 多变量积分记号

若 $x\in\mathbb R^n$、$y\in\mathbb R^m$，则可以写

$$
\int_Af(x,y)\,dx\,dy.
$$

也可以利用特征函数把区域积分改写为全空间积分：

$$
\int_Af(x,y)\,dx\,dy
=
\int_{\mathbb R^{n+m}}f(x,y)\chi_A(x,y)\,dx\,dy.
$$

---

## 1.54 Fubini 定理（重点）

设 $f$ 是 $\mathbb R^{n+m}$ 上的可测函数。如果

$$
\int_{\mathbb R^{n+m}}|f(x,y)|\,dx\,dy<\infty,
$$

则几乎对每个固定的 $y$，函数 $x\mapsto f(x,y)$ 可积；几乎对每个固定的 $x$，函数 $y\mapsto f(x,y)$ 可积，并且

$$
\boxed{
\int_{\mathbb R^{n+m}}f(x,y)\,dx\,dy
=
\int_{\mathbb R^m}
\left(\int_{\mathbb R^n}f(x,y)\,dx\right)dy
=
\int_{\mathbb R^n}
\left(\int_{\mathbb R^m}f(x,y)\,dy\right)dx.
}
$$

因此在绝对可积条件下，可以交换积分顺序。

若 $f\ge0$，即使积分可能是 $+\infty$，仍可用 Tonelli 定理交换积分顺序。实际计算中应先检查“非负”或“绝对可积”中的至少一种条件。

---

# 第三部分：测试函数与分布

## 1.55 为什么要引入分布？

经典导数要求函数足够光滑，但 Sobolev 空间希望容纳不光滑函数。例如 $|x|$ 在 $0$ 点没有经典导数，却仍然存在合理的弱导数。

分布理论的思路是：不直接逐点观察函数，而是让它作用在一批非常光滑、支集紧的测试函数上。

---

## 1.56 测试函数空间 $\mathcal D(\Omega)$（重点）

定义

$$
\mathcal D(\Omega)
=
C_c^\infty(\Omega).
$$

也就是说，$\varphi\in\mathcal D(\Omega)$ 必须同时满足：

- $\varphi$ 无限次可微；
- $\varphi$ 的支集是 $\Omega$ 内的紧集。

### 在 $\mathcal D(\Omega)$ 中怎样收敛？

称

$$
\varphi_j\to\varphi
\quad\text{in }\mathcal D(\Omega),
$$

如果满足两个条件。

第一，存在同一个紧集

$$
K\Subset\Omega
$$

使得对所有 $j$，

$$
\mathrm{supp}(\varphi_j-\varphi)\subset K.
$$

这里 $K\Subset\Omega$ 表示 $K$ 是 $\Omega$ 内部的紧子集，与边界保持正距离。

第二，对每个多重指标 $\alpha$，

$$
D^\alpha\varphi_j
\to
D^\alpha\varphi
$$

在 $K$ 上一致收敛。

所以 $\mathcal D$ 收敛比普通的一致收敛强得多：不仅所有阶导数都要一致收敛，而且支集不能向边界或无穷远处逃走。 $\mathcal D(\Omega)$ 不是赋范空间；它的拓扑不能由单个范数完整描述。

---

## 1.57 Schwartz 分布（重点）

$\mathcal D(\Omega)$ 的连续对偶空间记为

$$
\mathcal D'(\Omega),
$$

其元素称为 Schwartz 分布。

换句话说，分布 $T$ 是一个映射

$$
T:\mathcal D(\Omega)\to\mathbb C,
$$

并满足：

1. 线性；
2. 对 $\mathcal D$ 的收敛连续，即
   
   $$
   \varphi_j\to\varphi\text{ in }\mathcal D(\Omega)
   \quad\Longrightarrow\quad
   T(\varphi_j)\to T(\varphi).
   $$

分布不是必须逐点有值的函数。它只需要告诉我们：对每个测试函数 $\varphi$，数值 $T(\varphi)$ 是什么。

### 分布的收敛

称

$$
T_j\to T
\quad\text{in }\mathcal D'(\Omega),
$$

如果对所有 $\varphi\in\mathcal D(\Omega)$，都有

$$
T_j(\varphi)\to T(\varphi).
$$

这是一种逐个测试函数检验的弱星收敛。

---

## 1.58 局部可积函数产生分布

若对每个 $U\Subset\Omega$ 都有

$$
\int_U|u(x)|\,dx<\infty,
$$

则称 $u$ 局部可积，记为

$$
u\in L^1_{\mathrm{loc}}(\Omega).
$$

每个局部可积函数都定义一个分布：

$$
T_u(\varphi)
=
\int_\Omega u(x)\varphi(x)\,dx.
$$

为什么积分一定存在？因为 $\varphi$ 的支集包含在某个 $K\Subset\Omega$ 中，而 $u$ 在 $K$ 上可积。

### 连续性的验证

若 $\varphi_j\to\varphi$ in $\mathcal D(\Omega)$，并且所有差值的支集包含在同一紧集 $K$ 中，则

$$
\begin{aligned}
|T_u(\varphi_j)-T_u(\varphi)|
&\le
\sup_{x\in K}|\varphi_j(x)-\varphi(x)|
\int_K|u(x)|\,dx.
\end{aligned}
$$

第一项趋于零，第二项有限，所以

$$
T_u(\varphi_j)\to T_u(\varphi).
$$

因此 $T_u\in\mathcal D'(\Omega)$。这种由局部可积函数产生的分布称为正则分布。

---

## 1.59 不是所有分布都来自函数

若 $0\in\Omega$，定义 Dirac 分布

$$
\delta_0(\varphi)=\varphi(0).
$$

它是 $\mathcal D(\Omega)$ 上的连续线性泛函，因此

$$
\delta_0\in\mathcal D'(\Omega).
$$

但是不存在 $u\in L^1_{\mathrm{loc}}(\Omega)$ 使

$$
\int_\Omega u(x)\varphi(x)\,dx
=
\varphi(0)
$$

对所有测试函数都成立。

直观原因是：右边只读取单独一个点的值，而普通 Lebesgue 积分无法感受到单点，因为单点测度为零。

更严格地，可以选择支集不断缩向 $0$ 的测试函数 $\varphi_\varepsilon$，满足

$$
\varphi_\varepsilon(0)=1,
\qquad
|\varphi_\varepsilon|\le1.
$$

若 $u$ 局部可积，则

$$
\left|\int u\varphi_\varepsilon\right|
\le
\int_{B_\varepsilon(0)}|u(x)|\,dx
\to0,
$$

但

$$
\delta_0(\varphi_\varepsilon)=1.
$$

矛盾。因此 Dirac 分布不是正则分布。

---

# 4. 本节课的逻辑链

## 4.1 紧嵌入链

$$
\text{高阶正则性有界}
\overset{\text{Ascoli--Arzelà}}{\Longrightarrow}
\text{低阶空间中有收敛子列}
\overset{\text{插值估计}}{\Longrightarrow}
\text{中间 Hölder 空间中强收敛}.
$$

## 4.2 Lebesgue 积分链

$$
\text{简单函数}
\longrightarrow
\text{非负可测函数}
\longrightarrow
L^1\text{ 函数}
\longrightarrow
\text{极限与积分交换}.
$$

三个收敛工具的适用条件要分清：

| 定理 | 主要条件 | 结论形式 |
|---|---|---|
| 单调收敛 | $0\le f_j\uparrow f$ | 积分与极限相等 |
| Fatou 引理 | $f_j\ge0$ | 给出下极限不等式 |
| 控制收敛 | $f_j\to f$ 且 $|f_j|\le g\in L^1$ | 积分与极限相等，并有 $L^1$ 收敛 |

## 4.3 分布链

$$
u\in L^1_{\mathrm{loc}}(\Omega)
\Longrightarrow
T_u\in\mathcal D'(\Omega),
$$

但反方向不成立，因为

$$
\delta_0\in\mathcal D'(\Omega)
\quad\text{却不对应任何局部可积函数}.
$$

分布空间扩大了“函数”的范围。下一步定义分布导数后，每个分布都可以任意次求导，而 Sobolev 空间正是用这些弱导数来定义的。

