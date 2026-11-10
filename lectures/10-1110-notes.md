# 第十课复盘：Sobolev 空间、完备性、对偶与负阶空间（§§3.1–3.13）


## 0. 本节路线与符号约定

| 教材编号 | 主要问题 | 证明中最重要的工具 |
| --- | --- | --- |
| 3.1–3.2 | Sobolev 范数、三种空间如何定义？ | 弱导数、闭包、完备化 |
| 3.3–3.4 | 极限为什么仍有相应的弱导数？ | $L^p$ 完备性、Hölder 不等式、测试函数 |
| 3.5–3.6 | 可分性、自反性、一致凸性从哪里来？ | 等距嵌入、闭子空间 |
| 3.7–3.9 | Sobolev 空间上的连续线性泛函如何表示？ | Hahn–Banach、$L^p$ 对偶表示 |
| 3.10–3.11 | 泛函与分布是什么关系？为什么要使用 $W_0^{m,p}$？ | 分布导数、稠密延拓、边界信息 |
| 3.12–3.13 | 什么是负阶 Sobolev 空间与负阶范数？ | 对偶范数、最小表示、完备化 |

除特别说明外，约定如下。

- $\Omega\subset\mathbb R^n$ 是非空开集；本节核心结论不要求边界光滑。教材使用“域”时还包含连通性，但下面大多数证明不依赖连通性。
- $m\in\mathbb N$，$1\le p\le\infty$。**涉及教材 3.8–3.12 的对偶表示时，要求 $1\le p<\infty$。**
- 函数可以取实值或复值，按几乎处处相等识别为同一个元素。
- $C_c^\infty(\Omega)=\mathcal D(\Omega)$ 是光滑且紧支撑于 $\Omega$ 内的测试函数空间，教材也记作 $C_0^\infty(\Omega)$。
- $\|u\|_p$ 表示 $L^p(\Omega)$ 范数，$\|u\|_{m,p}$ 表示本节规定的 Sobolev 范数。
- $X'$ 表示赋范空间 $X$ 的连续线性对偶。分布空间 $\mathcal D'(\Omega)$ 中的撇号同样表示连续对偶，但其定义域采用测试函数拓扑。
- 共轭指数满足 $1/p+1/p'=1$，其中 $1'=\infty$，$\infty'=1$。

本节将两种配对分开写：

$$
\langle u,v\rangle=\int_\Omega u(x)v(x)\,dx
\quad\text{（对偶使用的双线性配对）},
$$

$$
(u,v)_{L^2}=\int_\Omega u(x)\overline{v(x)}\,dx
\quad\text{（Hilbert 空间内积）}.
$$

二者在复数情形下不同。采用教材的第一种约定时，泛函的系数中有时会出现共轭，不能随意删去。

## 1. 学习本节必须掌握的基础

### 1.1 为什么 $L^p$ 中的元素是等价类？

若 $u=v$ 几乎处处，则积分无法区分二者，且

$$
\|u-v\|_p=0.
$$

因此在 $L^p$ 中必须把它们视为同一个元素，否则范数的“零范数只对应零元素”就不成立。Sobolev 空间也沿用这一约定。

特别地，不能对一般 $L^p$ 元素直接谈“$u(x_0)$ 的值”。在一个点修改函数不会改变其 $L^p$ 元素，但会改变点值。要讨论边界值或点值，需要先证明存在合适的代表元，或者引入迹算子。

### 1.2 多重指标：把所有偏导数列清楚

设

$$
\alpha=(\alpha_1,\ldots,\alpha_n)\in\mathbb N_0^n,
\qquad |\alpha|=\alpha_1+\cdots+\alpha_n,
$$

定义

$$
D^\alpha=\partial_{x_1}^{\alpha_1}\cdots\partial_{x_n}^{\alpha_n},
\qquad D^0u=u.
$$

例如 $n=2,m=2$ 时，$|\alpha|\le2$ 对应

$$
u,\quad u_{x_1},\quad u_{x_2},\quad
u_{x_1x_1},\quad u_{x_1x_2},\quad u_{x_2x_2}.
$$

混合导数 $u_{x_1x_2}$ **只计一次**。一般地，这些多重指标的数量为

$$
N=N(n,m)=\binom{n+m}{m}.
$$

理由是引入 $\alpha_{n+1}=m-|\alpha|\ge0$，把计数化为 $n+1$ 个非负整数之和等于 $m$ 的解的个数。

### 1.3 为什么 $L^p$ 函数可以看成分布？

对紧集 $K\Subset\Omega$，Hölder 不等式给出

$$
\int_K|u|\,dx\le |K|^{1/p'}\|u\|_{L^p(\Omega)}
\quad(1\le p\le\infty).
$$

端点分别理解为 $\int_K|u|\le\|u\|_1$ 与 $\int_K|u|\le |K|\|u\|_\infty$。所以

$$
L^p(\Omega)\subset L^1_{\mathrm{loc}}(\Omega).
$$

每个 $u\in L^1_{\mathrm{loc}}(\Omega)$ 都诱导一个分布

$$
T_u(\varphi)=\int_\Omega u\varphi\,dx,
\qquad\varphi\in\mathcal D(\Omega).
$$

积分有限，是因为 $\varphi$ 有紧支撑且有界。若 $\varphi_j\to\varphi$ 于 $\mathcal D(\Omega)$，则差的支撑都包含于一个紧集 $K\Subset\Omega$，且 $\varphi_j-\varphi$ 一致趋于零，于是

$$
|T_u(\varphi_j)-T_u(\varphi)|
\le\|\varphi_j-\varphi\|_\infty\int_K|u|\,dx\to0.
$$

因此 $T_u$ 是连续线性泛函。

我们还要使用如下基本事实：

> 若 $f\in L^1_{\mathrm{loc}}(\Omega)$ 且 $\int_\Omega f\varphi=0$ 对所有 $\varphi\in C_c^\infty(\Omega)$ 成立，则 $f=0$ 几乎处处。

这称为测试函数分离局部可积函数的性质，也常作为变分基本引理使用。可以通过磨光证明：上述等式使 $f$ 的所有内部磨光为零，而磨光在局部 $L^1$ 中收敛到 $f$。

### 1.4 弱导数的定义与唯一性

设 $u,v\in L^1_{\mathrm{loc}}(\Omega)$。若

$$
\boxed{
\int_\Omega uD^\alpha\varphi\,dx
=(-1)^{|\alpha|}\int_\Omega v\varphi\,dx,
\qquad\forall\varphi\in C_c^\infty(\Omega),
}
$$

就称 $v$ 是 $u$ 的 $\alpha$ 阶弱导数，记作 $D^\alpha u=v$。

这个定义把对 $u$ 的求导转移到光滑测试函数上。测试函数在边界附近恒为零，因此在经典分部积分中不会产生边界项。

若 $v_1,v_2$ 都满足定义，则 $\int(v_1-v_2)\varphi=0$ 对所有测试函数成立，故 $v_1=v_2$ 几乎处处。因此弱导数是唯一的等价类。

分布导数则对任何分布都能定义：

$$
(D^\alpha T)(\varphi)=(-1)^{|\alpha|}T(D^\alpha\varphi).
$$

**每个分布都有任意阶分布导数，但这些导数不一定能由局部可积函数表示。** Sobolev 空间要求相应的分布导数恰好由 $L^p$ 函数表示，这是一项实质性限制。

### 1.5 例子：$|x|$ 有弱导数，却不处处经典可导

在 $(-1,1)$ 上令 $u(x)=|x|$。对测试函数分开在 $(-1,0)$、$(0,1)$ 上积分，得到

$$
\int_{-1}^1|x|\varphi'(x)\,dx
=-\int_{-1}^1\operatorname{sgn}(x)\varphi(x)\,dx.
$$

所以

$$
u'=\operatorname{sgn}(x)\quad\text{弱意义下},
\qquad u\in W^{1,p}(-1,1),\quad1\le p\le\infty.
$$

再次求分布导数则有

$$
u''=2\delta_0,
\qquad\delta_0(\varphi)=\varphi(0).
$$

Dirac 分布不能由局部可积函数表示。例如若 $T_f=\delta_0$，取 $0\le\eta\in C_c^\infty(-1,1)$、$\eta(0)=1$，令 $\eta_\varepsilon(x)=\eta(x/\varepsilon)$，则

$$
1=\delta_0(\eta_\varepsilon)
=\int f\eta_\varepsilon\to0,
$$

最后一步来自 $f$ 在零点附近可积以及积分的绝对连续性，矛盾。因此 $|x|\notin W^{2,p}(-1,1)$，$1\le p\le\infty$。

### 1.6 闭包、完备化与 Banach 空间

这三个概念要分开。

1. **Cauchy 列**：对每个 $\varepsilon>0$，存在 $N$，使 $j,k\ge N$ 时 $\|u_j-u_k\|<\varepsilon$。
2. **完备**：每个 Cauchy 列都在空间内部有范数极限。完备的赋范空间称为 Banach 空间。
3. **闭包** $\overline S^{,X}$：已经给定环境空间 $X$，取 $S$ 中序列在 $X$ 内的所有极限。
4. **完备化**：从可能不完备的空间 $S$ 出发，加入“缺失的 Cauchy 列极限”。严格构造可以使用 Cauchy 列的等价类。

两个常用结论：

- Banach 空间的闭线性子空间仍是 Banach 空间。
- 若 $S$ 等距嵌入 Banach 空间 $X$，则 $S$ 的完备化可等距识别为 $\overline S^{,X}$。

第二条正是教材 3.4 的逻辑依据。

## 2. §§3.1–3.2：Sobolev 范数与三种空间

### 2.1 Sobolev 范数

对 $1\le p<\infty$，定义

$$
\boxed{
\|u\|_{m,p}
=\left(\sum_{|\alpha|\le m}\|D^\alpha u\|_p^p\right)^{1/p}.
}
$$

对 $p=\infty$，定义

$$
\boxed{
\|u\|_{m,\infty}
=\max_{|\alpha|\le m}\|D^\alpha u\|_\infty.
}
$$

这测量的是“函数本身以及直到 $m$ 阶的全部弱导数”的大小。

例如

$$
\|u\|_{1,p}^p=\|u\|_p^p+\sum_{j=1}^n\|\partial_j u\|_p^p,
\qquad1\le p<\infty.
$$

注意，若用梯度的欧氏长度定义 $\|\nabla u\|_p$，一般只能说相应范数与上式等价；$p=2$ 时一阶公式才直接一致。二阶时，把 Hessian 全部矩阵项相加会把混合导数计两次，也不能直接当成本书相同的范数。

**为何它是范数？**

- 非负性显然。
- 若 $\|u\|_{m,p}=0$，则零阶项给出 $\|u\|_p=0$，故 $u=0$ 作为等价类。
- 弱导数线性，故 $\|cu\|_{m,p}=|c|\|u\|_{m,p}$。
- 对有限 $p$，先对每个分量使用 $L^p$ 三角不等式，再对有限数列使用 $\ell^p$ 三角不等式，得到

$$
\|u+v\|_{m,p}\le\|u\|_{m,p}+\|v\|_{m,p}.
$$

当 $p=\infty$，对各分量取最大值即可。

### 2.2 等价范数与最高阶半范数

当 $1\le p<\infty$ 时，记 $a_\alpha=\|D^\alpha u\|_p$。有限维数列范数之间满足

$$
\left(\sum a_\alpha^p\right)^{1/p}
\le\sum a_\alpha
\le N^{1-1/p}\left(\sum a_\alpha^p\right)^{1/p}.
$$

当 $p=\infty$ 时，令 $a_\alpha=\|D^\alpha u\|_\infty$，则

$$
\max_\alpha a_\alpha\le\sum_\alpha a_\alpha
\le N\max_\alpha a_\alpha.
$$

所以 $\sum_{|\alpha|\le m}\|D^\alpha u\|_p$ 与本书范数等价。等价范数给出相同的收敛、闭集、完备性和连续线性泛函，但**最小表示公式中的精确数值依赖具体范数**。

若只保留 $|\alpha|=m$ 的导数，得到的是最高阶半范数。比如在有限测度域上，非零常数的所有一阶导数都为零，但函数不为零。若想用最高阶半范数代替完整范数，需要另加边界条件及相应的 Poincaré 型不等式，不能不加说明直接替换。

### 2.3 用弱导数定义 $W^{m,p}(\Omega)$

$$
\boxed{
W^{m,p}(\Omega)
=\{u\in L^p(\Omega):D^\alpha u\in L^p(\Omega),\ |\alpha|\le m\}.
}
$$

这里 $D^\alpha u$ 一律指弱导数。零阶条件就是 $u\in L^p$。由弱导数的线性，$W^{m,p}$ 是向量空间。

作为补充，该定义也用于 $p=\infty$。教材 3.2 对三种空间并列讨论时主要取有限 $p$。

### 2.4 用光滑函数完备化定义 $H^{m,p}(\Omega)$

对 $1\le p<\infty$，先取

$$
S=\{u\in C^m(\Omega):\|u\|_{m,p}<\infty\},
$$

其中导数是经典导数，再定义

$$
H^{m,p}(\Omega)=S\text{ 关于 }\|\cdot\|_{m,p}\text{ 的完备化}.
$$

这个定义表达的是：“能否用光滑函数同时逼近函数及其各阶导数？”刚定义时 $H^{m,p}$ 是一个抽象完备化；要把它视为具体函数空间，需要教材 3.4 的识别。

**记号提醒。** 这里 $H^{m,p}$ 是本书的特定记法。通常 $H^m$ 专指 $W^{m,2}$；其他文献中的 $H^{s,p}$ 还可能表示 Bessel 势空间，不能仅凭字母相同混用。

### 2.5 用紧支撑光滑函数闭包定义 $W_0^{m,p}(\Omega)$

$$
\boxed{
W_0^{m,p}(\Omega)=\overline{C_c^\infty(\Omega)}^{,W^{m,p}(\Omega)}.
}
$$

也就是说，$u\in W_0^{m,p}$ 当且仅当存在 $\varphi_j\in C_c^\infty(\Omega)$，使

$$
\|u-\varphi_j\|_{m,p}\to0.
$$

不是只要求 $\|u-\varphi_j\|_p\to0$，而是要求所有 $|\alpha|\le m$ 的导数同时在 $L^p$ 中逼近。

因此有连续嵌入

$$
W_0^{m,p}(\Omega)\hookrightarrow W^{m,p}(\Omega)
\hookrightarrow L^p(\Omega),
\qquad\|u\|_p\le\|u\|_{m,p}.
$$

这里“连续嵌入”指包含映射有界，不意味着紧嵌入。

当 $m=0$，$W^{0,p}=L^p$；对有限 $p$，由测试函数在 $L^p$ 中稠密，还有 $W_0^{0,p}=L^p$。

### 2.6 为什么 $W_0^{m,p}$ 一般小于 $W^{m,p}$？

取 $\Omega=(0,1)$。常数 $1$ 属于 $W^{1,p}(0,1)$。假设它也属于 $W_0^{1,p}$，则存在测试函数 $\varphi_j$ 满足

$$
\varphi_j\to1\text{ 于 }L^p,
\qquad\varphi_j'\to0\text{ 于 }L^p.
$$

由 Hölder 不等式，$\int_0^1\varphi_j\to1$。另一方面，分部积分给出

$$
\int_0^1\varphi_j(x)\,dx
=-\int_0^1x\varphi_j'(x)\,dx\to0,
$$

矛盾。因此

$$
1\in W^{1,p}(0,1)\setminus W_0^{1,p}(0,1).
$$

这个证明不需要迹定理。它直接说明：**$C_c^\infty$ 在 $L^p$ 中稠密，不代表在 $W^{1,p}$ 中稠密。**

在边界足够规则的域上，可以用迹来解释 $W_0^{m,p}$ 的边界条件；但对一般开集，本节始终以“闭包”作为定义，不能把尚未定义的逐点边界值写成一般刻画。

### 2.7 板书补充：光滑空间为什么需要完备化？

在 $(-1,1)$ 上取

$$
u_\varepsilon(x)=\sqrt{x^2+\varepsilon^2}.
$$

这些函数都光滑，并且

$$
|u_\varepsilon(x)-|x||\le\varepsilon,
\qquad
u_\varepsilon'(x)=\frac{x}{\sqrt{x^2+\varepsilon^2}}
\to\operatorname{sgn}(x)\quad\text{a.e.}
$$

导数之差的绝对值不超过 $1$。对 $1\le p<\infty$，由控制收敛定理可得

$$
u_\varepsilon\to|x|\quad\text{于 }W^{1,p}(-1,1).
$$

但 $|x|$ 不是 $C^1$ 函数，而且没有 $C^1$ 代表元：连续函数若与 $|x|$ 几乎处处相等，就必须处处等于 $|x|$。因此光滑子空间关于 Sobolev 范数可能不完备。

这一例子不能照搬到 $p=\infty$，因为

$$
\|u_\varepsilon'-\operatorname{sgn}\|_\infty=1.
$$

### 2.8 本节尚未证明的等式

教材预告后面的 Meyers–Serrin 定理：对任意开集及 $1\le p<\infty$，

$$
H^{m,p}(\Omega)=W^{m,p}(\Omega).
$$

本节 3.4 只证明其中的包含关系。后面的光滑逼近结论不能提前用来证明本节完备性，否则逻辑会循环。这一预告也不说明 $W_0^{m,p}=W^{m,p}$。

## 3. §3.3：$W^{m,p}(\Omega)$ 是 Banach 空间——重点证明

### 3.1 定理与证明思路

**定理。** 对 $m\in\mathbb N_0$、$1\le p\le\infty$，$W^{m,p}(\Omega)$ 关于上述范数完备。

证明分为三步：

1. 每个导数分量在 $L^p$ 中有极限。
2. 用测试函数证明这些分量极限确实是同一个函数的弱导数。
3. 把有限个分量收敛合起来，得到 Sobolev 范数收敛。

第二步是整份证明的关键，不能省略。

### 3.2 第一步：逐分量取 $L^p$ 极限

设 $(u_j)$ 是 $W^{m,p}$ 中的 Cauchy 列。对每个 $|\alpha|\le m$，有

$$
\|D^\alpha u_j-D^\alpha u_k\|_p
\le\|u_j-u_k\|_{m,p}\to0.
$$

由 $L^p$ 的完备性，存在 $v_\alpha\in L^p(\Omega)$，使

$$
D^\alpha u_j\to v_\alpha\quad\text{于 }L^p(\Omega).
$$

对于零多重指标，记 $v_0=u$，于是 $u_j\to u$ 于 $L^p$。

现在只知道一组 $L^p$ 极限，并不能直接断言 $v_\alpha=D^\alpha u$。

### 3.3 第二步：验证弱导数相容性

固定任意 $\varphi\in C_c^\infty(\Omega)$。由于测试函数及其所有导数都光滑、紧支撑，

$$
\varphi,D^\alpha\varphi\in L^{p'}(\Omega).
$$

于是

$$
\left|\int_\Omega(u_j-u)D^\alpha\varphi\,dx\right|
\le\|u_j-u\|_p\|D^\alpha\varphi\|_{p'}\to0,
$$

$$
\left|\int_\Omega(D^\alpha u_j-v_\alpha)\varphi\,dx\right|
\le\|D^\alpha u_j-v_\alpha\|_p\|\varphi\|_{p'}\to0.
$$

对每个 $j$，弱导数定义给出

$$
\int_\Omega u_jD^\alpha\varphi\,dx
=(-1)^{|\alpha|}\int_\Omega D^\alpha u_j\,\varphi\,dx.
$$

令 $j\to\infty$，得到

$$
\int_\Omega uD^\alpha\varphi\,dx
=(-1)^{|\alpha|}\int_\Omega v_\alpha\varphi\,dx.
$$

因为 $\varphi$ 任意，故

$$
D^\alpha u=v_\alpha\quad\text{弱意义下}.
$$

所有 $v_\alpha$ 都属于 $L^p$，因此 $u\in W^{m,p}(\Omega)$。

这个论证同时覆盖 $p=1$ 与 $p=\infty$，因为对应的测试函数属于 $L^\infty$ 与 $L^1$。

### 3.4 第三步：证明在 Sobolev 范数下收敛

对有限 $p$，

$$
\|u_j-u\|_{m,p}^p
=\sum_{|\alpha|\le m}\|D^\alpha u_j-v_\alpha\|_p^p\to0.
$$

因为这是有限项之和，每项都趋于零。对 $p=\infty$，有限个趋零数的最大值也趋于零。

所以每个 Cauchy 列都在 $W^{m,p}$ 中收敛，定理得证。$\square$

### 3.5 如何用分布语言压缩这份证明？

Hölder 不等式说明 $L^p$ 收敛蕴含分布收敛。因此

$$
T_{v_\alpha}
=\lim_jT_{D^\alpha u_j}
=\lim_jD^\alpha T_{u_j}
=D^\alpha T_u.
$$

最后一步使用分布求导的连续性。但考试若要求展开细节，最好直接写前面的测试函数积分等式。

**不能使用的跳步：**“函数收敛，所以导数也收敛到极限函数的导数。”一般函数列根本没有这一性质；这里依靠的是同时控制导数，并在弱导数恒等式中取极限。

**立即推论：** $W_0^{m,p}$ 是 $W^{m,p}$ 的闭子空间，故也是 Banach 空间。

## 4. §3.4：把 $H^{m,p}$ 识别为 $W^{m,p}$ 的闭子空间

若 $u\in C^m(\Omega)$，其经典导数通过分部积分满足弱导数定义。因此

$$
S=\{u\in C^m(\Omega):\|u\|_{m,p}<\infty\}\subset W^{m,p}(\Omega),
$$

而且使用的是同一个范数。

由于已经证明 $W^{m,p}$ 完备，$S$ 的任意 Sobolev-Cauchy 列在 $W^{m,p}$ 中有极限。两个等价 Cauchy 列具有同一极限，故映射

$$
[(u_j)]\longmapsto\lim_j u_j\quad\text{于 }W^{m,p}
$$

给出等距同构

$$
H^{m,p}(\Omega)\cong\overline S^{,W^{m,p}(\Omega)}.
$$

作此识别以后，可以写

$$
H^{m,p}(\Omega)\subset W^{m,p}(\Omega).
$$

完整逻辑是“经典导数也是弱导数 → 等距嵌入 → 环境空间完备 → 完备化等于其中的闭包”，而不是把完备化直接当作一个已经给定的函数集合。

## 5. §3.5–3.6：把 Sobolev 空间放进乘积 $L^p$ 空间

### 5.1 构造 $\Omega^{(m)}$ 与 $E_p$

令 $A_m=\{\alpha:|\alpha|\le m\}$。给每个 $\alpha$ 配一个带标签的 $\Omega$ 副本 $\Omega_\alpha$，定义不交并

$$
\Omega^{(m)}=\bigsqcup_{\alpha\in A_m}\Omega_\alpha.
$$

也可以把它理解为 $\Omega\times A_m$，采用 Lebesgue 测度与计数测度的乘积。

令

$$
E_p=L^p(\Omega^{(m)})
\cong\prod_{|\alpha|\le m}L^p(\Omega).
$$

其元素是函数向量 $V=(v_\alpha)$，其范数为

$$
\|V\|_{E_p}=
\begin{cases}
\left(\sum_{|\alpha|\le m}\|v_\alpha\|_p^p\right)^{1/p},&p<\infty,\\
\max_{|\alpha|\le m}\|v_\alpha\|_\infty,&p=\infty.
\end{cases}
$$

这个“许多副本”的构造只是为了把有限个导数分量写成一个普通 $L^p$ 元素，不涉及新的空间变量或新的求导方向。

### 5.2 等距嵌入 $P$

定义

$$
P:W^{m,p}(\Omega)\to E_p,
\qquad Pu=(D^\alpha u)_{|\alpha|\le m}.
$$

由定义立刻有

$$
\|Pu\|_{E_p}=\|u\|_{m,p}.
$$

所以 $P$ 线性且等距。因为其中包含零阶分量 $u$，所以 $P$ 是单射。

记 $R=P(W^{m,p})$。若 $Pu_j\to V$ 于 $E_p$，则

$$
\|u_j-u_k\|_{m,p}=\|Pu_j-Pu_k\|_{E_p}\to0.
$$

完备性给出 $u_j\to u$ 于 $W^{m,p}$，从而 $Pu_j\to Pu$，所以 $V=Pu\in R$。因此 $R$ 是 $E_p$ 的闭线性子空间。

一般 $R\ne E_p$。例如取 $\Omega=(0,1)$、$m=1$ 时，向量 $(0,1)$ 不可能等于 $(u,u')$，因为 $u=0$ 的弱导数必须也是零。$R$ 中的分量必须满足弱导数相容条件。

### 5.3 性质如何从 $L^p$ 传递过来？

**定理 3.6。**

- $1\le p<\infty$ 时，$W^{m,p}(\Omega)$ 可分。
- $1<p<\infty$ 时，$W^{m,p}(\Omega)$ 一致凸且自反。
- $p=2$ 时，$W^{m,2}(\Omega)$ 是可分 Hilbert 空间。

解释如下。

**可分性：** 可分是指存在可数稠密子集。$E_p$ 对有限 $p$ 可分，其子空间作为度量空间也可分，因此 $R$ 可分，再由等距同构传回 $W^{m,p}$。

**一致凸性：** 在单位球中，两点若相距至少 $\varepsilon$，它们的中点就必须离单位球面至少一段只依赖 $\varepsilon$ 的距离。$E_p$ 在 $1<p<\infty$ 时一致凸，子空间用继承范数仍满足同一不等式。

**自反性：** 自反要求自然映射

$$
J:X\to X'',\qquad(Jx)(L)=L(x)
$$

为满射。自反 Banach 空间的闭子空间自反，因此由 $E_p$ 自反可得 $R$ 自反。

**注意范数：** 本节的一致凸性针对规定的 Sobolev 范数。换成任意等价范数后，完备性、可分性、自反性保持，但一致凸性不能只凭范数等价就断言保持。

### 5.4 $p=2$ 的内积

定义

$$
\boxed{
(u,v)_m=\sum_{|\alpha|\le m}\int_\Omega D^\alpha u(x)\overline{D^\alpha v(x)}\,dx.
}
$$

则 $(u,u)_m=\|u\|_{m,2}^2$，由完备性得到 Hilbert 空间结构。特别地，当 $m=1$，

$$
(u,v)_1=\int_\Omega u\overline v\,dx
+\int_\Omega\nabla u\cdot\overline{\nabla v}\,dx.
$$

这对应图片中的板书。$W_0^{m,p}$ 是闭子空间，也继承上述适用指数范围内的性质。

## 6. 对偶表示需要哪些基础？（3.7—3.8）

### 6.1 连续线性泛函与对偶范数

设 $X$ 是赋范空间。线性映射 $L:X\to\mathbb C$ 连续，当且仅当存在常数 $C$，使

$$
|L(u)|\le C\|u\|_X,\qquad u\in X.
$$

所有这样的泛函组成连续对偶空间 $X'$，其范数为

$$
\|L\|_{X'}=\sup_{\|u\|_X\le1}|L(u)|.
$$

这里的 $L$ 是“输入函数、输出一个数”的映射。例如，$v\in L^{p'}(\Omega)$ 给出

$$
L_v(u)=\int_\Omega u(x)v(x)\,dx.
$$

Hölder 不等式说明 $L_v$ 连续。这里沿用教材的双线性配对，不在积分中自动给 $v$ 加共轭；它与 Hilbert 内积的记号应当区分。

### 6.2 本节使用的两个泛函分析定理

**Hahn–Banach 延拓定理。** 若 $Y\subset X$ 是线性子空间，$\ell\in Y'$，则存在 $\widehat\ell\in X'$ 满足

$$
\widehat\ell|_Y=\ell,\qquad
\|\widehat\ell\|_{X'}=\|\ell\|_{Y'}.
$$

它保证“保范延拓存在”，一般不直接保证延拓唯一。这里不需要事先假设 $X$ 自反。

**$L^p$ 的对偶表示。** 对 Lebesgue 测度空间，若 $1\le p<\infty$，则每个 $L\in(L^p)'$ 都有唯一的 $v\in L^{p'}$，使

$$
L(u)=\int uv,\qquad \|L\|=\|v\|_{p'}.
$$

当 $p=1$ 时，$p'=\infty$，此结论仍成立。不能把它直接延伸为 $(L^\infty)'=L^1$；一般而言，$(L^\infty)'$ 比由 $L^1$ 函数产生的积分泛函空间大。

### 6.3 乘积空间的对偶

沿用第 5 节的记号

$$
E_p=\prod_{|\alpha|\le m}L^p(\Omega)
\cong L^p(\Omega^{(m)}).
$$

当 $1\le p<\infty$ 时，每个 $\Lambda\in E_p'$ 都可以唯一表示成

$$
\Lambda(U)=\sum_{|\alpha|\le m}\int_\Omega U_\alpha v_\alpha\,dx,
\qquad V=(v_\alpha)\in E_{p'},
$$

且

$$
\|\Lambda\|=\|V\|_{E_{p'}}=
\begin{cases}
\left(\displaystyle\sum_{|\alpha|\le m}\|v_\alpha\|_{p'}^{p'}\right)^{1/p'},&1<p<\infty,\\
\displaystyle\max_{|\alpha|\le m}\|v_\alpha\|_\infty,&p=1.
\end{cases}
$$

这是把 $L^p$ 对偶定理应用到“不相交的 $N$ 份 $\Omega$”上，或等价地应用到有限乘积空间上。

其基本估计是

$$
\begin{aligned}
\left|\sum_\alpha\int_\Omega U_\alpha v_\alpha\right|
&\le\sum_\alpha\|U_\alpha\|_p\|v_\alpha\|_{p'}\\
&\le\|U\|_{E_p}\|V\|_{E_{p'}}.
\end{aligned}
$$

第二步是对有限数列应用 Hölder 不等式；$p=1$ 时，它就是“和乘以最大值”的估计。

**为什么这里系数唯一，而后面可能不唯一？** 在整个 $E_p$ 上，所有分量 $U_\alpha$ 都可以独立选取；在 $P(W^{m,p})$ 上，分量必须是同一个函数的各阶导数，不能独立选取。

## 7. Sobolev 空间的对偶表示定理（3.9，重点证明）

### 7.1 定理的准确表述

设 $1\le p<\infty$，$L\in(W^{m,p}(\Omega))'$。则存在 $V=(v_\alpha)_{|\alpha|\le m}\in E_{p'}$，使

$$
\boxed{
L(u)=\sum_{|\alpha|\le m}\int_\Omega D^\alpha u(x)v_\alpha(x)\,dx,
\qquad u\in W^{m,p}(\Omega).
}
\tag{7.1}
$$

而且

$$
\boxed{
\|L\|_{(W^{m,p})'}
=\min\left\{\|V\|_{E_{p'}}:V\text{ 对所有 }u\in W^{m,p}\text{ 满足式 }(7.1)\right\}.
}
\tag{7.2}
$$

特别要分清三件事：

1. 系数表示存在。
2. 表示系数的范数下确界能够达到，所以可以写成最小值。
3. 若 $1<p<\infty$，**达到最小范数的系数组唯一**；普通的表示系数组一般不唯一。

第三点不能简写成“表示唯一”。教材所说的唯一性同时要求表示式和最小范数条件。

### 7.2 证明第一步：把泛函搬到闭子空间上

定义

$$
P:W^{m,p}(\Omega)\longrightarrow E_p,
\qquad Pu=(D^\alpha u)_{|\alpha|\le m},
$$

并令 $R=P(W^{m,p}(\Omega))$。第 5 节已经证明 $P$ 是到闭子空间 $R$ 的等距同构。

在 $R$ 上定义

$$
\ell(Pu)=L(u).
$$

因为 $P$ 单射，右侧不依赖于原像的选择，所以定义良好。又因为 $\|Pu\|_{E_p}=\|u\|_{m,p}$，

$$
\|\ell\|_{R'}
=\sup_{\|Pu\|_{E_p}\le1}|\ell(Pu)|
=\sup_{\|u\|_{m,p}\le1}|L(u)|
=\|L\|.
$$

### 7.3 证明第二步：Hahn–Banach 保范延拓

由 Hahn–Banach 定理，$\ell$ 可以延拓为 $\widehat\ell\in E_p'$，并且

$$
\widehat\ell|_R=\ell,
\qquad\|\widehat\ell\|=\|\ell\|=\|L\|.
$$

注意：这一步先把“只知道怎样作用在兼容导数组上的泛函”，延拓成“能够作用在任意函数数组上的泛函”。这样才能使用整个乘积空间的对偶表示。

### 7.4 证明第三步：使用 $L^p$ 对偶表示

由第 6 节，存在 $V\in E_{p'}$，使

$$
\widehat\ell(U)=\sum_\alpha\int_\Omega U_\alpha v_\alpha\,dx,
\qquad \|V\|_{E_{p'}}=\|\widehat\ell\|.
$$

取 $U=Pu$，得到

$$
L(u)=\ell(Pu)=\widehat\ell(Pu)
=\sum_\alpha\int_\Omega D^\alpha u\,v_\alpha\,dx.
$$

并且该系数组满足 $\|V\|_{E_{p'}}=\|L\|$。

### 7.5 证明第四步：为什么恰好是最小范数？

若另一个系数组 $Z=(z_\alpha)$ 也表示同一个 $L$，则由两次 Hölder 估计，

$$
|L(u)|\le\|u\|_{m,p}\|Z\|_{E_{p'}}.
$$

对 $\|u\|_{m,p}\le1$ 取上确界，得到

$$
\|L\|\le\|Z\|_{E_{p'}}.
$$

上一步构造的 $V$ 正好达到这个下界，故最小值成立。至此，式 (7.1)—(7.2) 得证。

**端点提醒：** 这一“最小值能够达到”的论证也适用于 $p=1$。它来自 Hahn–Banach 保范延拓，并不依赖 $L^\infty$ 的自反性。

### 7.6 证明第五步：最小系数组为什么唯一？

设 $1<p<\infty$。此时 $1<p'<\infty$，$E_{p'}$ 严格凸：两个不同的、具有相同非零范数的向量，其平均值的范数严格小于该公共范数。

假设 $V,Z$ 都表示 $L$，且

$$
\|V\|_{E_{p'}}=\|Z\|_{E_{p'}}=\|L\|=M.
$$

若 $M=0$，则 $V=Z=0$。若 $M>0$ 且 $V\ne Z$，则

$$
\left\|\frac{V+Z}{2}\right\|_{E_{p'}}<M.
$$

但 $(V+Z)/2$ 仍然表示同一个 $L$，与 $M$ 是最小值矛盾。因此 $V=Z$。

这里使用严格凸性已经足够；一致凸性蕴含严格凸性。对于 $p=1$，$E_\infty$ 一般不严格凸，因此不能由此宣称最小系数组唯一。

### 7.7 普通系数表示不唯一的具体例子

取 $\Omega=(0,1)$、$m=1$，任意非零 $\psi\in C_c^\infty(0,1)$。由弱导数定义，对每个 $u\in W^{1,p}(0,1)$ 都有

$$
\int_0^1u\psi'\,dx+\int_0^1u'\psi\,dx=0.
$$

因此 $(0,0)$ 和 $(\psi',\psi)$ 都表示零泛函。更一般地，若 $(v_0,v_1)$ 表示 $L$，那么

$$
(v_0+\psi',\ v_1+\psi)
$$

也表示 $L$。这些表示的范数未必相同；零泛函的最小范数系数当然只有零数组。

**考试可复述的证明链：** 等距嵌入 $P$ → 在像空间上定义 $\ell$ → Hahn–Banach 保范延拓 → $L^p$ 对偶表示 → Hölder 证明最小性 → 严格凸性证明最小表示唯一。

## 8. 从 Sobolev 泛函到分布：边界信息在哪里？（3.10—3.11）

### 8.1 把泛函限制到测试函数

设 $L$ 由式 (7.1) 表示。每个 $v_\alpha\in L^{p'}(\Omega)$ 都局部可积，因而定义分布

$$
T_{v_\alpha}(\varphi)=\int_\Omega\varphi v_\alpha\,dx.
$$

令

$$
\boxed{
T=\sum_{|\alpha|\le m}(-1)^{|\alpha|}D^\alpha T_{v_\alpha}.
}
\tag{8.1}
$$

对任意 $\varphi\in\mathcal D(\Omega)=C_c^\infty(\Omega)$，分布导数的定义给出

$$
\begin{aligned}
T(\varphi)
&=\sum_\alpha(-1)^{|\alpha|}(-1)^{|\alpha|}
T_{v_\alpha}(D^\alpha\varphi)\\
&=\sum_\alpha\int_\Omega D^\alpha\varphi\,v_\alpha\,dx
=L(\varphi).
\end{aligned}
$$

两个符号相乘得到 $(-1)^{2|\alpha|}=1$，这是最容易写错的一步。

当 $m=1$ 时，式 (8.1) 写作

$$
T=v_0-\sum_{j=1}^n\partial_jv_j=v_0-\operatorname{div}V,
$$

这里的等号是在分布意义下成立，$V=(v_1,\ldots,v_n)$。

### 8.2 为什么不能随便把导数移到系数上？

板书中“分部积分”的想法是正确的，但需要明确解释：

- 对测试函数，转移导数是分布导数的定义，不要求 $v_\alpha$ 有经典导数。
- 对一般 $u\in W^{m,p}(\Omega)$，不能未经说明就写成没有边界项的经典分部积分。
- $v_\alpha\in L^{p'}$ 本身也不保证它有边界值或经典偏导数。

因此，表示式 $\sum_\alpha\int D^\alpha u\,v_\alpha$ 在完整的 $W^{m,p}$ 上有意义，而 $\sum_\alpha(-1)^{|\alpha|}D^\alpha v_\alpha$ 首先是作用在测试函数上的分布。

### 8.3 关键反例：不同泛函可能对应同一个分布

取 $\Omega=(0,1)$、$m=1$，定义

$$
L(u)=\int_0^1u'(x)\,dx.
$$

对 $1\le p<\infty$，Hölder 不等式给出

$$
|L(u)|\le\|u'\|_{L^p(0,1)}\le\|u\|_{1,p},
$$

所以 $L\in(W^{1,p}(0,1))'$。它不是零泛函，因为 $L(x)=1$。

但对每个 $\varphi\in C_c^\infty(0,1)$，

$$
L(\varphi)=\int_0^1\varphi'\,dx=0.
$$

因此 $L$ 限制到测试函数得到的分布是零分布。其系数可以取 $(v_0,v_1)=(0,1)$，对应

$$
T=-D(1)=0\quad\text{在 }\mathcal D'(0,1)\text{ 中}.
$$

在一维绝对连续代表的语言下，$L(u)=u(1)-u(0)$，它记录的是边界信息；测试函数在边界附近为零，检测不到这部分信息。

由连续性，$L$ 在 $W_0^{1,p}(0,1)$ 上也恒为零。这说明：

$$
\boxed{\text{完整 }W^{m,p}\text{ 上的泛函，通常不能仅靠其对应分布来恢复。}}
$$

不要把这个例子与第 7.7 节混淆：$(\psi',\psi)$ 在整个 $W^{1,p}$ 上表示零泛函；$(0,1)$ 只在 $W_0^{1,p}$ 上表示零泛函。

### 8.4 固定泛函的最小值，与固定分布的最小值

对于固定的 $L\in(W^{m,p})'$，第 7 节取最小值时，系数必须对**所有 $u\in W^{m,p}$** 表示这个指定的 $L$。

对于固定分布 $T$，系数只需要对**所有测试函数**给出 $T$。这是较弱的要求，允许的系数组可能更多。

上例中，固定非零泛函 $L(u)=\int u'$ 的最小表示范数严格为正；但固定其对应的零分布 $T=0$，最小表示范数是零。阅读教材 3.10 的最小值表述时，必须保留“表示指定的延拓 $L$”这一约束，不能只保留“表示 $T$”。

### 8.5 给定这样的分布，怎样延拓到 $W_0^{m,p}$？

设 $T$ 有式 (8.1) 的表示。对测试函数有

$$
|T(\varphi)|\le\|V\|_{E_{p'}}\|\varphi\|_{m,p}.
\tag{8.2}
$$

给定 $u\in W_0^{m,p}(\Omega)$，按照该空间的定义，存在 $\varphi_j\in C_c^\infty(\Omega)$ 满足

$$
\|\varphi_j-u\|_{m,p}\to0.
$$

于是

$$
|T(\varphi_j)-T(\varphi_k)|
\le\|V\|_{E_{p'}}\|\varphi_j-\varphi_k\|_{m,p}\to0.
$$

所以 $T(\varphi_j)$ 是数域中的 Cauchy 列，极限存在。定义

$$
L_T(u)=\lim_{j\to\infty}T(\varphi_j).
$$

如果另有 $\psi_j\to u$，则

$$
|T(\varphi_j)-T(\psi_j)|
\le\|V\|_{E_{p'}}
\bigl(\|\varphi_j-u\|_{m,p}+\|\psi_j-u\|_{m,p}\bigr)\to0.
$$

因此定义与逼近序列无关。由极限运算可得线性，由式 (8.2) 可得

$$
|L_T(u)|\le\|V\|_{E_{p'}}\|u\|_{m,p}.
$$

这说明 $L_T\in(W_0^{m,p})'$。

**唯一性：** 两个连续延拓若在稠密子集 $C_c^\infty$ 上相同，则对其任一范数收敛逼近序列取极限，在整个 $W_0^{m,p}$ 上也相同。

### 8.6 延拓到完整空间，为什么可能不唯一？

固定系数组 $V$，式 (7.1) 本身就给出一个到 $W^{m,p}$ 的连续延拓；也可以对 $L_T$ 使用 Hahn–Banach 得到保范延拓。

然而，若 $W_0^{m,p}$ 是 $W^{m,p}$ 的真闭子空间，则存在非零连续泛函在 $W_0^{m,p}$ 上恒为零。把这样的泛函加到某个延拓上，得到另一个延拓。

所以这里的准确结论是：**在 $W_0^{m,p}$ 上延拓唯一；在完整 $W^{m,p}$ 上延拓可能不唯一。**

## 9. 负阶 Sobolev 空间（3.12）

### 9.1 定义与对偶定理

设 $m\ge1$、$1\le p<\infty$。定义

$$
W^{-m,p'}(\Omega)
=\left\{T\in\mathcal D'(\Omega):
T=\sum_{|\alpha|\le m}(-1)^{|\alpha|}D^\alpha T_{v_\alpha},
\quad V\in E_{p'}\right\}.
$$

负号“$-m$”表示负阶正则性，不是在做“负数次经典求导”。空间中的元素通常是分布，未必是普通函数。

定理 3.12 断言

$$
\boxed{
(W_0^{m,p}(\Omega))'\cong W^{-m,p'}(\Omega)
}
\tag{9.1}
$$

是等距同构，其中

$$
\boxed{
\|T\|_{-m,p'}
=\min_{T=\sum_\alpha(-1)^{|\alpha|}D^\alpha T_{v_\alpha}}
\|V\|_{E_{p'}}.
}
\tag{9.2}
$$

这里的最小值固定的是分布 $T$，也就固定了它在 $W_0^{m,p}$ 上的唯一延拓。

### 9.2 证明：两个方向和范数相等

**方向一：从系数表示到连续泛函。** 第 8.5 节已经构造唯一的 $L_T\in(W_0^{m,p})'$，且对每一组表示系数都有

$$
\|L_T\|\le\|V\|_{E_{p'}}.
\tag{9.3}
$$

**方向二：从连续泛函到分布表示。** 给定 $L\in(W_0^{m,p})'$，先限制到 $C_c^\infty$，记作 $T$。要确认它是分布，设 $\varphi_j\to0$ 于 $\mathcal D(\Omega)$。这些函数具有共同紧支撑 $K\Subset\Omega$，且各阶导数一致趋于零。特别地，

$$
\|\varphi_j\|_{m,p}^p
\le |K|\sum_{|\alpha|\le m}\|D^\alpha\varphi_j\|_\infty^p\to0.
$$

于是 $|T(\varphi_j)|\le\|L\|\|\varphi_j\|_{m,p}\to0$，从而 $T\in\mathcal D'(\Omega)$。

再由 Hahn–Banach，把 $L$ 保范延拓到 $W^{m,p}$，然后使用定理 3.9，得到表示系数 $V$，且

$$
T=\sum_\alpha(-1)^{|\alpha|}D^\alpha T_{v_\alpha},
\qquad \|V\|_{E_{p'}}=\|L\|.
\tag{9.4}
$$

由于测试函数在 $W_0^{m,p}$ 中稠密，限制映射是单射；第一个方向保证它也是满射。式 (9.3)—(9.4) 同时证明等距性以及最小值的达到。

### 9.3 三种等价的范数表达

以后把 $T$ 与其唯一延拓统一记为 $T$。那么

$$
\begin{aligned}
\|T\|_{-m,p'}
&=\sup_{\substack{u\in W_0^{m,p}\\\|u\|_{m,p}\le1}}|T(u)|\\
&=\sup_{\substack{\varphi\in C_c^\infty(\Omega)\\\|\varphi\|_{m,p}\le1}}|T(\varphi)|\\
&=\min_{T=\sum_\alpha(-1)^{|\alpha|}D^\alpha T_{v_\alpha}}
\|V\|_{E_{p'}}.
\end{aligned}
$$

第二个等号来自稠密性，必要时把逼近函数稍作归一化，使其仍在单位球内。这三个公式分别强调“对偶作用”“测试函数检验”“系数表示”。

### 9.4 完备性、可分性与自反性

连续对偶空间总是 Banach 空间，因此 $W^{-m,p'}$ 完备。

当 $1<p<\infty$ 时，它还可分且自反。可以通过下列商空间描述理解：定义

$$
Q:E_{p'}\to W^{-m,p'},
\qquad Q(V)=\sum_\alpha(-1)^{|\alpha|}D^\alpha T_{v_\alpha}.
$$

估计 $\|Q(V)\|_{-m,p'}\le\|V\|_{E_{p'}}$ 表明 $Q$ 连续；其核 $\ker Q$ 是闭子空间，并且

$$
W^{-m,p'}\cong E_{p'}/\ker Q
$$

等距成立。商范数就是在所有表示系数组中取下确界的范数，而这里下确界已经证明可以达到。可分空间的商空间可分，自反 Banach 空间关于闭子空间的商空间自反，故结论成立。

### 9.5 一个负阶空间中的非函数元素：Dirac 分布

取 $\Omega=(0,1)$、$a\in(0,1)$。对 $\varphi\in C_c^\infty(0,1)$，

$$
|\varphi(a)|=\left|\int_0^a\varphi'(x)\,dx\right|
\le\sqrt a\,\|\varphi'\|_2
\le\sqrt a\,\|\varphi\|_{1,2}.
$$

因此 $\delta_a(\varphi)=\varphi(a)$ 连续延拓到 $H_0^1(0,1)=W_0^{1,2}(0,1)$，即

$$
\delta_a\in H^{-1}(0,1)=W^{-1,2}(0,1).
$$

还可以直接给出系数表示。令 $H_a(x)=\mathbf1_{(a,1)}(x)$，则

$$
DH_a=\delta_a,
\qquad \delta_a=-D(-H_a).
$$

这里 $-H_a\in L^2(0,1)$，正好符合定理 3.12 的形式。这说明负阶空间可以容纳集中在一点的源项。该结论使用了一维估计，不能不加检验地推广成“任意维数的 Dirac 分布都属于 $H^{-1}$”。

## 10. 在普通函数上定义负阶范数（3.13）

### 10.1 从 $L^{p'}$ 函数到负阶空间

本节按教材取 $1<p<\infty$。对 $v\in L^{p'}(\Omega)$，定义

$$
L_v(u)=\int_\Omega uv\,dx,\qquad u\in W_0^{m,p}(\Omega).
$$

由 Hölder 不等式和 $\|u\|_p\le\|u\|_{m,p}$，

$$
|L_v(u)|\le\|v\|_{p'}\|u\|_p
\le\|v\|_{p'}\|u\|_{m,p}.
$$

因此定义

$$
\boxed{
\|v\|_{-m,p'}
:=\|L_v\|_{(W_0^{m,p})'}
=\sup_{\substack{u\in W_0^{m,p}\\\|u\|_{m,p}\le1}}
\left|\int_\Omega uv\,dx\right|
\le\|v\|_{p'}.
}
\tag{10.1}
$$

这就是图片中 3.13 和旁注写出的范数。这里上确界的约束是 **Sobolev 范数不超过 $1$**，不能改成只要求 $\|u\|_p\le1$；后者通常会恢复普通 $L^{p'}$ 范数。

### 10.2 为什么它是范数，而不只是半范数？

齐次性和三角不等式由积分和上确界直接得到。关键是正定性：若 $\|v\|_{-m,p'}=0$，则

$$
\int_\Omega\varphi v\,dx=0,
\qquad \varphi\in C_c^\infty(\Omega).
$$

由局部可积函数确定分布的唯一性，$v=0$ a.e.。所以它确实是 $L^{p'}$ 等价类上的范数。

### 10.3 “更弱的范数”具体是什么意思？

由式 (10.1)，$L^{p'}$ 范数收敛必然推出负阶范数收敛，但反方向一般不成立。

例：取 $\Omega=(0,2\pi)$、$m=1$、$p=p'=2$，令 $v_k(x)=\sin(kx)$。则

$$
\|v_k\|_2=\sqrt\pi.
$$

对 $\varphi\in C_c^\infty(0,2\pi)$，分部积分给出

$$
\int_0^{2\pi}\sin(kx)\varphi(x)\,dx
=\frac1k\int_0^{2\pi}\cos(kx)\varphi'(x)\,dx.
$$

所以

$$
\left|\int_0^{2\pi}v_k\varphi\,dx\right|
\le\frac{\sqrt\pi}{k}\|\varphi'\|_2
\le\frac{\sqrt\pi}{k}\|\varphi\|_{1,2}.
$$

由稠密性，该估计也适用于 $H_0^1$ 中的测试对象。因此

$$
\|v_k\|_{-1,2}\le\frac{\sqrt\pi}{k}\to0,
\qquad\|v_k\|_2\not\to0.
$$

负阶范数衡量函数对具有导数控制的测试对象的作用。高频振荡在配对积分中产生抵消，因此可能在负阶范数中很小。

### 10.4 补充：负阶空间是这个较弱范数下的完备化

图片中 3.13 展示到负阶范数的定义；3.7 还预告了完备化解释。下面补出其论证，帮助理解“负阶空间为何比普通函数空间更大”。

当 $1<p<\infty$ 时，

$$
\boxed{
\overline{\bigl(L^{p'}(\Omega),\|\cdot\|_{-m,p'}\bigr)}^{\text{完备化}}
\cong W^{-m,p'}(\Omega).
}
\tag{10.2}
$$

**证明。** 由式 (10.1)，$L^{p'}$ 等距地映入负阶空间——这里“等距”指在源空间使用负阶范数。目标空间已经完备，只需证明像稠密。

给定

$$
T=\sum_\alpha(-1)^{|\alpha|}D^\alpha T_{v_\alpha},
\qquad v_\alpha\in L^{p'}(\Omega).
$$

由于 $p'<\infty$，可用 $g_{\alpha,j}\in C_c^\infty(\Omega)$ 在 $L^{p'}$ 中逼近每个 $v_\alpha$。令

$$
f_j=\sum_\alpha(-1)^{|\alpha|}D^\alpha g_{\alpha,j}.
$$

这是有限个紧支撑光滑函数的和，所以 $f_j\in C_c^\infty(\Omega)\subset L^{p'}(\Omega)$。分布意义下，

$$
T-T_{f_j}
=\sum_\alpha(-1)^{|\alpha|}D^\alpha T_{v_\alpha-g_{\alpha,j}}.
$$

于是

$$
\|T-T_{f_j}\|_{-m,p'}
\le\left(\sum_\alpha\|v_\alpha-g_{\alpha,j}\|_{p'}^{p'}\right)^{1/p'}\to0.
$$

稠密性得证。这个证明只使用此前的 $C_c^\infty$ 在有限指数 $L^{p'}$ 中稠密，不需要提前使用尚未证明的 Sobolev 光滑逼近定理。

### 10.5 为什么完备化结论不能直接推广到 $p=1$？

当 $p=1$ 时，$p'=\infty$，光滑函数通常不能在 $L^\infty$ 范数中逼近任意有界可测函数。事实上，式 (10.2) 在这个端点一般不成立。

以下例子可以选读。仍在 $(0,1)$ 上，$\delta_a\in W^{-1,\infty}$，因为

$$
|\varphi(a)|\le\|\varphi'\|_1\le\|\varphi\|_{1,1}.
$$

取非负光滑单峰函数 $\eta\in C_c^\infty(-1,1)$，满足 $\eta(0)=1$、$\int|\eta'|=2$，并令 $\varphi_h(x)=\eta((x-a)/h)$，其中 $h$ 足够小。则

$$
\|\varphi_h\|_{1,1}=h\|\eta\|_1+2,
\qquad \delta_a(\varphi_h)=1.
$$

对任意固定 $g\in L^\infty(0,1)$，

$$
\left|\int_0^1g\varphi_h\,dx\right|
\le h\|g\|_\infty\|\eta\|_1\to0.
$$

故

$$
\|\delta_a-T_g\|_{-1,\infty}
\ge\limsup_{h\downarrow0}
\frac{|\delta_a(\varphi_h)-T_g(\varphi_h)|}{\|\varphi_h\|_{1,1}}
=\frac12.
$$

所以 $L^\infty$ 的像在 $W^{-1,\infty}$ 中并不稠密。这与 3.12 在 $p=1$ 时仍然成立、最小表示范数仍能达到，并不矛盾；它们是不同的结论。

## 11. 板书补充：为什么 Poisson 方程自然联系到负阶空间？


### 11.1 从经典方程到弱形式

设 $\Omega\subset\mathbb R^n$ 是有界开集。形式上的 Dirichlet 问题为

$$
\begin{cases}
-\Delta u=f,&x\in\Omega,\\
u=0,&x\in\partial\Omega.
\end{cases}
$$

假如 $u$ 足够光滑，乘以 $\varphi\in C_c^\infty(\Omega)$ 并分部积分，得到

$$
\int_\Omega\nabla u\cdot\nabla\varphi\,dx
=\int_\Omega f\varphi\,dx.
$$

这条等式左侧只需要一阶导数。因此，即使无法把 $\Delta u$ 理解为普通函数，仍然可以寻找 $u\in H_0^1(\Omega)=W_0^{1,2}(\Omega)$，使

$$
\int_\Omega\nabla u\cdot\nabla\varphi\,dx
=\langle f,\varphi\rangle,
\qquad\forall\varphi\in H_0^1(\Omega).
$$

这里 $f$ 可以是 $H^{-1}(\Omega)=(H_0^1(\Omega))'$ 的元素，右侧首先是对偶作用。若 $f$ 由局部可积函数诱导，则对 $\varphi\in C_c^\infty(\Omega)$ 可以写成 $\int_\Omega f\varphi\,dx$；但仅有 $f\in L^1_{\mathrm{loc}}(\Omega)$ 并不能保证该普通积分对每个 $\varphi\in H_0^1(\Omega)$ 都有意义。例如，当 $f\in L^2(\Omega)$ 时，Hölder 不等式保证 $f\varphi\in L^1(\Omega)$，因而可以对所有 $\varphi\in H_0^1(\Omega)$ 使用积分表达式。一般情形应保留对偶作用记号，除非已经验证相应的可积性。

**弱形式降低的是对未知函数的可微性要求，并没有放弃方程本身。** 取测试函数后，它仍然表达 $-\Delta u=f$ 在分布意义下成立。

### 11.2 为什么 $-\Delta u\in H^{-1}(\Omega)$？

若 $u\in H_0^1(\Omega)$，定义

$$
F_u(\varphi)=\int_\Omega\nabla u\cdot\nabla\varphi\,dx.
$$

由 Cauchy–Schwarz 不等式，

$$
|F_u(\varphi)|
\le\|\nabla u\|_2\|\nabla\varphi\|_2
\le\|u\|_{1,2}\|\varphi\|_{1,2}.
$$

所以 $F_u\in(H_0^1)'$。它在测试函数上的作用恰好是 $-\Delta u$ 的分布作用。用 3.12 的表示法，就是取

$$
v_0=0,\qquad v_{e_j}=\partial_j u,
$$

于是

$$
F_u=-\sum_{j=1}^n\partial_j T_{\partial_j u}=-\Delta u.
$$

这说明二阶微分算子 $-\Delta$ 可以被理解为一个有界线性映射

$$
-\Delta:H_0^1(\Omega)\longrightarrow H^{-1}(\Omega).
$$

注意：这里没有声称 $\partial_i\partial_j u\in L^2$。$u\in H^1$ 与 $u\in H^2$ 是不同层次的条件。

### 11.3 Poincaré 不等式与弱解的存在唯一性【基础补充】

在有界开集上，对 $u\in H_0^1(\Omega)$ 有

$$
\|u\|_2\le C_\Omega\|\nabla u\|_2.
$$

因此在 $H_0^1$ 上，$\|\nabla u\|_2$ 是一个与 $\|u\|_{1,2}$ 等价的范数。它在一般 $H^1$ 上通常只是半范数：非零常函数的梯度仍然是零。

一个不需要光滑边界的证明如下。取立方体 $Q=(a,b)^n$ 包含 $\Omega$，先令 $\varphi\in C_c^\infty(\Omega)$，并把它零延拓到 $Q$。固定其余坐标，由微积分基本定理与 Cauchy–Schwarz 不等式，

$$
|\varphi(x_1,x')|^2
=\left|\int_a^{x_1}\partial_1\varphi(t,x')\,dt\right|^2
\le(b-a)\int_a^b|\partial_1\varphi(t,x')|^2\,dt.
$$

对 $Q$ 积分，得到

$$
\|\varphi\|_{L^2(\Omega)}
\le(b-a)\|\partial_1\varphi\|_{L^2(\Omega)}
\le(b-a)\|\nabla\varphi\|_{L^2(\Omega)}.
$$

再利用 $H_0^1$ 的定义，以 $C_c^\infty$ 中的序列逼近 $u$，将不等式传递到极限。

定义双线性型

$$
a(u,\varphi)=\int_\Omega\nabla u\cdot\nabla\varphi\,dx.
$$

它连续，并且由 Poincaré 不等式可得

$$
a(u,u)=\|\nabla u\|_2^2
\ge\frac{1}{1+C_\Omega^2}\|u\|_{1,2}^2.
$$

这种“二次型从下方控制范数平方”的性质叫作**强制性**。Lax–Milgram 定理告诉我们：在 Hilbert 空间上，连续且强制的双线性型对应的变分方程，对每个连续线性右端都有唯一解。因此，对每个 $f\in H^{-1}(\Omega)$，存在唯一 $u\in H_0^1(\Omega)$ 满足上述弱形式，并有

$$
\|u\|_{1,2}\le(1+C_\Omega^2)\|f\|_{H^{-1}}.
$$

这里 Lax–Milgram 定理是为解释板书而补充的工具，不是本次 3.1–3.13 已经证明的结论。其使用条件在上面已经逐项核对。

若 $f\equiv1$，由于 $|\Omega|<\infty$，有 $1\in L^2(\Omega)$，从而

$$
\left|\int_\Omega\varphi\,dx\right|
\le|\Omega|^{1/2}\|\varphi\|_2
\le|\Omega|^{1/2}\|\varphi\|_{1,2}.
$$

所以 $f=1$ 确实给出 $H^{-1}$ 中的右端。

### 11.4 “零边界条件”目前应怎样理解？

在任意开集上，本节最稳妥的表述是

$$
u\in H_0^1(\Omega)
=\overline{C_c^\infty(\Omega)}^{\,H^1}.
$$

这通过逼近定义了零边界条件，不要求每个 Sobolev 等价类都有逐点边界值。在具有适当边界正则性的区域上，后续的迹定理才把这个条件与“迹为零”联系起来。对于一般 $W_0^{m,p}$，也不能未经说明就将下标 $0$ 简化为一个逐点条件 $u|_{\partial\Omega}=0$。

### 11.5 尖点、角点与更高正则性

弱解存在于 $H_0^1$，不等于弱解一定属于 $H^2$。更高正则性会受到区域形状、边界正则性、右端与边界条件的共同影响。

图片给出了带尖点的示意图，但没有足够清晰的区域方程或角度参数；因此不能仅凭图形断定解属于哪个精确的 $H^{1+s}$，也不能确认某个分数指数是最优指数。严谨的题目至少应说明具体区域，并给出相应的正则性定理或要求证明的范围。

本节应先掌握的结论是：**$f\in H^{-1}$ 可以与 $H_0^1$ 中的一阶弱解配对；把弱解进一步提升到更高 Sobolev 空间，是另一个需要额外条件的问题。**

### 11.6 一个可以完整算出的例子

在 $\Omega=(0,1)$ 上，令 $f=1$。函数

$$
u(x)=\frac{x(1-x)}2
$$

满足 $u(0)=u(1)=0$、$-u''=1$，并属于 $H_0^1(0,1)$。例如，利用靠近端点的光滑截断可以在 $H^1$ 中逼近它；端点附近 $u(x)$ 至多按到端点的距离增长，因而截断产生的导数误差也趋于零。

对任意 $\varphi\in C_c^\infty(0,1)$，

$$
\int_0^1u'\varphi'\,dx
=-\int_0^1u''\varphi\,dx
=\int_0^1\varphi\,dx.
$$

由密度和两侧的连续性，这个等式对所有 $\varphi\in H_0^1(0,1)$ 成立。它同时是经典解与弱解，说明弱解概念与经典解相容。

## 12. 考试复习：假设、证明路线与易错点


### 12.1 指数范围必须和结论一起记忆

| 结论 | 本节适用范围 | 必须注意的限制 |
|---|---|---|
| $W^{m,p}$ 是 Banach 空间 | $1\le p\le\infty$ | 完备性证明包括两个端点 |
| $W_0^{m,p}$ 是 Banach 空间 | $1\le p\le\infty$ | 它按定义是 $W^{m,p}$ 的闭子空间 |
| $H^{m,p}\hookrightarrow W^{m,p}$ | 本节按 $1\le p<\infty$ 定义 $H^{m,p}$ | 先得到等距嵌入；等号需要后续密度定理 |
| $W^{m,p}$、$W_0^{m,p}$ 可分 | $1\le p<\infty$ | 不自动包括 $p=\infty$ |
| 一致凸、自反 | $1

### 12.2 证明一：3.3 完备性的答题结构

拿到“证明 $W^{m,p}(\Omega)$ 完备”时，按下面四步组织答案。

1. **逐个导数取极限。** 若 $\{u_j\}$ 是 Sobolev 范数下的 Cauchy 列，则对每个 $|\alpha|\le m$，$\{D^\alpha u_j\}$ 是 $L^p$ 中的 Cauchy 列。由 $L^p$ 完备性，存在 $g_\alpha\in L^p$ 使 $D^\alpha u_j\to g_\alpha$；记 $u=g_0$。
2. **用测试函数传递导数关系。** 对任意 $\varphi\in C_c^\infty(\Omega)$，写出
   
   $$
   \int_\Omega D^\alpha u_j\,\varphi
   =(-1)^{|\alpha|}\int_\Omega u_jD^\alpha\varphi.
   $$
   
   由 Hölder 不等式使两侧分别趋于 $\int g_\alpha\varphi$ 与 $(-1)^{|\alpha|}\int uD^\alpha\varphi$。
3. **识别极限。** 由弱导数定义得 $D^\alpha u=g_\alpha$，所以 $u\in W^{m,p}$。
4. **回到完整范数。** 多重指标只有有限个，逐分量 $L^p$ 收敛推出 $\|u_j-u\|_{m,p}\to0$。

最关键的是第二步。仅说“每个导数都收敛”还不够，必须证明这些极限仍然是同一个函数的弱导数。

### 12.3 证明二：3.9 对偶表示的答题结构

核心路线为

$$
W^{m,p}\xrightarrow{\ P\ }R\subset E_p
\xrightarrow{\text{Hahn–Banach}}E_p
\xrightarrow{\text{$L^p$ 对偶表示}}(v_\alpha)_{|\alpha|\le m}.
$$

准确展开为：

1. $Pu=(D^\alpha u)_\alpha$ 是等距嵌入，$R=P(W^{m,p})$ 是闭子空间。
2. 在 $R$ 上定义 $L^*(Pu)=L(u)$。由 $P$ 单射，它良定义；由等距性，$\|L^*\|=\|L\|$。
3. 用 Hahn–Banach 将 $L^*$ 延拓为 $\widehat L\in E_p'$，并保持范数。
4. 由 $E_p'=E_{p'}$，存在系数组 $v$，使 $\widehat L(U)=\sum_\alpha\int U_\alpha v_\alpha$，且 $\|v\|_{E_{p'}}=\|L\|$。
5. 令 $U=Pu$，得到所需表示。再由 Hölder 说明任意表示的系数范数都不小于 $\|L\|$，从而得到**达到的最小值**。
6. 若题目还要求唯一性，须明确是最小范数表示唯一，并对两个极小元使用 $E_{p'}$ 的严格凸性；这一部分要求 $1<p<\infty$。

不要把 Hahn–Banach 的“存在保范延拓”直接写成“存在唯一保范延拓”。唯一性在这里来自额外的几何性质。

### 12.4 证明三：3.11–3.12 唯一延拓与负阶空间

已知

$$
T=\sum_{|\alpha|\le m}(-1)^{|\alpha|}D^\alpha T_{v_\alpha},
\qquad v\in E_{p'},
$$

先对测试函数证明

$$
|T(\varphi)|\le\|v\|_{E_{p'}}\|\varphi\|_{m,p}.
$$

对于 $u\in W_0^{m,p}$，选 $\varphi_j\to u$ 于 Sobolev 范数，并定义

$$
L_T(u)=\lim_{j\to\infty}T(\varphi_j).
$$

答题时必须交代四件事：极限存在、与逼近序列无关、得到有界线性泛函、延拓唯一。前三件事来自上述估计，最后一件事来自 $C_c^\infty$ 在 $W_0^{m,p}$ 中的稠密性。

反方向从 $L\in(W_0^{m,p})'$ 出发，用 Hahn–Banach 保范延拓到 $W^{m,p}$，再用 3.9 得到系数表示。这个方向同时说明：负范数的下确界可以达到。

### 12.5 高频易错点

| 容易写错的说法 | 应当怎样表述 |
|---|---|
| $D^\alpha u$ 总是经典导数 | 在 $W^{m,p}$ 的定义中，它是弱导数；必须由 $L^p$ 函数表示 |
| 分布导数存在，所以函数属于任意阶 Sobolev 空间 | 每个分布都有各阶分布导数，但导数未必能由 $L^p$ 函数表示 |
| $u_j\to u$ 于 $L^p$，所以 $D u_j\to Du$ 于 $L^p$ | 一般错误；还需要导数收敛等额外条件 |
| $C_c^\infty$ 总在 $W^{m,p}$ 中稠密 | 它按定义在 $W_0^{m,p}$ 中稠密；一般 $W_0^{m,p}\ne W^{m,p}$ |
| $W_0^{m,p}$ 是所有光滑紧支撑函数组成的空间 | 它是这些函数在 Sobolev 范数下的闭包，含有非光滑函数 |
| $\int D^\alpha u\,v=(-1)^{|\alpha|}\int uD^\alpha v$ 总成立 | 必须检查导数、边界与可积性；对测试函数可按分布定义处理 |
| 对偶表示系数组唯一 | 一般不唯一；在 $1

### 12.6 自测题与核对答案

**题 1.** 为什么 Sobolev 范数必须包含 $\alpha=0$ 项？

答：$D^0u=u$。包含这一项能控制函数本身并确保正定性。仅包含最高阶导数时，非零的低次多项式可能具有零半范数，例如 $\nabla1=0$。在特定子空间上可以借助 Poincaré 类不等式用导数范数控制函数，但那是附加结论。

**题 2.** 若 $u_j\to u$、$\partial_i u_j\to g$ 均在 $L^p$ 中成立，为什么 $\partial_i u=g$？

答：对任意测试函数有 $\int\partial_i u_j\varphi=-\int u_j\partial_i\varphi$。利用 Hölder 在两侧取极限，得 $\int g\varphi=-\int u\partial_i\varphi$，即弱导数定义。这个证明不要求逐点导数收敛。

**题 3.** 在 $(0,1)$ 上，能否找到非零的 $W^{1,p}$ 连续线性泛函，其在所有测试函数上都为零？

答：可以。取 $L(u)=\int_0^1u'(x)\,dx$。由 Hölder 它连续；$L(x)=1$，但 $L(\varphi)=0$ 对每个 $\varphi\in C_c^\infty(0,1)$ 成立。它消失于 $W_0^{1,p}$，体现了边界信息。

**题 4.** 在一阶情形，$L(u)=\int uv_0+\sum_j\int\partial_j u\,v_j$ 对应的分布是什么？

答：$T=T_{v_0}-\sum_j\partial_jT_{v_j}$，即 $v_0-\operatorname{div}V$。负号来自分布导数的定义。

**题 5.** 如何构造同一泛函的不同系数表示？

答：在一维取任意 $\psi\in C_c^\infty(0,1)$，则 $\int u\psi'+\int u'\psi=0$ 对 $u\in W^{1,p}(0,1)$ 成立。因此在表示 $(v_0,v_1)$ 上加上 $(\psi',\psi)$，不改变泛函。

**题 6.** 为什么对偶范数公式中是 $\min$？

答：Hölder 给出每组表示系数的范数至少为 $\|L\|$；保范 Hahn–Banach 延拓加上 $L^p$ 对偶表示，构造出一组范数恰为 $\|L\|$ 的系数。上下两方面合起来说明最小值达到。

**题 7.** 已知 $v\in L^{p'}$，为什么 $\|v\|_{-m,p'}\le\|v\|_{p'}$？

答：$|\int uv|\le\|u\|_p\|v\|_{p'}\le\|u\|_{m,p}\|v\|_{p'}$，再对 $W_0^{m,p}$ 的单位球取上确界。取上确界时的约束是 Sobolev 范数，不是单独的 $L^p$ 范数。

**题 8.** $W^{-m,p'}$ 中的“负阶”是否意味着“把函数积分 $m$ 次”？

答：不是。它首先表示 $W_0^{m,p}$ 的连续对偶，等价地可以由不超过 $m$ 阶的 $L^{p'}$ 函数分布导数组合表示。负阶是可测试的正则性尺度，不是一个未经定义的不定积分操作。

**题 9.** 为什么从 $W_0^{m,p}$ 的对偶到分布的映射是单射，而从 $W^{m,p}$ 的对偶到分布的限制映射可能不是？

答：测试函数在前一个空间中稠密，所以连续泛函在测试函数上的值决定它在整个空间中的值；在后一个空间中测试函数的闭包通常只是 $W_0^{m,p}$，因此还可能存在消失于这一闭包的非零泛函。

**题 10.** 写出二维 $W^{2,2}$ 的内积。

答：对 $u,v\in W^{2,2}(\Omega)$，

$$
(u,v)_{2,2}
=\int_\Omega\bigl(
u\overline v
+u_x\overline{v_x}+u_y\overline{v_y}
+u_{xx}\overline{v_{xx}}
+u_{xy}\overline{v_{xy}}
+u_{yy}\overline{v_{yy}}
\bigr)\,dx\,dy.
$$

这里混合导数 $u_{xy}$ 作为一个多重指标只出现一次。如果改用 Hessian 矩阵的 Frobenius 内积，则混合项通常出现两次；那给出的是另一种等价约定，不能不加说明地混写。

### 12.7 建议的复习顺序

第一遍先读第 1–3 节，确保能独立写出弱导数定义与 3.3 的四步证明。第二遍读第 5–7 节，理解 $Pu=(D^\alpha u)_\alpha$ 如何把 Sobolev 问题转成有限乘积 $L^p$ 问题，并复述 Hahn–Banach 的使用位置。第三遍读第 8–10 节，围绕“边界信息是否丢失”和“测试函数在哪个空间中稠密”理解负阶空间。最后用本节自测题检查，而不只背诵定理名称。

