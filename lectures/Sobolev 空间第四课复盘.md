# 第四课复盘：分布、分布导数与弱导数

> 教材范围：1.55—1.63
> 主题主线：试验函数 $\longrightarrow$ 分布 $\longrightarrow$ 分布导数 $\longrightarrow$ 弱导数

## 0. 本节课的逻辑主线

经典导数要求函数具有足够的点态光滑性，但很多重要函数并不满足这一要求。例如，Heaviside 函数在原点跳跃，$|x|$ 在原点不可导，$\log |x|$ 的经典导数 $1/x$ 在原点附近甚至不可积。

分布理论的基本思想是：不再直接观察函数在每一点的值，而是观察它对所有光滑、紧支撑试验函数的作用。这样可以把“求导”转移到试验函数上：

$$
\int_\Omega D^\alpha u\,\varphi\,dx
=(-1)^{|\alpha|}\int_\Omega uD^\alpha\varphi\,dx.
$$

右边即使在 $u$ 不可经典求导时也可能有意义，于是可以反过来把它作为广义导数的定义。本节内容的结构为

$$
C_c^\infty(\Omega)
\longrightarrow \mathcal D(\Omega)
\longrightarrow \mathcal D'(\Omega)
\longrightarrow D^\alpha T
\longrightarrow D^\alpha u\text{（弱导数）}.
$$

---

## 1.55 为什么要引入分布

设 $\Omega\subset\mathbb R^n$ 是开集。Sobolev 空间的核心是弱导数，而弱导数最自然的语言就是分布。

分布理论要解决两个问题：

1. 怎样把普通函数看成线性泛函；
2. 怎样让不光滑对象也能任意次求导。

这里会频繁使用多重指标

$$
\alpha=(\alpha_1,\ldots,\alpha_n),\qquad
|\alpha|=\alpha_1+\cdots+\alpha_n,
$$

以及

$$
D^\alpha
=\frac{\partial^{|\alpha|}}
{\partial x_1^{\alpha_1}\cdots\partial x_n^{\alpha_n}}.
$$

记号 $K\Subset\Omega$ 表示 $K$ 是 $\Omega$ 的紧子集。换言之，$K$ 是紧集，并且与边界 $\partial\Omega$ 保持正距离。

---

## 1.56 试验函数空间 $\mathcal D(\Omega)$

### 1.56.1 试验函数

定义

$$
\mathcal D(\Omega):=C_c^\infty(\Omega).
$$

其元素称为试验函数。也就是说，$\varphi\in\mathcal D(\Omega)$ 同时满足：

- $\varphi$ 在 $\Omega$ 内任意阶光滑；
- $\mathrm{supp}\,\varphi$ 是 $\Omega$ 的紧子集。

其中

$$
\mathrm{supp}\,\varphi
=\overline{\{x\in\Omega:\varphi(x)\ne0\}}
$$

称为 $\varphi$ 的支集。

试验函数之所以重要，是因为它在靠近 $\partial\Omega$ 的地方恒为零。因此对其分部积分时不会出现边界项。

### 1.56.2 $\mathcal D(\Omega)$ 中的收敛

称 $\varphi_j\to\varphi$ 于 $\mathcal D(\Omega)$，若满足：

1. 存在一个固定的 $K\Subset\Omega$，使得
   
   $$
   \mathrm{supp}(\varphi_j-\varphi)\subset K,
   \qquad j=1,2,\ldots;
   $$
2. 对每个多重指标 $\alpha$，都有
   
   $$
   \sup_{x\in K}
   |D^\alpha\varphi_j(x)-D^\alpha\varphi(x)|
   \longrightarrow0.
   $$

这里两个条件缺一不可。仅有逐点收敛，甚至仅有每阶导数的局部一致收敛，都不足以保证 $\mathcal D(\Omega)$ 中的收敛；所有函数的支集还必须被同一个紧集控制。

### 1.56.3 一个立即可用的结论

若 $\varphi_j\to\varphi$ 于 $\mathcal D(\Omega)$，则对任意多重指标 $\alpha$，

$$
D^\alpha\varphi_j\to D^\alpha\varphi
\qquad\text{于 }\mathcal D(\Omega).
$$

原因是求导不会扩大支集，并且

$$
D^\beta(D^\alpha\varphi_j-D^\alpha\varphi)
=D^{\alpha+\beta}(\varphi_j-\varphi)
$$

在固定紧集 $K$ 上一致趋于零。

---

## 1.57 Schwartz 分布 $\mathcal D'(\Omega)$

### 1.57.1 定义

试验函数空间 $\mathcal D(\Omega)$ 上的连续线性泛函称为 $\Omega$ 上的 Schwartz 分布。所有分布组成的空间记为

$$
\mathcal D'(\Omega).
$$

因此，$T\in\mathcal D'(\Omega)$ 意味着：

1. 线性：
   
   $$
   T(a\varphi+b\psi)=aT(\varphi)+bT(\psi);
   $$
2. 连续：若 $\varphi_j\to\varphi$ 于 $\mathcal D(\Omega)$，则
   
   $$
   T(\varphi_j)\to T(\varphi).
   $$

分布并不一定是普通函数。它首先是一个“输入试验函数、输出数”的映射。

### 1.57.2 分布的收敛

称 $T_j\to T$ 于 $\mathcal D'(\Omega)$，若对每个 $\varphi\in\mathcal D(\Omega)$，

$$
T_j(\varphi)\longrightarrow T(\varphi).
$$

这就是逐个试验函数检验的收敛，也可看作 $\mathcal D'(\Omega)$ 上的弱星收敛。

> 不要混淆两种收敛：$\varphi_j\to\varphi$ 是试验函数空间中的强条件；$T_j\to T$ 则只要求对每个固定试验函数的作用值收敛。

---

## 1.58 局部可积函数所诱导的正则分布

### 1.58.1 局部可积

若 $u$ 在 $\Omega$ 上几乎处处有定义，并且对每个 $K\Subset\Omega$ 都有

$$
\int_K|u(x)|\,dx<\infty,
$$

则称 $u$ 在 $\Omega$ 上局部可积，记为

$$
u\in L^1_{\mathrm{loc}}(\Omega).
$$

等价地，对每个相对紧开集 $U\Subset\Omega$，都有 $u\in L^1(U)$。

### 1.58.2 从函数构造分布

对 $u\in L^1_{\mathrm{loc}}(\Omega)$，定义

$$
T_u(\varphi):=\int_\Omega u(x)\varphi(x)\,dx,
\qquad \varphi\in\mathcal D(\Omega).
$$

由局部可积函数诱导的分布称为正则分布。

### 1.58.3 证明：$T_u$ 确实是分布

#### 第一步：良定义

给定 $\varphi\in\mathcal D(\Omega)$，令 $K=\mathrm{supp}\,\varphi\Subset\Omega$。则

$$
|T_u(\varphi)|
\le \int_K|u(x)|\,|\varphi(x)|\,dx
\le \|\varphi\|_{C(K)}\int_K|u(x)|\,dx<\infty.
$$

因此积分是有限的，$T_u(\varphi)$ 有意义。

#### 第二步：线性

积分的线性直接给出

$$
T_u(a\varphi+b\psi)
=aT_u(\varphi)+bT_u(\psi).
$$

#### 第三步：连续性

若 $\varphi_j\to\varphi$ 于 $\mathcal D(\Omega)$，则存在固定的 $K\Subset\Omega$，使得所有 $\varphi_j-\varphi$ 的支集均包含于 $K$，并且

$$
\|\varphi_j-\varphi\|_{C(K)}\to0.
$$

于是

$$
\begin{aligned}
|T_u(\varphi_j)-T_u(\varphi)|
&=\left|\int_Ku(x)(\varphi_j(x)-\varphi(x))\,dx\right|\\
&\le \|\varphi_j-\varphi\|_{C(K)}
\int_K|u(x)|\,dx\\
&\longrightarrow0.
\end{aligned}
$$

故 $T_u\in\mathcal D'(\Omega)$。

### 1.58.4 函数到分布的对应是单射

一个以后反复使用的基本事实是：若 $u,v\in L^1_{\mathrm{loc}}(\Omega)$，则

$$
T_u=T_v
\quad\Longleftrightarrow\quad
u=v\quad\text{几乎处处}.
$$

只需证明：若

$$
\int_\Omega u\varphi\,dx=0,
\qquad\forall\varphi\in\mathcal D(\Omega),
$$

则 $u=0$ 几乎处处。这一结论称为变分法基本引理或分布基本引理。

一个严谨证明可借助后面介绍的磨光核。取标准磨光核 $\rho_\varepsilon$。对任意 $K\Subset\Omega$，当 $\varepsilon$ 足够小时，对 $x\in K$ 有

$$
(u*\rho_\varepsilon)(x)
=\int_\Omega u(y)\rho_\varepsilon(x-y)\,dy=0,
$$

因为 $y\mapsto\rho_\varepsilon(x-y)$ 是试验函数。另一方面，近似恒等算子定理给出

$$
u*\rho_\varepsilon\to u
\qquad\text{于 }L^1(K).
$$

所以 $u=0$ 几乎处处于 $K$。由于 $K\Subset\Omega$ 任意，故 $u=0$ 几乎处处于 $\Omega$。

这也说明在分布理论中，彼此仅在零测集上不同的函数代表同一个正则分布。

---

## 1.59 Dirac 分布与非正则分布

设 $x_0\in\Omega$。定义

$$
\delta_{x_0}(\varphi):=\varphi(x_0),
\qquad\varphi\in\mathcal D(\Omega).
$$

当 $x_0=0$ 时简写为 $\delta$。

### 1.59.1 为什么 $\delta_{x_0}$ 是分布

线性显然成立。若 $\varphi_j\to\varphi$ 于 $\mathcal D(\Omega)$，则特别有一致收敛，因此

$$
|\delta_{x_0}(\varphi_j)-\delta_{x_0}(\varphi)|
=|\varphi_j(x_0)-\varphi(x_0)|
\le\|\varphi_j-\varphi\|_{C(K)}	o0.
$$

故 $\delta_{x_0}\in\mathcal D'(\Omega)$。

### 1.59.2 为什么 Dirac 分布不是普通函数

不存在 $u\in L^1_{\mathrm{loc}}(\Omega)$ 使得 $T_u=\delta_{x_0}$。

反证。若存在这样的 $u$，对任意支集不含 $x_0$ 的试验函数 $\varphi$，有

$$
\int_\Omega u\varphi\,dx
=\delta_{x_0}(\varphi)=0.
$$

由上一节的基本引理，$u=0$ 几乎处处于 $\Omega\setminus\{x_0\}$。单点集的 Lebesgue 测度为零，所以 $u=0$ 几乎处处于 $\Omega$，从而 $T_u=0$，这与 $\delta_{x_0}\ne0$ 矛盾。

因此

$$
L^1_{\mathrm{loc}}(\Omega)
\subsetneq \mathcal D'(\Omega).
$$

### 1.59.3 Dirac 分布与卷积

在卷积有意义时，

$$
(\delta_0*\varphi)(x)
=\delta_0\bigl(y\mapsto\varphi(x-y)\bigr)
=\varphi(x).
$$

更一般地，

$$
(\delta_{x_0}*\varphi)(x)=\varphi(x-x_0).
$$

因此 $\delta_0$ 是卷积运算的单位元。

### 1.59.4 磨光核逼近 Dirac 分布

取 $\rho\in C_c^\infty(\mathbb R^n)$，满足

$$
\rho\ge0,\qquad
\int_{\mathbb R^n}\rho(x)\,dx=1,
\qquad
\mathrm{supp}\,\rho\subset B_1(0).
$$

定义

$$
\rho_\varepsilon(x)
=\varepsilon^{-n}\rho\left(\frac{x}{\varepsilon}\right).
$$

则

$$
\int_{\mathbb R^n}\rho_\varepsilon(x)\,dx=1,
\qquad
\mathrm{supp}\,\rho_\varepsilon\subset B_\varepsilon(0).
$$

对任意 $\varphi\in\mathcal D(\mathbb R^n)$，作变量替换 $x=\varepsilon y$：

$$
\begin{aligned}
T_{\rho_\varepsilon}(\varphi)
&=\int_{\mathbb R^n}\rho_\varepsilon(x)\varphi(x)\,dx\\
&=\int_{\mathbb R^n}\rho(y)\varphi(\varepsilon y)\,dy\\
&\longrightarrow \varphi(0)
=\delta_0(\varphi).
\end{aligned}
$$

故

$$
T_{\rho_\varepsilon}\longrightarrow\delta_0
\qquad\text{于 }\mathcal D'(\mathbb R^n).
$$

这就是板书中“支集不断收缩、峰值不断升高、总质量保持为 $1$”的严格含义。注意：$\rho_\varepsilon(0)$ 通常趋于无穷，但分布收敛考察的是积分作用，而不是逐点收敛。

### 1.59.5 高斯核逼近 Dirac 分布

一维中取归一化高斯核

$$
G_\sigma(x)
=\frac{1}{\sqrt{2\pi}\,\sigma}
\exp\left(-\frac{x^2}{2\sigma^2}\right),
\qquad \sigma>0.
$$

归一化常数来自

$$
\int_{-\infty}^{\infty}
\exp\left(-\frac{x^2}{2\sigma^2}\right)dx
=\sqrt{2\pi}\,\sigma.
$$

对任意 $\varphi\in\mathcal D(\mathbb R)$，令 $x=\sigma y$，得

$$
T_{G_\sigma}(\varphi)
=\int_{\mathbb R}\frac{1}{\sqrt{2\pi}}
e^{-y^2/2}\varphi(\sigma y)\,dy.
$$

当 $\sigma\downarrow0$ 时，$\varphi(\sigma y)\to\varphi(0)$，并且

$$
\left|\frac{1}{\sqrt{2\pi}}e^{-y^2/2}\varphi(\sigma y)\right|
\le \frac{\|\varphi\|_\infty}{\sqrt{2\pi}}e^{-y^2/2}.
$$

右端可积，由控制收敛定理，

$$
T_{G_\sigma}(\varphi)
\longrightarrow
\varphi(0)\int_{\mathbb R}\frac{1}{\sqrt{2\pi}}e^{-y^2/2}\,dy
=\varphi(0).
$$

因此

$$
T_{G_\sigma}\longrightarrow\delta_0
\qquad\text{于 }\mathcal D'(\mathbb R).
$$

在 $\mathbb R^n$ 中相应的核为

$$
G_\sigma(x)
=(2\pi\sigma^2)^{-n/2}
\exp\left(-\frac{|x|^2}{2\sigma^2}\right).
$$

---

## 1.60 分布的导数

### 1.60.1 定义的来源：分部积分

若 $u\in C^1(\Omega)$，$\varphi\in\mathcal D(\Omega)$，则由于 $\varphi$ 在边界附近为零，

$$
\int_\Omega \frac{\partial u}{\partial x_j}\varphi\,dx
=-\int_\Omega u\frac{\partial\varphi}{\partial x_j}\,dx.
$$

更一般地，若 $u$ 足够光滑，则

$$
\int_\Omega(D^\alpha u)\varphi\,dx
=(-1)^{|\alpha|}\int_\Omega uD^\alpha\varphi\,dx.
$$

于是对任意 $T\in\mathcal D'(\Omega)$，定义其分布导数为

$$
(D^\alpha T)(\varphi)
:=(-1)^{|\alpha|}T(D^\alpha\varphi),
\qquad\varphi\in\mathcal D(\Omega).
$$

负号并不是人为添加的，而是为了使分布导数与经典导数在光滑函数上完全一致。

### 1.60.2 证明：$D^\alpha T$ 仍是分布

线性显然。下面证明连续性。

若 $\varphi_j\to\varphi$ 于 $\mathcal D(\Omega)$，由 1.56.3，

$$
D^\alpha\varphi_j\to D^\alpha\varphi
\qquad\text{于 }\mathcal D(\Omega).
$$

利用 $T$ 的连续性，

$$
\begin{aligned}
D^\alpha T(\varphi_j)
&=(-1)^{|\alpha|}T(D^\alpha\varphi_j)\\
&\longrightarrow
(-1)^{|\alpha|}T(D^\alpha\varphi)\\
&=D^\alpha T(\varphi).
\end{aligned}
$$

所以 $D^\alpha T\in\mathcal D'(\Omega)$。

由此得到一个非常重要的结论：

> 每个分布都具有任意阶分布导数。

### 1.60.3 求导运算在分布空间中连续

若 $T_j\to T$ 于 $\mathcal D'(\Omega)$，则对每个 $\varphi\in\mathcal D(\Omega)$，

$$
\begin{aligned}
D^\alpha T_j(\varphi)
&=(-1)^{|\alpha|}T_j(D^\alpha\varphi)\\
&\longrightarrow
(-1)^{|\alpha|}T(D^\alpha\varphi)\\
&=D^\alpha T(\varphi).
\end{aligned}
$$

因此

$$
T_j\to T\text{ 于 }\mathcal D'
\quad\Longrightarrow\quad
D^\alpha T_j\to D^\alpha T\text{ 于 }\mathcal D'.
$$

这表示在分布意义下可以安全地交换“取极限”和“求导”。

---

## 1.61 分布导数的典型例子

### 1.61.1 Dirac 分布的导数

由定义，

$$
D^\alpha\delta_0(\varphi)
=(-1)^{|\alpha|}\delta_0(D^\alpha\varphi)
=(-1)^{|\alpha|}D^\alpha\varphi(0).
$$

更一般地，

$$
D^\alpha\delta_{x_0}(\varphi)
=(-1)^{|\alpha|}D^\alpha\varphi(x_0).
$$

### 1.61.2 Heaviside 函数的分布导数

定义

$$
H(x)=
\begin{cases}
1,&x\ge0,\\
0,&x<0.
\end{cases}
$$

它诱导的正则分布为

$$
T_H(\varphi)=\int_0^\infty\varphi(x)\,dx.
$$

于是

$$
\begin{aligned}
T_H'(\varphi)
&=-T_H(\varphi')\\
&=-\int_0^\infty\varphi'(x)\,dx\\
&=\varphi(0)\\
&=\delta_0(\varphi).
\end{aligned}
$$

故

$$
H'=\delta_0
\qquad\text{于 }\mathcal D'(\mathbb R).
$$

这说明函数在某点发生单位跳跃时，其分布导数会在该点产生一个 Dirac 质量。

### 1.61.3 $\log|x|$ 的分布导数

函数

$$
u(x)=\log|x|
$$

属于 $L^1_{\mathrm{loc}}(\mathbb R)$，因为

$$
\int_0^1|\log x|\,dx<\infty.
$$

但其经典导数 $1/x$ 不属于 $L^1_{\mathrm{loc}}(\mathbb R)$。因此不能简单写成 $T_u'=T_{1/x}$。

定义 $1/x$ 的 Cauchy 主值分布：

$$
\mathrm{p.v.}\frac1x(\varphi)
:=\lim_{\varepsilon\downarrow0}
\left(
\int_{-\infty}^{-\varepsilon}\frac{\varphi(x)}x\,dx
+\int_\varepsilon^\infty\frac{\varphi(x)}x\,dx
\right).
$$

这个极限存在。事实上，在原点附近可将对称部分写成

$$
\int_\varepsilon^a
\frac{\varphi(x)-\varphi(-x)}x\,dx.
$$

由中值定理，$|\varphi(x)-\varphi(-x)|\le C|x|$，所以被积函数在原点附近有界。

现在计算 $T_{\log|x|}'$。设 $\mathrm{supp}\,\varphi\subset[-a,a]$。对 $(-a,-\varepsilon)$ 与 $(\varepsilon,a)$ 分别分部积分：

$$
\begin{aligned}
T_{\log|x|}'(\varphi)
&=-\lim_{\varepsilon\downarrow0}
\left(
\int_{-a}^{-\varepsilon}\log|x|\,\varphi'(x)\,dx
+\int_\varepsilon^a\log|x|\,\varphi'(x)\,dx
\right)\\
&=\lim_{\varepsilon\downarrow0}
\left(
\int_{-a}^{-\varepsilon}\frac{\varphi(x)}x\,dx
+\int_\varepsilon^a\frac{\varphi(x)}x\,dx
+\log\varepsilon\,[\varphi(\varepsilon)-\varphi(-\varepsilon)]
\right).
\end{aligned}
$$

由中值定理，

$$
|\varphi(\varepsilon)-\varphi(-\varepsilon)|
\le2\varepsilon\|\varphi'\|_\infty,
$$

而 $\varepsilon|\log\varepsilon|\to0$，故最后的边界项趋于零。因此

$$
(\log|x|)'
=\mathrm{p.v.}\frac1x
\qquad\text{于 }\mathcal D'(\mathbb R).
$$

这正是“分布导数存在，但不能由普通局部可积函数 $1/x$ 表示”的典型例子。

---

## 1.62 弱导数

### 1.62.1 定义

设 $u\in L^1_{\mathrm{loc}}(\Omega)$。如果存在 $v_\alpha\in L^1_{\mathrm{loc}}(\Omega)$，使得

$$
T_{v_\alpha}=D^\alpha T_u
\qquad\text{于 }\mathcal D'(\Omega),
$$

则称 $v_\alpha$ 是 $u$ 的 $\alpha$ 阶弱导数或分布导数，并记为

$$
D^\alpha u=v_\alpha.
$$

展开定义，这等价于：对所有 $\varphi\in\mathcal D(\Omega)$，

$$
\int_\Omega u(x)D^\alpha\varphi(x)\,dx
=(-1)^{|\alpha|}
\int_\Omega v_\alpha(x)\varphi(x)\,dx.
$$

### 1.62.2 弱导数的唯一性

若 $v_\alpha,w_\alpha\in L^1_{\mathrm{loc}}(\Omega)$ 都是 $u$ 的弱导数，则

$$
T_{v_\alpha}=D^\alpha T_u=T_{w_\alpha}.
$$

因此

$$
T_{v_\alpha-w_\alpha}=0.
$$

由 1.58.4 的基本引理，

$$
v_\alpha=w_\alpha
\qquad\text{几乎处处}.
$$

所以弱导数按“几乎处处相等”的意义唯一。

### 1.62.3 经典导数一定是弱导数

若 $u$ 具有连续的经典导数 $D^\alpha u$，则反复分部积分可得

$$
\int_\Omega uD^\alpha\varphi,dx
=(-1)^{|\alpha|}
\int_\Omega(D^\alpha u)\varphi,dx.
$$

所以经典导数与弱导数一致。

反过来不成立：函数可以没有经典导数，却存在弱导数。

### 1.62.4 例：$|x|$ 的弱导数

令 $u(x)=|x|$。其经典导数在 $x=0$ 不存在，但定义

$$
v(x)=\mathrm{sgn}(x)=
\begin{cases}
1,&x>0,\\
-1,&x<0.
\end{cases}
$$

则对任意 $\varphi\in\mathcal D(\mathbb R)$，分段积分得

$$
\begin{aligned}
\int_\mathbb R|x|\varphi'(x)\,dx
&=\int_{-\infty}^0(-x)\varphi'(x)\,dx
+\int_0^\infty x\varphi'(x)\,dx\\
&=-\int_\mathbb R\mathrm{sgn}(x)\varphi(x)\,dx.
\end{aligned}
$$

故

$$
u'=\mathrm{sgn}(x)
\qquad\text{几乎处处，且为弱导数}.
$$

### 1.62.5 “分布导数”与“弱导数”并不完全等同

这是本节最容易混淆的地方：

- 对每个 $T\in\mathcal D'(\Omega)$，$D^\alpha T$ 总是存在，并仍是分布；
- 对 $u\in L^1_{\mathrm{loc}}(\Omega)$，只有当 $D^\alpha T_u$ 能由某个局部可积函数表示时，才说 $u$ 具有教材意义下的弱导数。

例如，Heaviside 函数满足

$$
D T_H=\delta_0,
$$

但 $\delta_0$ 不是正则分布。因此 $H$ 有分布导数，却没有属于 $L^1_{\mathrm{loc}}(\mathbb R)$ 的弱导数。

同理，$\log|x|$ 的分布导数是 $\mathrm{p.v.}(1/x)$，它也不是由 $L^1_{\mathrm{loc}}$ 函数表示的弱导数。

---

## 1.63 光滑函数与分布的乘积

设 $T\in\mathcal D'(\Omega)$，$\omega\in C^\infty(\Omega)$。定义

$$
(\omega T)(\varphi):=T(\omega\varphi),
\qquad\varphi\in\mathcal D(\Omega).
$$

因为 $\omega\varphi\in\mathcal D(\Omega)$，所以该定义有意义，并且 $\omega T\in\mathcal D'(\Omega)$。

若 $T=T_u$，其中 $u\in L^1_{\mathrm{loc}}(\Omega)$，则

$$
(\omega T_u)(\varphi)
=\int_\Omega u\omega\varphi\,dx
=T_{\omega u}(\varphi),
$$

即

$$
\omega T_u=T_{\omega u}.
$$

### 1.63.1 分布版本的 Leibniz 公式

先看一阶导数。对任意 $\varphi\in\mathcal D(\Omega)$，

$$
\begin{aligned}
D_j(\omega T)(\varphi)
&=-(\omega T)(D_j\varphi)\\
&=-T(\omega D_j\varphi)\\
&=-T\bigl(D_j(\omega\varphi)-(D_j\omega)\varphi\bigr)\\
&=(\omega D_jT)(\varphi)+((D_j\omega)T)(\varphi).
\end{aligned}
$$

因此

$$
D_j(\omega T)=\omega D_jT+(D_j\omega)T.
$$

推广到任意多重指标，

$$
D^\alpha(\omega T)
=\sum_{\beta\le\alpha}
\binom{\alpha}{\beta}
(D^\beta\omega)D^{\alpha-\beta}T,
$$

其中

$$
\binom{\alpha}{\beta}
=\prod_{j=1}^n\binom{\alpha_j}{\beta_j}.
$$

这说明经典微积分中的乘积求导法则可以完整地延伸到分布空间。

---

## 2. 核心结论总表

| 对象 | 定义或结论 | 关键含义 |
|---|---|---|
| 试验函数 | $\mathcal D(\Omega)=C_c^\infty(\Omega)$ | 光滑且紧支撑，可无边界项地分部积分 |
| 分布 | $\mathcal D'(\Omega)=\mathcal D(\Omega)$ 上的连续线性泛函 | 广义函数 |
| 正则分布 | $T_u(\varphi)=\int u\varphi$ | 把 $L^1_{\mathrm{loc}}$ 函数嵌入分布空间 |
| Dirac 分布 | $\delta_{x_0}(\varphi)=\varphi(x_0)$ | 不是普通局部可积函数 |
| 分布导数 | $D^\alpha T(\varphi)=(-1)^{|\alpha|}T(D^\alpha\varphi)$ | 每个分布都可任意次求导 |
| 弱导数 | $T_v=D^\alpha T_u$，其中 $v\in L^1_{\mathrm{loc}}$ | 分布导数恰好还能由函数表示 |
| Heaviside 导数 | $H'=\delta_0$ | 跳跃产生 Dirac 质量 |
| 对数导数 | $(\log\|x\|)'=\mathrm{p.v.}(1/x)$ | 奇异性由主值分布表达 |
| 磨光核 | $T_{\rho_\varepsilon}\to\delta_0$ | 平滑函数可在分布意义下逼近点质量 |
| 光滑乘子 | $(\omega T)(\varphi)=T(\omega\varphi)$ | 分布可与光滑函数相乘 |

---

