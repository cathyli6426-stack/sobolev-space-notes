# 第八课复盘：$L^p$ 紧性、一致凸性与对偶表示

_教材范围：2.31—2.44；根据课堂讲义、批注和板书整理。本文以复值 $L^p$ 为一般情形，实值情形只需去掉共轭。_

---

## 📋 本节课的逻辑主线与记号

本节课依次回答三个问题：一族 $L^p$ 函数何时能抽出强收敛子列？为什么 $1<p<\infty$ 的 $L^p$ 具有比一般 Banach 空间更强的几何性质？每个 $L^p$ 上的连续线性泛函能否由积分表示？

$$
\begin{aligned}
&\text{一致的尾部控制}+\text{一致的平移连续性}
\Longrightarrow L^p\text{ 中的预紧性};\\
&\text{标量不等式}\Longrightarrow\text{Clarkson 不等式}
\Longrightarrow L^p\text{ 一致凸}\Longrightarrow L^p\text{ 自反};\\
&\text{一致凸性保证范数取到}+\text{范数的变分导数}
\Longrightarrow (L^p)'\cong L^{p'}\quad(1<p<\infty).
\end{aligned}
$$

全文约定 $\Omega\subset\mathbb R^n$ 为开集，$1\le p<\infty$ 时 $\|u\|_p=(\int_\Omega|u|^p)^{1/p}$，共轭指数满足 $1/p+1/p'=1$。$K\Subset\Omega$ 表示 $K$ 是 $\Omega$ 的紧子集。**预紧**指闭包紧；在完备的 $L^p$ 空间中，这等价于任意序列都有强收敛子列，也等价于对每个 $\varepsilon>0$ 存在有限 $\varepsilon$ 网。

若 $u\in L^p(\Omega)$，其**零延拓**记为

$$
\widetilde u(x)=
\begin{cases}
u(x),&x\in\Omega,\\
0,&x\notin\Omega.
\end{cases}
\qquad
\|\widetilde u\|_{L^p(\mathbb R^n)}=\|u\|_{L^p(\Omega)}.
$$

零延拓只是可测函数的定义，不预设边界上的连续性或 Sobolev 延拓性质。以下 $T_hf(x)=f(x+h)$，因此 $\|T_hf\|_p=\|f\|_p$。

---

## 🧩 2.31—2.33：$L^p$ 中的预紧性

### 2.31 为什么要寻找 $L^p$ 版 Arzelà–Ascoli 定理

连续函数族的预紧性常用一致有界和等度连续刻画。$L^p$ 函数只按几乎处处相等的意义确定，不能直接逐点比较，故改用两种范数条件：

1. **一致平移连续性**：小幅平移在 $L^p$ 范数中同时改变得很少。
2. **一致紧性**：所有函数的 $L^p$ 质量同时集中在某个固定紧集附近；即质量不会向无穷远或 $\partial\Omega$ 逃逸。

有界性本身不够。例如 $u_k=\mathbf1_{(k,k+1)}$ 在 $L^p(\mathbb R)$ 中有界，但质量不断远移；$u_k(x)=e^{ikx}\mathbf1_{(0,1)}(x)$ 则说明没有统一平移控制时可能出现越来越快的振荡。

### 2.32 紧性判别定理的准确表述

**定理。** 设 $1\le p<\infty$，$\mathcal K\subset L^p(\Omega)$ 有界。则 $\mathcal K$ 预紧，当且仅当对每个 $\varepsilon>0$，均存在 $G\Subset\Omega$ 与 $\delta>0$，使所有 $u\in\mathcal K$ 及 $|h|<\delta$ 同时满足

$$
\int_{\Omega\setminus G}|u(x)|^p\,dx<\varepsilon^p,
\qquad
\int_\Omega|\widetilde u(x+h)-\widetilde u(x)|^p\,dx<\varepsilon^p.
\qquad\text{(2.32)}
$$

教材第二个积分只写在 $\Omega$ 上；标准的 Fréchet–Kolmogorov 判据常将它写在 $\mathbb R^n$ 上。这里两种写法在第一项的**统一尾部条件**下等价，不能孤立地把其中一项换成另一项。证明如下。

记 $d=\operatorname{dist}(G,\mathbb R^n\setminus\Omega)>0$。若 $|h|<d$，则

$$
\begin{aligned}
\int_{\mathbb R^n\setminus\Omega}
|\widetilde u(x+h)-\widetilde u(x)|^p\,dx
&=\int_{\{y\in\Omega:y-h\notin\Omega\}}|u(y)|^p\,dy\\
&\le\int_{\Omega\setminus G}|u(y)|^p\,dy.
\end{aligned}
$$

因为 $y\in G$ 且 $|h|<d$ 时必有 $y-h\in\Omega$。故

$$
\|T_h\widetilde u-\widetilde u\|_{L^p(\mathbb R^n)}^p
\le
\int_\Omega|\widetilde u(x+h)-\widetilde u(x)|^p\,dx
+\int_{\Omega\setminus G}|u|^p.
\qquad\text{(A)}
$$

这一步解释了边界处看似“少算了”的平移质量如何由尾部条件补齐。

#### 必要性：从有限网得到两项统一估计

假定 $\mathcal K$ 预紧。固定 $\varepsilon>0$。先在 $\mathcal K$ 中选有限范数网，再利用 $C_c(\Omega)$ 在 $L^p(\Omega)$ 中的稠密性，可得到有限集 $S\subset C_c(\Omega)$，使每个 $u\in\mathcal K$ 都有 $\phi\in S$ 满足 $\|u-\phi\|_p<\varepsilon/3$。令 $G$ 包含 $S$ 中各函数支撑的并，并取为 $\Omega$ 的紧子集。于是

$$
\|u\|_{L^p(\Omega\setminus G)}
=\|u-\phi\|_{L^p(\Omega\setminus G)}<\varepsilon/3.
$$

每个 $\widetilde\phi\in C_c(\mathbb R^n)$ 的平移在 $L^p$ 中连续；由于 $S$ 有限，存在统一的 $\delta>0$，使 $|h|<\delta$ 时对全部 $\phi\in S$ 有 $\|T_h\widetilde\phi-\widetilde\phi\|_p<\varepsilon/3$。平移保持 $L^p$ 范数，所以

$$
\begin{aligned}
\|T_h\widetilde u-\widetilde u\|_p
&\le\|T_h(\widetilde u-\widetilde\phi)\|_p
+\|T_h\widetilde\phi-\widetilde\phi\|_p
+\|\widetilde\phi-\widetilde u\|_p\\
&<\varepsilon.
\end{aligned}
$$

这还顺便证明了：对任意单个 $f\in L^p(\mathbb R^n)$，$\|T_hf-f\|_p\to0$；有限网使这一连续性对预紧族一致成立。

#### 充分性：磨光、Arzelà–Ascoli 与有限网

先由 (A) 将教材的条件改写为对零延拓族 $\widetilde{\mathcal K}$ 的全空间一致平移连续性。记上一课构造的非负磨光核为 $J_\eta$，$\int J_\eta=1$，$\operatorname{supp}J_\eta\subset\overline B_\eta(0)$。Minkowski 积分不等式给出

$$
\begin{aligned}
\|J_\eta*\widetilde u-\widetilde u\|_p
&=\left\|\int J_\eta(y)(T_{-y}\widetilde u-\widetilde u)\,dy\right\|_p\\
&\le\int J_\eta(y)\|T_{-y}\widetilde u-\widetilde u\|_p\,dy\\
&\le\sup_{|y|<\eta}\|T_{-y}\widetilde u-\widetilde u\|_p.
\end{aligned}
\qquad\text{(B)}
$$

故 $\eta\downarrow0$ 时，$J_\eta*\widetilde u\to\widetilde u$ **对 $u\in\mathcal K$ 一致地在 $L^p$ 中成立**。这是单个函数的磨光收敛之外最关键的额外结论。

固定足够小的 $\eta$。设 $M=\sup_{u\in\mathcal K}\|u\|_p<\infty$。Hölder 不等式及平移核的连续性给出

$$
\begin{aligned}
|J_\eta*\widetilde u(x)|&\le M\|J_\eta\|_{p'},\\
|J_\eta*\widetilde u(x+h)-J_\eta*\widetilde u(x)|
&\le M\|T_hJ_\eta-J_\eta\|_{p'},
\end{aligned}
\qquad\text{(C)}
$$

其中 $p=1$ 时按 $p'=\infty$ 理解。于是磨光后的函数族在任意固定紧集上一致有界、等度连续。

再由尾部条件选一个闭球 $B_R$，使 $\sup_{u\in\mathcal K}\|u\|_{L^p(\mathbb R^n\setminus B_R)}$ 足够小。在 $B_R$ 上用 Arzelà–Ascoli 定理为 $\{J_\eta*\widetilde u:u\in\mathcal K\}$ 取有限的一致范数网 $\psi_1,\ldots,\psi_N$。将 $\psi_j$ 乘以 $\mathbf1_{B_R}$ 视为 $L^p(\mathbb R^n)$ 函数；不要求它在球面连续。对相应的 $j$，

$$
\begin{aligned}
\|\widetilde u-\mathbf1_{B_R}\psi_j\|_p
&\le\|\widetilde u-J_\eta*\widetilde u\|_{L^p(B_R)}\\
&\quad+|B_R|^{1/p}\|J_\eta*\widetilde u-\psi_j\|_{C(B_R)}
+\|\widetilde u\|_{L^p(\mathbb R^n\setminus B_R)}.
\end{aligned}
$$

三项可统一做得任意小，因此 $\widetilde{\mathcal K}$ 有有限 $\varepsilon$ 网。$L^p$ 完备，故 $\mathcal K$ 预紧。注意：这一步控制的是原函数在球外的尾部，**无需先证明所有磨光函数在球外也有统一小尾部**。

### 2.33 局部预紧加一致尾部推出整体预紧

**定理。** 设 $1\le p<\infty$，$\Omega_j\subset\Omega_{j+1}\subset\Omega$。若 $\mathcal K$ 在每个 $L^p(\Omega_j)$ 中的限制族预紧，且对每个 $\varepsilon>0$ 存在 $j$ 使

$$
\sup_{u\in\mathcal K}\int_{\Omega\setminus\Omega_j}|u|^p<\varepsilon,
$$

则 $\mathcal K$ 在 $L^p(\Omega)$ 中预紧。

**证明。** 从任意序列 $u_m\in\mathcal K$ 出发，依次在 $\Omega_1,\Omega_2,\ldots$ 上抽取嵌套收敛子列，最后取对角子列 $v_m$。对每个固定 $j$，$v_m|_{\Omega_j}$ 是 $L^p(\Omega_j)$ 中的 Cauchy 列。给定 $\varepsilon>0$，选 $j$ 使每个 $u\in\mathcal K$ 的尾积分小于 $\varepsilon^p/2^{p+2}$。由 $|a-b|^p\le2^{p-1}(|a|^p+|b|^p)$，

$$
\int_{\Omega\setminus\Omega_j}|v_m-v_l|^p
\le2^{p-1}\!\left(
\int_{\Omega\setminus\Omega_j}|v_m|^p
+\int_{\Omega\setminus\Omega_j}|v_l|^p
\right)<\frac{\varepsilon^p}{4}.
$$

再令 $m,l$ 足够大，使 $\int_{\Omega_j}|v_m-v_l|^p<\varepsilon^p/4$。于是 $v_m$ 在 $L^p(\Omega)$ 中 Cauchy，利用完备性得到强收敛子列。此定理可记为“**局部紧性 + 不逃逸 = 整体紧性**”。

---

## 🔢 2.34—2.37：Clarkson 不等式所需的标量准备

### 2.34 从平行四边形律走向一致凸性

$L^2$ 的平行四边形律为

$$
\|u+v\|_2^2+\|u-v\|_2^2
=2\|u\|_2^2+2\|v\|_2^2.
$$

在 $p\ne2$ 时一般没有这样的等式。Clarkson 不等式以可控制的上下界代替它，并最终证明 $1<p<\infty$ 的 $L^p$ 一致凸。为了照顾复值函数，先建立复数 $z,w$ 的不等式。

### 2.35 一个严格单调的辅助函数

固定 $0<s<1$，令 $F_s(t)=(1-s^t)/t$，$t>0$。则 $F_s$ 严格递减。实际上置 $r=s^t\in(0,1)$，有

$$
F_s'(t)=\frac{r-r\log r-1}{t^2}.
$$

函数 $g(r)=r-r\log r$ 满足 $g'(r)=-\log r>0$ 且 $g(1)=1$，故 $g(r)<1$，从而 $F_s'(t)<0$。这个单调性将在 2.36 中比较两个不同的指数，而不能只凭图形直观判断幂级数系数的符号。

### 2.36 实数标量的关键不等式

若 $1<p\le2$，$p'=p/(p-1)$ 且 $0\le t\le1$，则

$$
\left(\frac{1+t}{2}\right)^{p'}
+\left(\frac{1-t}{2}\right)^{p'}
\le
\left(\frac{1+t^p}{2}\right)^{1/(p-1)}.
\qquad\text{(D)}
$$

$p=2$ 或 $t\in\{0,1\}$ 时直接验算；以下设 $1<p<2$、$0<t<1$。作代换 $t=(1-s)/(1+s)$，$0<s<1$。将两边乘以 $(1+s)^{p'}$ 再取 $(p-1)$ 次方，(D) 等价于

$$
\frac{(1+s)^p+(1-s)^p}{2}
\ge(1+s^{p'})^{p-1}.
\qquad\text{(E)}
$$

在 $0<s<1$ 内利用广义二项式级数，左减右的常数项抵消，可按 $k\ge1$ 写成级数 $\sum_{k\ge1}c_k(s)$，其中

$$
c_k(s)=\binom p{2k}s^{2k}
-\binom{p-1}{2k-1}s^{p'(2k-1)}
-\binom{p-1}{2k}s^{2kp'}.
$$

直接整理系数，设

$$
A_k(s)=\frac{(2-p)(3-p)\cdots(2k-p)}{(2k-1)!}s^{2k}>0,
$$

得到

$$
c_k(s)=A_k(s)\left[
F_s\!\left(\frac{2k-p}{p-1}\right)
-F_s\!\left(\frac{2k}{p-1}\right)
\right].
$$

前一个自变量严格小于后一个，由 2.35 知方括号为正，因此每项 $c_k(s)>0$，(E) 成立。端点 $s=0,1$ 由连续性得到。这个证明的实际思路是：**代换以消去外层指数—展开偶次项—把每项化为同一个递减函数的差**。

### 2.37 复数标量版本

若 $z,w\in\mathbb C$ 且 $1<p\le2$，则

$$
\left|\frac{z+w}{2}\right|^{p'}
+\left|\frac{z-w}{2}\right|^{p'}
\le
\left(\frac{|z|^p+|w|^p}{2}\right)^{1/(p-1)}.
\qquad\text{(F)}
$$

若某个数为零可直接验证。利用对称性及齐次性，可设 $|z|\ge|w|>0$ 且 $w/z=re^{i\theta}$，$0<r\le1$。固定 $r$，令

$$
H(c)=(1+r^2+2rc)^{p'/2}+(1+r^2-2rc)^{p'/2},
\quad 0\le c\le1.
$$

因为 $p'\ge2$，

$$
H'(c)=p'r\left[(1+r^2+2rc)^{p'/2-1}
-(1+r^2-2rc)^{p'/2-1}\right]\ge0.
$$

表达式关于 $\cos\theta$ 对称，所以最大值在 $|\cos\theta|=1$ 取得，即两复数同线时。该情形恰是 2.36 中 $t=r$ 的不等式；乘回 $|z|^{p'}$ 即得 (F)。复数相位这一步不可省略：不能把实数结论未经解释就用于复值函数。

另一个后面立即会用到的标量估计更简单。由复数的平行四边形恒等式和 $r\mapsto r^{p/2}$ 的凹凸性，可得

$$
\left|\frac{z+w}{2}\right|^p
+\left|\frac{z-w}{2}\right|^p
\begin{cases}
\le\dfrac{|z|^p+|w|^p}{2},&p\ge2,\\[3pt]
\ge\dfrac{|z|^p+|w|^p}{2},&1<p\le2.
\end{cases}
\qquad\text{(G)}
$$

例如 $p\ge2$ 时，设 $a=|(z+w)/2|^2$、$b=|(z-w)/2|^2$，则 $a+b=(|z|^2+|w|^2)/2$，而

$$
a^{p/2}+b^{p/2}
\le(a+b)^{p/2}
\le\frac{|z|^p+|w|^p}{2}.
$$

$p\le2$ 时两步不等号均反向。

---

## 📐 2.38—2.40：Clarkson 不等式、一致凸性与自反性

### 2.38 四个 Clarkson 不等式怎样对应两个指数区间

以下 $u,v\in L^p(\Omega)$，且 $p'=p/(p-1)$。记 $m=(u+v)/2$、$d=(u-v)/2$。

| 指数范围 | $p$ 次幂的结论 | $p'$ 次幂的结论 |
| --- | --- | --- |
| $2\le p<\infty$ | $\|m\|_p^p+\|d\|_p^p\le(\|u\|_p^p+\|v\|_p^p)/2$ | $\|m\|_p^{p'}+\|d\|_p^{p'}\ge[(\|u\|_p^p+\|v\|_p^p)/2]^{p'-1}$ |
| $1

这分别是教材的 (30)、(31)、(33)、(32)。注意两个区间中上下界方向恰好互换，且 $p=2$ 时全部成为平行四边形等式。

**证明 $p$ 次幂两式。** 对 (G) 逐点取 $z=u(x),w=v(x)$，再对 $x$ 积分即可。

**证明 $1<p\le2$ 时的 $p'$ 次幂上界。** 令 $q=p-1\in(0,1]$，$F=|m|^{p'}$、$H=|d|^{p'}$。因 $p'q=p$，

$$
\|F\|_q=\|m\|_p^{p'},
\qquad
\|H\|_q=\|d\|_p^{p'}.
$$

$q<1$ 时，对非负函数用上一课的反向 Minkowski 不等式，并由 (F) 逐点得到

$$
\begin{aligned}
\|m\|_p^{p'}+\|d\|_p^{p'}
&\le\|F+H\|_q\\
&=\left[\int_\Omega(F+H)^q\right]^{1/q}\\
&\le\left[\int_\Omega\frac{|u|^p+|v|^p}{2}\right]^{1/q}.
\end{aligned}
$$

当 $p=2$ 时两边相等。这里 $q=p-1<1$ 不是 Banach 范数，**不能错用通常的三角不等式**。

**证明 $p\ge2$ 时的 $p'$ 次幂下界。** 现在 $q=p-1\ge1$。将 (F) 用于指数 $p'\le2$、以及数 $z=u+v,w=u-v$。此时 (F) 左边成为 $|u|^p+|v|^p$；注意 $(p'-1)(p-1)=1$，整理可得逐点不等式

$$
\bigl(|m|^{p'}+|d|^{p'}\bigr)^q
\ge\frac{|u|^p+|v|^p}{2}.
\qquad\text{(H)}
$$

通常的 Minkowski 不等式及 (H) 给出

$$
\begin{aligned}
\|m\|_p^{p'}+\|d\|_p^{p'}
&=\|F\|_q+\|H\|_q\\
&\ge\|F+H\|_q\\
&\ge\left[\frac{\|u\|_p^p+\|v\|_p^p}{2}\right]^{1/q}.
\end{aligned}
$$

这说明为何两区间的证明要分别调用直接和反向 Minkowski。

### 2.39 从 Clarkson 不等式得到一致凸性

**定义。** 赋范空间 $X$ 一致凸，是指对每个 $0<\varepsilon\le2$，存在只依赖于 $\varepsilon$ 的 $\delta(\varepsilon)>0$，使

$$
\|u\|_X=\|v\|_X=1,
\quad\|u-v\|_X\ge\varepsilon
\quad\Longrightarrow\quad
\left\|\frac{u+v}{2}\right\|_X\le1-\delta(\varepsilon).
$$

教材证明使用单位球版本 $\|u\|,\|v\|\le1$，它也由同样的不等式直接得到。对 $p\ge2$，Clarkson (30) 产生

$$
\left\|\frac{u+v}{2}\right\|_p^p
\le1-\left(\frac\varepsilon2\right)^p.
$$

对 $1<p\le2$，Clarkson (32) 产生

$$
\left\|\frac{u+v}{2}\right\|_p^{p'}
\le1-\left(\frac\varepsilon2\right)^{p'}.
$$

因而可以取

$$
\delta_p(\varepsilon)=
\begin{cases}
1-\bigl[1-(\varepsilon/2)^{p'}\bigr]^{1/p'},&1<p\le2,\\
1-\bigl[1-(\varepsilon/2)^p\bigr]^{1/p},&2\le p<\infty.
\end{cases}
$$

两式在 $p=2$ 一致。此 $\delta_p$ 只是一个可用的正下界；不必声称它对所有 $p$ 都是最优的凸性模。

### 2.40 自反性从哪里来

上一章的一般定理说明：**一致凸的 Banach 空间是自反的**。由 2.39 和 $L^p$ 的完备性，

$$
1<p<\infty\quad\Longrightarrow\quad L^p(\Omega)\text{ 自反}.
$$

这里“自反”是自然嵌入 $J:L^p\to(L^p)''$ 满射；“一致凸”是单位球的定量几何性质；二者不能视作同一个定义。后面的对偶表示也会给出自反性的另一条理解路径。

### 课堂补充：弱收敛加范数收敛何时推出强收敛

在 $1<p<\infty$ 中，若 $u_k\rightharpoonup u$ 且 $\|u_k\|_p\to\|u\|_p$，则 $\|u_k-u\|_p\to0$。$u=0$ 时结论直接来自范数收敛。若 $u\ne0$，归一化得 $x_k=u_k/\|u_k\|_p\rightharpoonup x=u/\|u\|_p$，且两者范数为 $1$。于是 $(x_k+x)/2\rightharpoonup x$。范数的弱下半连续性给出

$$
1=\|x\|_p\le\liminf_k\left\|\frac{x_k+x}{2}\right\|_p
\le\limsup_k\left\|\frac{x_k+x}{2}\right\|_p\le1.
$$

中点范数趋于 $1$，一致凸性迫使 $\|x_k-x\|_p\to0$，再乘回范数即可。这称为 Radon–Riesz 或 Kadec–Klee 性质。**只知道 $\|u_k\|_p\to\|u\|_p$ 而没有弱收敛，当然不足以推出强收敛。** 在 $L^1(0,1)$ 中，即使附加弱收敛也不够：令 $u_k(x)=1+\sin(2\pi kx)$、$u(x)=1$。由 Riemann–Lebesgue 引理，$u_k\rightharpoonup u$ 于 $L^1$，且 $\|u_k\|_1=\|u\|_1=1$，但 $\|u_k-u\|_1=2/\pi$。

---

## 🔗 2.41—2.44：$L^p$ 的赋范对偶

### 2.41 积分配对先给出一个等距嵌入

对 $1\le p\le\infty$，定义 $p'$ 使 $1/p+1/p'=1$。给定 $v\in L^{p'}(\Omega)$，定义**复线性**泛函

$$
L_v(u)=\int_\Omega u(x)v(x)\,dx,
\qquad u\in L^p(\Omega).
\qquad\text{(I)}
$$

这里没有在公式中对 $v$ 取共轭；若沿用 Hilbert 空间内积 $(u,w)=\int u\overline w$，则 $v=\overline w$。Hölder 不等式证明 $\|L_v\|\le\|v\|_{p'}$。反向不等式分三种情形：

1. $1<p<\infty$：若 $v\ne0$，取 $u=|v|^{p'-2}\overline v$，在 $v=0$ 处置零。则 $u\in L^p$，且
   
   $$
   \|u\|_p=\|v\|_{p'}^{p'-1},
   \qquad L_v(u)=\|v\|_{p'}^{p'}.
   $$
   
   两式相除得 $\|L_v\|\ge\|v\|_{p'}$。
2. $p=\infty$、$p'=1$：取 $u=\overline v/|v|$ 于 $v\ne0$ 处，其他处置零。则 $\|u\|_\infty\le1$、$L_v(u)=\|v\|_1$。
3. $p=1$、$p'=\infty$：对任意 $0<\varepsilon<\|v\|_\infty$，由本性上确界定义，可在集合 $\{|v|>\|v\|_\infty-\varepsilon\}$ 中取有限正测度子集 $A$；令 $u=\mathbf1_A\overline v/|v|$。则 $L_v(u)/\|u\|_1\ge\|v\|_\infty-\varepsilon$，令 $\varepsilon\downarrow0$。

因此总有

$$
\boxed{\ \|L_v\|_{(L^p)'}=\|v\|_{p'}\ },
\qquad
L^{p'}(\Omega)\hookrightarrow(L^p(\Omega))'
\text{ 等距}.
\qquad\text{(J)}
$$

等距嵌入只说“每个 $v$ 给出一个泛函，而且范数不变”，**尚未说明每个泛函都是这样来的**。

### 2.42 满射问题及 $p=\infty$ 的障碍

对 $1<p<\infty$，2.44 将证明 (J) 满射。$p=1$ 的满射结论 $(L^1)'\cong L^\infty$ 属于教材下一节 2.45，证明方法与这里的范数取到论证不同。$p=\infty$ 时，通常 $(L^\infty)'$ 严格大于 $L^1$。

一个说明其差别的例子在 $(0,1)$ 上：在“于 $0$ 附近存在本性极限”的有界可测函数子空间上定义 $\Lambda(f)=\operatorname*{ess\,lim}_{x\downarrow0}f(x)$。它是范数不超过 $1$ 的线性泛函，Hahn–Banach 定理可将它延拓到 $L^\infty(0,1)$。若该延拓可写为 $\int_0^1fv$，其中 $v\in L^1$，则对每个 $\varepsilon>0$ 取 $f=\mathbf1_{(\varepsilon,1)}$ 得 $\int_\varepsilon^1v=0$；继而 $v=0$ 几乎处处。但 $\Lambda(1)=1$，矛盾。这正是 $L^\infty$ 端点不能照搬 2.44 的原因之一。

### 2.43 单位范数泛函与单位向量的唯一配对

**引理。** 若 $1<p<\infty$，则：

- 对任意 $L\in(L^p)'$、$\|L\|=1$，存在唯一 $w\in L^p$ 满足 $\|w\|_p=L(w)=1$。
- 对任意 $w\in L^p$、$\|w\|_p=1$，存在唯一 $L\in(L^p)'$ 满足 $\|L\|=L(w)=1$。

第一项说明**范数取到且取到点唯一**；第二项说明**支撑单位球的规范泛函唯一**。证明它们不能混为一谈。

**第一项证明。** 按算子范数定义取 $w_k$，使 $\|w_k\|_p=1$ 且 $|L(w_k)|\to1$。乘以单位复数后可设 $L(w_k)\to1$ 为非负实数。于是

$$
1\ge\left\|\frac{w_k+w_l}{2}\right\|_p
\ge L\left(\frac{w_k+w_l}{2}\right)\longrightarrow1
\quad(k,l\to\infty).
$$

一致凸性的逆否形式表明 $\|w_k-w_l\|_p\to0$。完备性给出极限 $w$，连续性给出 $\|w\|_p=L(w)=1$。若另有 $z$ 满足同样两式，则 $L((w+z)/2)=1$；一致凸性蕴含严格凸性，故 $w=z$。

**第二项的存在性。** 对给定 $\|w\|_p=1$，令

$$
v_w(x)=
\begin{cases}
|w(x)|^{p-2}\overline{w(x)},&w(x)\ne0,\\
0,&w(x)=0.
\end{cases}
\qquad\text{(K)}
$$

因为 $(p-1)p'=p$，有 $\|v_w\|_{p'}^{p'}=\int|w|^p=1$，且 $L_{v_w}(w)=\int|w|^p=1$。所以 (J) 给出 $\|L_{v_w}\|=1$。

**第二项的唯一性：变分证明。** 假设 $L$ 是任一满足 $\|L\|=L(w)=1$ 的复线性泛函。对 $h\in L^p$、实数 $t$，

$$
|1+tL(h)|=|L(w+th)|\le\|w+th\|_p.
$$

当 $1<p<\infty$ 且 $\|w\|_p=1$ 时，范数在 $w$ 处对实参数的导数为

$$
\left.\frac{d}{dt}\|w+th\|_p\right|_{t=0}
=\operatorname{Re}\int_\Omega|w|^{p-2}\overline w\,h.
\qquad\text{(L)}
$$

这是先对 $\int|w+th|^p$ 求导、再用链式法则得到的；求导与积分交换可由 $C_p(|w|^{p-1}|h|+|h|^p)$ 控制差商，并由 Hölder 知该控制函数可积。对上述范数不等式分别令 $t\downarrow0$、$t\uparrow0$，得

$$
\operatorname{Re}L(h)
=\operatorname{Re}\int|w|^{p-2}\overline w\,h.
$$

再将 $h$ 换为 $ih$ 得虚部也相等，所以 $L(h)=L_{v_w}(h)$ 对所有 $h$ 成立，唯一性得证。教材也可用 Clarkson 不等式作反证；变分法直接展示了唯一泛函的具体公式。

### 2.44 $L^p$ 的 Riesz 表示定理

**定理。** 若 $1<p<\infty$，则任意 $L\in(L^p(\Omega))'$ 都存在唯一 $v\in L^{p'}(\Omega)$，使

$$
L(u)=\int_\Omega u(x)v(x)\,dx
\quad\text{对所有 }u\in L^p(\Omega),
\qquad
\|L\|=\|v\|_{p'}.
\qquad\text{(M)}
$$

即 $(L^p(\Omega))'\cong L^{p'}(\Omega)$，而且同构保范数。

**证明。** $L=0$ 时取 $v=0$。若 $L\ne0$，将 $L$ 除以 $\|L\|$，由 2.43 第一项取唯一 $w$，满足 $\|w\|_p=L(w)=1$。按 (K) 构造 $v_w$，则 $L_{v_w}$ 与 $L$ 都是范数为 $1$ 且在 $w$ 处取值 $1$ 的泛函。由 2.43 第二项的唯一性，$L=L_{v_w}$。再乘回 $\|L\|$ 得 (M)。若两个 $v$ 表示同一泛函，则 (J) 对差 $v_1-v_2$ 给出 $\|v_1-v_2\|_{p'}=0$，故唯一。

这个证明的闭合链条是

$$
\boxed{\text{一致凸}\Rightarrow\text{单位泛函范数取到}
\Rightarrow\text{范数取到点 }w
\Rightarrow v_w=|w|^{p-2}\overline w
\Rightarrow\text{全部泛函均为积分泛函}.}
$$

---

## 🧭 三个容易混淆的结论

| 说法 | 正确范围与关键原因 |
| --- | --- |
| $L^p$ 有界族必预紧 | 一般错误。还需统一尾部控制和平移连续性。 |
| 弱收敛且范数收敛推出强收敛 | 对 $1

课堂图片还提及 Barron 空间与神经网络逼近。这是另一个延伸主题：Barron 空间的定义依赖所选激活函数、网络表示及所用的变差或 Fourier 型范数，仅凭“Barron space”这一名称不能确定唯一数学对象或某个逼近定理。复习本节时应先掌握这里已证明的 $L^p$ 稠密、预紧及对偶结果；讨论神经网络逼近时须另行写明具体 Barron 范数和目标函数类。

