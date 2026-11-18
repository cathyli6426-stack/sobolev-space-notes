# 第十一课：Sobolev 空间中的逼近、零延拓、分布与坐标变换

## 0. 本课地图与阅读顺序


本课研究三个相互联系的问题：

1. 逼近：能不能用光滑函数逼近弱可微函数？逼近函数需要在什么地方光滑、支集能到哪里？
2. 边界：把区域外的函数补成零，会不会产生额外的边界分布？
3. 变换：改变坐标后，弱导数与 Sobolev 范数怎样变化？

主要逻辑是

$$
\text{单位分解}
\longrightarrow\text{局部磨光}
\longrightarrow H=W
\longrightarrow\text{把光滑函数上的公式传递给弱可微函数}.
$$

另一条逻辑是

$$
\text{紧支集逼近}
\longrightarrow\text{零延拓与求导交换}
\longrightarrow\text{分析边界造成的障碍}.
$$

### 0.1 编号与掌握程度

| 教材编号 | 内容 | 本文处理 |
|---|---|---|
| 3.15 | 光滑单位分解 | 定义、构造思路、显式例子详解 |
| 3.16 | Sobolev 范数下的局部磨光 | 完整证明 |
| 3.17 | Meyers–Serrin 定理：$H=W$ | 分步证明，补齐支集和局部有限性的细节 |
| 3.18 | $p=\infty$ 反例 | 完整证明，澄清与 Gibbs 现象的关系 |
| 3.19—3.20 | 光滑到边界的逼近可能失败 | 反例及定量矛盾详解 |
| 3.21—3.22 | 线段条件与全空间光滑逼近 | 定义、结论、几何直观；证明只给路线 |
| 3.23 | 全空间上 $W_0^{m,p}=W^{m,p}$ | 给出实用的截断—磨光证明 |
| 3.24—3.25 | 极集与问题背景 | 按画叉批注，只作概念说明 |
| 3.26—3.27 | 零延拓 | 完整证明与反例 |
| 3.28 | 极集与全空间稠密性 | 结论、用途，简述对偶思想 |
| 3.29—3.32 | 零积分分解、导数为零、分布唯一性 | 重点展开 |
| 3.33—3.38 | 极集进一步判据 | 缺页核对后简列结论，不假定课堂要求背证明 |
| 3.39 | Hilbert 空间正交分解 | 按“没讲”批注简述 |
| 3.40—3.41 | 坐标变换 | 定义、换元、链式法则、完整证明 |

## 1. 本课反复使用的基础

### 1.1 三种“光滑函数”不能混为一谈

记 $\mathcal D(\Omega)=C_c^\infty(\Omega)$，教材的 $C_0^\infty$ 在这里就是 $C_c^\infty$。

| 函数类 | 要求 | 能否在边界附近非零 |
|---|---|---|
| $C^\infty(\Omega)$ | 只要求区域内部无限可微 | 可以；甚至可以靠近边界时无界 |
| $C_c^\infty(\mathbb R^n)\big\vert_\Omega$ | 来自一个全空间光滑紧支集函数 | 可以 |
| $C_c^\infty(\Omega)$ | 光滑，而且支集紧包含于区域内部 | 不可以：每个函数都在某个边界邻域中为零 |

例如在 $(0,1)$ 上，常数函数 $1$ 可以是全空间紧支集光滑函数的限制：取一个在 $[0,1]$ 附近恒等于 $1$ 的截断函数即可。但 $1$ 不能在 $W^{1,p}(0,1)$ 范数下被 $C_c^\infty(0,1)$ 逼近。

所以，“区域满足线段条件”并不意味着 $W_0^{m,p}(\Omega)=W^{m,p}(\Omega)$。§3.22 逼近函数的支集在全空间中紧，而不要求紧包含于 $\Omega$。

### 1.2 弱导数、Sobolev 范数与 $H=W$

多重指标 $\alpha=(\alpha_1,\ldots,\alpha_n)\in\mathbb N_0^n$，记

$$
|\alpha|=\alpha_1+\cdots+\alpha_n,\qquad
D^\alpha=\partial_1^{\alpha_1}\cdots\partial_n^{\alpha_n}.
$$

对 $u,g\in L^1_{\mathrm{loc}}(\Omega)$，$D^\alpha u=g$ 的含义是

$$
\int_\Omega g\varphi
=(-1)^{|\alpha|}\int_\Omega uD^\alpha\varphi,
\qquad\forall\varphi\in\mathcal D(\Omega).
$$

当 $1\le p<\infty$ 时，

$$
W^{m,p}(\Omega)=\{u:D^\alpha u\in L^p(\Omega),\ |\alpha|\le m\},
\qquad
\|u\|_{m,p}=\left(\sum_{|\alpha|\le m}\|D^\alpha u\|_p^p\right)^{1/p}.
$$

$W_0^{m,p}(\Omega)$ 是 $C_c^\infty(\Omega)$ 在这个范数下的闭包。

本教材的 $H^{m,p}$ 指 $C^m(\Omega)\cap W^{m,p}(\Omega)$ 对此范数的完备化。因此本课的 $H=W$ 是“完备化定义”和“弱导数定义”等价。不要把这里带两个参数的 $H^{m,p}$ 与其他教材的 Bessel 势空间记号不加区别地混用。特别地，$H^m=W^{m,2}$ 是常见的 Hilbert 空间记号。

### 1.3 局部有限：允许逐项求导的关键

函数族 $\{f_j\}$ 在 $\Omega$ 中局部有限，指每个点有一个邻域，在这个邻域中只有有限个 $f_j$ 不恒为零。等价地，每个紧集只碰到有限多个支集。

于是

$$
f=\sum_jf_j
$$

在每个小邻域中实际上是有限和。因此，若所有 $f_j$ 都光滑，则 $f$ 光滑，而且可以逐项求导。

**仅仅“在每个点只有有限项非零”还不够。** 还需要邻域中的有限性，才能直接保证光滑性。§3.17 中必须控制卷积后扩大的支集，正是为了保住这一点。

### 1.4 紧包含、穷竭与到边界的距离

$K\Subset\Omega$ 表示 $K$ 的闭包紧且包含于 $\Omega$。若 $K$ 紧、$\Omega$ 开，则

$$
\operatorname{dist}(K,\Omega^c)>0.
$$

常用穷竭为

$$
\Omega_k=\{x\in\Omega:|x|<k,\ d(x)>1/k\},
\qquad d(x)=\operatorname{dist}(x,\Omega^c).
$$

若 $\Omega=\mathbb R^n$，可约定 $d=+\infty$。有

$$
\overline{\Omega_k}\subset\Omega_{k+1},\qquad
\Omega_k\uparrow\Omega.
$$

原因是 $|x|\le k<k+1$，且 $d(x)\ge1/k>1/(k+1)$。距离函数满足

$$
|d(x)-d(y)|\le|x-y|,
$$

即它是 $1$-Lipschitz 的。这条估计可用来计算卷积允许的半径。

### 1.5 平移连续与磨光

取非负函数 $J\in C_c^\infty(B(0,1))$，满足 $\int J=1$，令

$$
J_\varepsilon(x)=\varepsilon^{-n}J(x/\varepsilon).
$$

对 $g\in L^p(\mathbb R^n)$、$1\le p<\infty$，有

$$
\|g(\cdot-h)-g\|_p\to0\quad(h\to0).
$$

这是先对紧支集连续函数使用一致连续性，再利用其在 $L^p$ 中的稠密性得到的。由积分型 Minkowski 不等式，

$$
\begin{aligned}
\|J_\varepsilon*g-g\|_p
&\le\int J(z)\|g(\cdot-\varepsilon z)-g\|_p\,dz
\longrightarrow0.
\end{aligned}
$$

这里被积函数不超过 $2\|g\|_pJ(z)$，可用支配收敛定理。对于 $p=\infty$，平移通常不在范数下连续，不能照搬结论。

### 1.6 与上一课负阶空间的衔接

对 $1<p<\infty$，

$$
W^{-m,p'}(\Omega)=(W_0^{m,p}(\Omega))',\qquad
\frac1p+\frac1{p'}=1.
$$

若 $v\in L^{p'}(\Omega)$，定义

$$
\|v\|_{-m,p'}
=\sup_{u\in W_0^{m,p},\ \|u\|_{m,p}\le1}
\left|\int_\Omega uv\right|.
$$

由 Hölder 不等式，$\|v\|_{-m,p'}\le\|v\|_{p'}$，并且

$$
|\langle u,v\rangle|\le\|u\|_{m,p}\|v\|_{-m,p'}.
$$

图片第 65 页所补充的是：$L^{p'}$ 按这个较弱范数完备化，得到 $W^{-m,p'}$。稠密性的证明要点是：令 $X=W_0^{m,p}$，若 $F\in X''$ 消灭所有积分泛函 $L_v$，由 $X$ 自反，$F=Jf$，于是 $\int fv=0$ 对所有 $v\in L^{p'}$ 成立，取 $v=|f|^{p-2}\overline f$（零处定义为零）便知 $f=0$。再用 Hahn–Banach 的稠密性判据。

对 $(W^{m,p})'$，§3.14 使用的却是测试整个 $W^{m,p}$ 单位球的范数 $\|\cdot\|_{-m,p'}^*$。两个测试空间不同，不能混用。

## 2. §3.15：单位分解——把整体问题拆成局部问题

### 2.1 定理究竟说了什么

设开集族 $\mathcal U$ 覆盖集合 $A\subset\mathbb R^n$。可以找到一族 $\psi_j\in C_c^\infty(\mathbb R^n)$，使：

1. $0\le\psi_j\le1$；
2. 在 $A$ 上局部有限；
3. 每个 $\operatorname{supp}\psi_j$ 包含于某个 $U\in\mathcal U$；
4. $\sum_j\psi_j(x)=1$，$x\in A$。

它叫作从属于该开覆盖的光滑单位分解。

“单位”是说总和等于 $1$；“从属”是说每一片都放在某个指定的开集里。于是

$$
u=\sum_j\psi_ju.
$$

$\psi_ju$ 只研究 $u$ 在一小块上的行为，可以分别磨光、换坐标，再拼接回来。

### 2.2 为什么不能直接用特征函数切块

$\mathbf1_Uu$ 往往在 $\partial U$ 处发生跳跃，求导时会出现边界分布。光滑权函数则服从弱 Leibniz 公式：

$$
D^\alpha(\psi u)
=\sum_{\beta\le\alpha}\binom\alpha\beta
D^\beta\psi\,D^{\alpha-\beta}u.
$$

这里 $\beta\le\alpha$ 确实表示逐分量比较。由于 $\psi$ 的导数有界、支集紧，这些乘积都在相应 $L^p$ 空间中。该公式可先由一阶分布定义验证，再对阶数归纳。

### 2.3 构造的核心：先取鼓包，再归一化

在开集 $\Omega$ 内，取局部有限的紧支集光滑鼓包 $\rho_j\ge0$，使每一点至少落在某个 $\rho_j>0$ 的地方，且支集从属于原覆盖。设

$$
S(x)=\sum_j\rho_j(x)>0,\qquad
\psi_j(x)=\frac{\rho_j(x)}{S(x)}.
$$

局部有限使 $S$ 光滑；分母处处正使商有定义；归一化给出 $\sum_j\psi_j=1$。因 $\rho_j$ 的支集紧包含于 $\Omega$，每个商可以在 $\Omega$ 外补零为全空间光滑函数。

开集中的局部有限鼓包族可这样得到：用紧集穷竭，把区域分成一层层紧的“环带”；每个环带用有限多个小球覆盖，稍放大后仍在相应覆盖成员内，再在小球上放鼓包。放大球只进入相邻有限层，因此整个族局部有限。

对紧集 $A$，有限开覆盖与有限鼓包就够了；归一化先在 $A$ 的一个开邻域完成，再乘一个在 $A$ 附近恒为 $1$、支集留在该邻域中的截断函数。对一般集合，可在开集 $\bigcup\mathcal U$ 上构造，再限制到 $A$。

这也补足了教材证明中的一个书写注意：环带型开集覆盖的是相应的紧环带，不能直接说它覆盖整个更大的穷竭紧集。

### 2.4 作业1：给出覆盖 $\{(k,k+2):k\in\mathbb Z\}$ 的显式单位分解

选一个支集严格落在 $(0,2)$ 中的鼓包：

$$
\rho(t)=
\begin{cases}
\displaystyle\exp\!\left(-\frac1{1-\frac{16}{9}(t-1)^2}\right),
&|t-1|<\frac34,\\
0,&|t-1|\ge\frac34.
\end{cases}
$$

于是 $\rho\in C_c^\infty((0,2))$，支集为 $[1/4,7/4]$。令

$$
S(x)=\sum_{j\in\mathbb Z}\rho(x-j),\qquad
\boxed{\psi_k(x)=\frac{\rho(x-k)}{S(x)}.}
$$

逐项检查：

- 分母为正：任意 $x$ 到某个整数 $k+1$ 的距离不超过 $1/2<3/4$，所以 $\rho(x-k)>0$。
- 光滑：每个有界区间只碰到有限个平移支集，所以 $S$ 是光滑函数。
- 支集：$\operatorname{supp}\psi_k=[k+1/4,k+7/4]\Subset(k,k+2)$。
- 非负且不超过一：分母包含分子且所有项非负。
- 总和：$\sum_k\psi_k=S/S=1$。

对任意函数 $f$，都得到局部有限分解

$$
\boxed{f(x)=\sum_{k\in\mathbb Z}\psi_k(x)f(x).}
$$

若只是把支集取成 $[k,k+2]$，就没有严格从属于开区间 $(k,k+2)$；本构造特意留出边距。

## 3. §3.16：磨光如何逼近所有弱导数

### 3.1 准确结论

设 $1\le p<\infty$，$u\in W^{m,p}(\Omega)$，且 $\Omega'\Subset\Omega$。那么

$$
J_\varepsilon*u\longrightarrow u
\quad\text{在 }W^{m,p}(\Omega')\text{ 中}.
$$

卷积可使用 $u$ 的零延拓定义。但这里只讨论远离边界的 $\Omega'$，**没有预先声称零延拓属于全空间的 $W^{m,p}$**。

### 3.2 导数与卷积交换的完整理由

取 $\varepsilon<\operatorname{dist}(\overline{\Omega'},\Omega^c)$。对 $x\in\Omega'$，核只读取 $u$ 在 $\Omega$ 内的值。

对 $|\alpha|\le m$，把 $y\mapsto J_\varepsilon(x-y)$ 作为关于 $y$ 的测试函数。由于它的支集紧包含于 $\Omega$，弱导数定义给出

$$
\begin{aligned}
\int_\Omega D^\alpha u(y)J_\varepsilon(x-y)\,dy
&=(-1)^{|\alpha|}\int_\Omega u(y)D_y^\alpha J_\varepsilon(x-y)\,dy\\
&=\int_\Omega u(y)D_x^\alpha J_\varepsilon(x-y)\,dy\\
&=D_x^\alpha(J_\varepsilon*\widetilde u)(x).
\end{aligned}
$$

第二步使用 $D_y^\alpha J_\varepsilon(x-y)=(-1)^{|\alpha|}D_x^\alpha J_\varepsilon(x-y)$，两个负号抵消。最后的求导可移入积分，是因为核光滑紧支集，而 $u$ 局部可积。

因此，在 $\Omega'$ 上有

$$
\boxed{D^\alpha(J_\varepsilon*\widetilde u)
=J_\varepsilon*\widetilde{D^\alpha u}.}
$$

注意右边是“先在 $\Omega$ 中求导，再作零延拓”。这是局部等式，不是关于 $D^\alpha\widetilde u$ 的全局断言。

### 3.3 从每个导数的 $L^p$ 收敛推出 Sobolev 收敛

令 $g_\alpha=\widetilde{D^\alpha u}\in L^p(\mathbb R^n)$。近似恒等算子性质给出

$$
\begin{aligned}
\|D^\alpha(J_\varepsilon*\widetilde u)-D^\alpha u\|_{L^p(\Omega')}
&\le\|J_\varepsilon*g_\alpha-g_\alpha\|_{L^p(\mathbb R^n)}
\to0.
\end{aligned}
$$

只有有限多个 $|\alpha|\le m$，故将其 $p$ 次方相加再开 $p$ 次方，得到结论。
卷积只读内部 → 用弱导数转移导数 → 每个导数应用 $L^p$ 逼近 → 有限求和。

## 4. §3.17：$H=W$ 的完整证明

### 4.1 定理与真正的难点

对任意开集 $\Omega$、整数 $m\ge0$ 和 $1\le p<\infty$，

$$
\boxed{\overline{C^\infty(\Omega)\cap W^{m,p}(\Omega)}^{\,W^{m,p}}
=W^{m,p}(\Omega).}
$$

从而教材定义下 $H^{m,p}(\Omega)=W^{m,p}(\Omega)$。

难点是：全域没有统一的正数 $\varepsilon$ 能保证所有卷积球都留在 $\Omega$ 内。解决方法是每一块用自己的 $\varepsilon_k$，再把误差分成可求和的份额。

### 4.2 第一步：穷竭与环带覆盖

使用前述 $\Omega_k$，并令所有 $k\le0$ 的 $\Omega_k=\varnothing$。定义

$$
U_k=\Omega_{k+1}\setminus\overline{\Omega_{k-1}},\qquad k\ge1.
$$

这些开集覆盖 $\Omega$。例如，取 $x$ 首次进入的 $\Omega_k$；由于 $\overline{\Omega_{k-2}}\subset\Omega_{k-1}$，可知 $x\in U_{k-1}$，最初的指标单独处理即可。

它们在 $\Omega$ 中局部有限：若 $K\Subset\Omega$，则 $K\subset\Omega_N$ 对某个 $N$ 成立；当 $k$ 足够大时，$K\subset\Omega_{k-1}$，故 $K\cap U_k=\varnothing$。

### 4.3 第二步：单位分解并局部化

取从属于 $\{U_k\}$ 的单位分解 $\{\psi_k\}$，使

$$
\psi_k\in C_c^\infty(U_k),\qquad \sum_k\psi_k=1.
$$

若最初得到多个鼓包属于同一 $U_k$，先为每个鼓包指定一个所属开集，再合并。因为 $\overline{U_k}\Subset\Omega$、原族局部有限，这里的合并只涉及有限项，不会重复计算。

令 $w_k=\psi_ku$。由弱 Leibniz 公式，$w_k\in W^{m,p}(\Omega)$ 且支集紧包含于 $\Omega$。

因此 $w_k$ 可以安全地零延拓为 $\mathbb R^n$ 上的 $W^{m,p}$ 函数：在其支集外的一圈邻域中它已经为零，分部积分不会碰到 $\partial\Omega$。这一步只用“内部紧支集”的特例，不依赖后面的 §3.27。

### 4.4 第三步：同时控制卷积支集和误差

定义略大的环带

$$
V_k=\Omega_{k+2}\setminus\overline{\Omega_{k-2}}.
$$

有 $\operatorname{supp}w_k\Subset V_k$。所以可选足够小的 $\varepsilon_k>0$，使

$$
\operatorname{supp}(J_{\varepsilon_k}*w_k)\subset V_k.
$$

这是利用

$$
\operatorname{supp}(J_\varepsilon*w)
\subset\operatorname{supp}w+\overline{B(0,\varepsilon)}.
$$

教材给出 $\varepsilon_k<1/((k+1)(k+2))$ 这一方便的统一几何上界。也可以直接选择小于支集到 $V_k^c$ 的距离的半径，逻辑相同。

再由磨光收敛，把 $\varepsilon_k$ 进一步缩小，令

$$
\|J_{\varepsilon_k}*w_k-w_k\|_{m,p,\mathbb R^n}
<\frac{\delta}{2^{k+1}}.
$$

为什么取几何级数？因为 $\sum_{k\ge1}\delta/2^{k+1}=\delta/2<\delta$，无穷多块的总误差仍受控。

### 4.5 第四步：拼接并证明光滑

令

$$
\phi=\sum_{k=1}^\infty J_{\varepsilon_k}*w_k.
$$

$\{V_k\}$ 仍然局部有限，所以在每个紧子集附近，这个和只有有限项。因此 $\phi\in C^\infty(\Omega)$。

这里不能只说“每一项都光滑，所以无穷和光滑”。真正的依据是卷积后的支集仍局部有限。

### 4.6 第五步：控制全域误差

设 $e_k=J_{\varepsilon_k}*w_k-w_k$。其范数可求和，所以由 $W^{m,p}(\mathbb R^n)$ 的完备性，$\sum e_k$ 在这个空间中收敛为某个 $e$，且

$$
\|e\|_{m,p,\mathbb R^n}
\le\sum_k\|e_k\|_{m,p,\mathbb R^n}<\delta.
$$

在 $\Omega$ 的每个紧子集上，局部有限性以及 $\sum w_k=u$ 表明 $e=\phi-u$。因此

$$
\boxed{\|\phi-u\|_{m,p,\Omega}<\delta.}
$$

也可按教材做法：先在 $\Omega_N$ 上用有限和估计，再令 $N\to\infty$，对各 $|D^\alpha(\phi-u)|^p$ 应用单调收敛定理。两种写法得到同一结论。

### 4.7 证明题可背的骨架

$$
\boxed{
\text{穷竭}\to\text{环带}\to\text{单位分解}\to
\text{逐块磨光}\to\text{支集局部有限}\to\text{误差可求和}.
}
$$

不要求边界光滑；逼近函数只需在 $\Omega$ 内部光滑；必须有 $p<\infty$。

## 5. §3.18：为什么 $p=\infty$ 失败

取 $\Omega=(-1,1)$，$u(x)=|x|$。其弱导数为

$$
u'(x)=\operatorname{sgn}x=
\begin{cases}-1,&x<0,\\1,&x>0.\end{cases}
$$

因此 $u\in W^{1,\infty}(-1,1)$。但对任意 $\phi\in C^1(-1,1)$，实际上

$$
\boxed{\|\phi'-\operatorname{sgn}\|_{L^\infty(-1,1)}\ge1.}
$$

证明：若该范数为 $M<1$，则在负半区几乎处处有 $|\phi'(x)+1|\le M$，在正半区几乎处处有 $|\phi'(x)-1|\le M$。由于 $\phi'$ 连续，这些不等式在各自开半区处处成立：若某点违反，连续性会给出一个正测度的违反区间。

令 $x\to0^-$ 和 $x\to0^+$，得到

$$
|\phi'(0)+1|\le M,\qquad |\phi'(0)-1|\le M.
$$

三角不等式推出 $2\le2M$，矛盾。因此 $u$ 不可能在 $W^{1,\infty}$ 范数下被 $C^1$ 函数逼近。

这里不能仅说“导数在 $0$ 这一点不连续”：$L^\infty$ 会忽略单点。真正的矛盾来自跳跃两边的整个邻域。

### 5.1  Gibbs 

本反例的核心是：连续函数无法在本性上确界范数下逼近真正的跳跃函数。

例如将 $\operatorname{sgn}x$ 在 $(-\pi,\pi)$ 上作周期延拓，其 Fourier 展开为

$$
\frac4\pi\sum_{k=0}^\infty\frac{\sin((2k+1)x)}{2k+1}.
$$

有限部分和连续，不可能在 $L^\infty$ 范数下收敛到这个跳跃函数；经典 Gibbs 现象进一步描述了跳跃附近的过冲。

但**非负磨光核不必产生 Gibbs 过冲**：若 $-1\le g\le1$，由 $J_\varepsilon\ge0$、$\int J_\varepsilon=1$，仍有 $-1\le J_\varepsilon*g\le1$。因此“磨光不能给出 $W^{1,\infty}$ 收敛”不等于“所有磨光都出现 Gibbs 过冲”。

## 6. §3.19—§3.23：内部光滑、边界光滑与全空间逼近

### 6.1 §3.20：裂缝两边的函数可以独立取值

设

$$
\Omega=\{(x,y):0<|x|<1,\ 0<y<1\},\qquad
u(x,y)=\begin{cases}0,&x<0,\\1,&x>0.\end{cases}
$$

$\Omega$ 是两个分离的矩形。$u$ 在每个连通分支上为常数，所以它在 $\Omega$ 内甚至是 $C^\infty$ 函数，所有一阶弱导数都为零。

跳跃发生在被删去的线段上；这条线段不在开集内部，内部测试函数不会跨过它产生分布导数。

但是，若要求逼近函数连续地延伸到整个闭包，就必须在裂缝上取同一个值，不能保留左右两种取值。

### 6.2 完整的定量矛盾

记 $L=(-1,0)\times(0,1)$、$R=(0,1)\times(0,1)$。假设有在闭包上 $C^1$ 的实值 $\phi$ 满足

$$
\|u-\phi\|_{1,p,\Omega}<\varepsilon.
$$

由于 $|L|=|R|=1$，Hölder 不等式给出

$$
\int_L|\phi|<\varepsilon,\qquad
\int_R|1-\phi|<\varepsilon,\qquad
\|\partial_x\phi\|_{L^p(\Omega)}<\varepsilon.
$$

令 $F(x)=\int_0^1\phi(x,y)\,dy$。由前两个估计，可选 $a\in(-1,0)$、$b\in(0,1)$，使

$$
|F(a)|<\varepsilon,\qquad |1-F(b)|<\varepsilon.
$$

因为 $\phi$ 在裂缝两边拼接成 $C^1$ 函数，微积分基本定理给出

$$
\begin{aligned}
1-2\varepsilon
&<F(b)-F(a)
=\int_a^bF'(x)\,dx\\
&\le\int_\Omega|\partial_x\phi|\,dx
\le2^{1/p'}\|\partial_x\phi\|_p
<2^{1/p'}\varepsilon.
\end{aligned}
$$

于是 $1<(2+2^{1/p'})\varepsilon$，对足够小的 $\varepsilon$ 矛盾。复值逼近函数可先取实部，误差不会增大。

这个反例说明：§3.17 的内部光滑逼近不要求跨裂缝连续，因此与本例不矛盾。

### 6.3 §3.21：线段条件

每个 $x\in\partial\Omega$ 都有邻域 $U_x$ 和非零向量 $y_x$，使

$$
z\in\overline\Omega\cap U_x,quad0<t<1
\quad\Longrightarrow\quad z+ty_x\in\Omega.
$$

直观上，在一个边界小片附近，存在统一的“向内”方向，把该片的所有点向同一方向平移一点就进入区域。

裂缝例子不满足它：任何横向平移都会把裂缝某一侧的点穿过裂缝；纯切向平移又不能把裂缝上的点送到区域内部。

不要把线段条件理解成整个区域凸；它是局部条件，且不同边界小片可以使用不同方向。

### 6.4 §3.22：结论与证明路线即可

若 $\Omega$ 满足线段条件，$1\le p<\infty$，则

$$
\boxed{\{\Phi|_\Omega:\Phi\in C_c^\infty(\mathbb R^n)\}
\text{ 在 }W^{m,p}(\Omega)\text{ 中稠密}.}
$$

按图片“不讲证明”的批注，只记路线：先截断远处，再用单位分解；内部块直接磨光，边界块先向内取值平移，让可能产生跳跃的界面移到区域外，再磨光。图中 $\Gamma_t$ 正是平移后避开 $\overline\Omega$ 的界面。

这里 $u_{j,t}(x)=u_j(x+ty)$ 是在向内的点取值，因此其原有界面在自变量空间中向相反方向移出。不要把这两个方向混淆。

### 6.5 §3.23：全空间没有边界障碍

对 $1\le p<\infty$，

$$
\boxed{W_0^{m,p}(\mathbb R^n)=W^{m,p}(\mathbb R^n).}
$$

一个可独立使用的证明是“截断再磨光”。取 $\chi\in C_c^\infty(\mathbb R^n)$，$0\le\chi\le1$，在 $B_1$ 上为一，支集在 $B_2$ 中；令 $\chi_R(x)=\chi(x/R)$。

由 Leibniz 公式，

$$
D^\alpha(\chi_Ru-u)
=(\chi_R-1)D^\alpha u+
\sum_{0<\beta\le\alpha}\binom\alpha\beta
D^\beta\chi_R\,D^{\alpha-\beta}u.
$$

第一项由 $L^p$ 尾部积分趋于零；其余项满足

$$
\|D^\beta\chi_R\,D^{\alpha-\beta}u\|_p
\le C_\beta R^{-|\beta|}\|D^{\alpha-\beta}u\|_p\to0.
$$

所以 $\chi_Ru\to u$ 于 $W^{m,p}(\mathbb R^n)$。固定足够大的 $R$，再取足够小的 $\varepsilon$，$J_\varepsilon*(\chi_Ru)\in C_c^\infty(\mathbb R^n)$，且在 Sobolev 范数中接近 $\chi_Ru$。三角不等式完成证明。

在有边界区域中，不能随意用“逼近边界的截断”替代这里的“截断无穷远”：边界截断的导数可能越来越大，且函数并没有相应的小尾部可补偿。

## 7. §3.26—§3.27：零延拓为什么需要零边界条件

### 7.1 定义与结论

对定义于 $\Omega$ 的函数 $u$，令

$$
\widetilde u(x)=\begin{cases}u(x),&x\in\Omega,\\0,&x\notin\Omega.\end{cases}
$$

若 $u\in W_0^{m,p}(\Omega)$，则

$$
\boxed{D^\alpha\widetilde u=\widetilde{D^\alpha u}\quad(|\alpha|\le m)}
$$

在全空间的分布意义下成立。因此

$$
\widetilde u\in W^{m,p}(\mathbb R^n),\qquad
\|\widetilde u\|_{m,p,\mathbb R^n}=\|u\|_{m,p,\Omega}.
$$

本课主要使用 $1\le p<\infty$。若 $W_0^{m,\infty}$ 也按 $C_c^\infty$ 的范数闭包定义，相同的极限论证仍适用于其中的元素。

### 7.2 完整证明：把分部积分交给逼近函数

取 $\phi_j\in C_c^\infty(\Omega)$，使 $\phi_j\to u$ 于 $W^{m,p}(\Omega)$。对任意 $\psi\in\mathcal D(\mathbb R^n)$，有

$$
\begin{aligned}
\langle D^\alpha\widetilde u,\psi\rangle
&=(-1)^{|\alpha|}\int_{\mathbb R^n}\widetilde uD^\alpha\psi\\
&=(-1)^{|\alpha|}\int_\Omega uD^\alpha\psi\\
&=\lim_{j\to\infty}(-1)^{|\alpha|}\int_\Omega\phi_jD^\alpha\psi\\
&=\lim_{j\to\infty}\int_\Omega D^\alpha\phi_j\,\psi\\
&=\int_\Omega D^\alpha u\,\psi
=\int_{\mathbb R^n}\widetilde{D^\alpha u}\,\psi.
\end{aligned}
$$

两次极限交换都由 Hölder 不等式保证。中间没有边界项，是因为 $\phi_j$ 紧支撑于 $\Omega$，即使 $\psi$ 在边界附近不为零也没有问题。

所以分布导数恰好由 $\widetilde{D^\alpha u}\in L^p$ 表示。各导数在区域外为零，范数相等立即成立。

### 7.3 反例：一般 $W^{1,p}$ 函数不行

取 $u=1$ 于 $(0,1)$。它在区间内部的弱导数为零，但零延拓为 $\mathbf1_{(0,1)}$。对测试函数 $\psi$，

$$
\langle D\widetilde u,\psi\rangle
=-\int_0^1\psi'(x)\,dx
=\psi(0)-\psi(1).
$$

因此

$$
D\widetilde u=\delta_0-\delta_1\ne0=\widetilde{Du}.
$$

这个分布不能由局部可积函数表示，故不属于任何通常的 $L^p$ 函数类。比如将固定取值为一的测试鼓包缩到 $0$ 附近：对局部可积函数的积分趋于零，但 $\delta_0$ 的取值一直为一。

边界跳跃产生了额外的 Dirac 分布，这就是零延拓失败的原因。反过来也说明常数 $1\notin W_0^{1,p}(0,1)$。

### 7.4 “零延拓可行”不要随意当成“属于 $W_0$”

§3.27 给出的是充分条件。对任意开集，单凭 $\widetilde u\in W^{m,p}(\mathbb R^n)$，不能不加条件就断言 $u\in W_0^{m,p}(\Omega)$。

例如取 $\Omega=(-1,0)\cup(0,1)$，$u$ 是在 $(-1,1)$ 上紧支集光滑且 $u(0)=1$ 的函数的限制。将 $u$ 在删去的点补零，仅改动一个零测集，因此其零延拓仍代表一个全空间光滑函数的 Sobolev 等价类。

但对 $p>1$，每个 $C_c^\infty(\Omega)$ 函数在 $0$ 两侧的迹都为零，而 $u$ 的迹为一，故 $u\notin W_0^{1,p}(\Omega)$。这里的一维迹连续性可由

$$
|v(0)|\le\int_0^1|v(t)|\,dt+\int_0^1|v'(t)|\,dt
\le\|v\|_{L^p(0,1)}+\|v'\|_{L^p(0,1)}
$$

直接得到。这个例子也说明：零测集在 $L^p$ 中可以忽略，但作为区域里删去的边界，仍可能影响 $W_0$。

## 8. §3.29—§3.32：测试函数、分布与“导数为零”

这一组结果把经典事实“梯度为零则为常数”推广到分布和局部可积函数。务必分清以下两层：

- $T$ 是抽象分布，未必由函数表示；
- $u\in L^1_{\mathrm{loc}}$ 诱导分布 $T_u$，此时需要证明分布相等确实意味着函数几乎处处相等。

### 8.1 §3.29：零积分测试函数的分解

设 $B=\prod_{j=1}^n(a_j,b_j)$ 是开矩形盒，$\phi\in\mathcal D(B)$ 且 $\int_B\phi=0$。则可写

$$
\phi=\sum_{j=1}^n\phi_j,\qquad \phi_j\in\mathcal D(B),
$$

并使每个 $\phi_j$ 对自己的第 $j$ 个坐标积分为零：

$$
\int_{a_j}^{b_j}\phi_j(x_1,\ldots,x_j,\ldots,x_n)\,dx_j=0
$$

对所有固定的其余坐标成立。

这里的“对每条坐标线积分为零”比“总积分为零”强。定理通过把 $\phi$ 拆成 $n$ 块，给不同块安排不同的方向。

### 8.2 先看二维：减去平均再补回来

取 $\rho_1\in\mathcal D(a_1,b_1)$，$\int\rho_1=1$，记

$$
a(x_2)=\int_{a_1}^{b_1}\phi(t,x_2)\,dt.
$$

定义

$$
\phi_1(x_1,x_2)=\phi(x_1,x_2)-\rho_1(x_1)a(x_2),\qquad
\phi_2(x_1,x_2)=\rho_1(x_1)a(x_2).
$$

显然 $\phi=\phi_1+\phi_2$；同时

$$
\int\phi_1\,dx_1=a-a=0,\qquad
\int\phi_2\,dx_2=\rho_1(x_1)\int_B\phi=0.
$$

而 $a$ 的支集包含在 $\operatorname{supp}\phi$ 向 $x_2$ 轴的投影中，仍远离端点，因此两个函数都是内部紧支集光滑函数。

### 8.3 一般维数：用望远镜求和记住构造

取 $\rho_j\in\mathcal D(a_j,b_j)$，$\int\rho_j=1$。定义算子

$$
(P_jf)(x)=\rho_j(x_j)\int_{a_j}^{b_j}
f(x_1,\ldots,t,\ldots,x_n)\,dt.
$$

$P_j$ 把第 $j$ 方向的积分提取出来，再用归一化鼓包补回该方向。不同坐标上的 $P_i,P_j$ 交换。令

$$
\phi_j=P_1\cdots P_{j-1}(I-P_j)\phi.
$$

则望远镜求和给出

$$
\sum_{j=1}^n\phi_j
=\phi-P_1\cdots P_n\phi
=\phi-\left(\prod_{j=1}^n\rho_j(x_j)\right)\int_B\phi
=\phi.
$$

对 $x_j$ 积分时，$(I-P_j)\phi$ 的两项积分抵消，其余 $P_i$ 不改变这一性质，所以各 $\phi_j$ 满足要求。每次积分与乘鼓包都保持光滑和内部紧支集。

这与教材用 $\omega_j$ 逐项相减的构造相同，只是写成算子形式后更容易看出抵消关系。

### 8.4 零积分为什么使原函数仍然紧支撑

对上面的 $\phi_j$，定义

$$
\theta_j(x)=\int_{a_j}^{x_j}
\phi_j(x_1,\ldots,t,\ldots,x_n)\,dt.
$$

则 $D_j\theta_j=\phi_j$。还必须检查 $\theta_j\in\mathcal D(B)$：

- 在靠近左端点处，被积函数尚未进入支集，积分为零；
- 在靠近右端点处，积分已经等于整条坐标线上的积分，而这个积分为零；
- 其他坐标的支集仍留在原支集的紧投影内。

所以原函数不会在右端留下一个非零常数尾巴。这正是“积分为零”不可缺少的原因。最终得到

$$
\boxed{\int_B\phi=0\quad\Longrightarrow\quad
\phi=\sum_{j=1}^nD_j\theta_j,\quad\theta_j\in\mathcal D(B).}
$$

### 8.5 §3.30：所有一阶导数为零的分布是常数分布

设 $T\in\mathcal D'(B)$ 且 $D_jT=0$，$j=1,\ldots,n$。证明存在常数 $c$，使

$$
\boxed{T(\phi)=c\int_B\phi,\qquad\forall\phi\in\mathcal D(B).}
$$

**第一步：证明 $T$ 消灭零积分测试函数。** 若 $\int\phi=0$，由上一小节，

$$
T(\phi)=\sum_jT(D_j\theta_j)
=-\sum_j(D_jT)(\theta_j)=0.
$$

**第二步：从零积分推广到任意测试函数。** 固定 $\rho\in\mathcal D(B)$，$\int\rho=1$。任意 $\phi$ 可分解为

$$
\phi=\underbrace{\left[\phi-\left(\int_B\phi\right)\rho\right]}_{\text{积分为零}}
+\left(\int_B\phi\right)\rho.
$$

因此

$$
T(\phi)=T(\rho)\int_B\phi.
$$

取 $c=T(\rho)$ 即可，不需要单独区分 $T=0$ 和 $T\ne0$。

这里“$T=c$”指 $T$ 等于常数函数 $c$ 所诱导的分布，并不是指对所有 $\phi$ 都有 $T(\phi)=c$。

### 8.6 §3.31：局部可积函数诱导的分布具有唯一性

若 $u\in L^1_{\mathrm{loc}}(\Omega)$ 且

$$
\int_\Omega u\phi=0,\qquad\forall\phi\in\mathcal D(\Omega),
$$

则 $u=0$ 几乎处处。

**证明一：用磨光，最适合快速掌握。**

固定开集 $V\Subset\Omega$。对 $x\in V$ 和足够小的 $\varepsilon$，$y\mapsto J_\varepsilon(x-y)$ 是合法测试函数。因此

$$
u_\varepsilon(x)=\int_\Omega u(y)J_\varepsilon(x-y)\,dy=0.
$$

取稍大的 $V'\Subset\Omega$ 包含 $\overline V$，用截断把 $u$ 局部化为全空间 $L^1$ 函数。近似恒等算子定理给出 $u_\varepsilon\to u$ 于 $L^1(V)$，所以 $u=0$ 几乎处处于 $V$。再以可数个这样的集合穷竭 $\Omega$ 即得结论。

这是“先令所有局部平均为零，再让平均半径趋零”。

### 8.7 按 Lusin 证明路线，把隐藏的局部性补齐

图片采用“用连续函数逼近符号函数”的方法，其关键如下。

**第一步：把测试函数从光滑扩展到连续。** 对 $\psi\in C_c(\Omega)$，$J_\varepsilon*\psi$ 一致收敛到 $\psi$，且支集留在同一个紧集 $K'\Subset\Omega$。所以

$$
\left|\int u(J_\varepsilon*\psi-\psi)\right|
\le\|J_\varepsilon*\psi-\psi\|_\infty\int_{K'}|u|\to0.
$$

因此 $\int u\psi=0$ 对所有 $\psi\in C_c(\Omega)$ 成立。

**第二步：想测出 $|u|$，就应当选择共轭符号。** 固定 $K\Subset\Omega$，令

$$
g=\mathbf1_K\,\overline{\operatorname{sgn}u},\qquad
\operatorname{sgn}u=\begin{cases}u/|u|,&u\ne0,\\0,&u=0.\end{cases}
$$

那么 $ug=\mathbf1_K|u|$。但 $g$ 一般不连续，不能直接拿来测试。

**第三步：Lusin 定理与积分绝对连续性。** 先固定较大的紧集 $K'\Subset\Omega$，使 $K$ 包含于其内部，并取 $\eta\in C_c(\Omega)$，$0\le\eta\le1$、$\eta=1$ 于 $K$、支集在 $K'$ 内。

由于 $u\in L^1(K')$，给定 $\epsilon>0$，存在 $\delta>0$，使

$$
E\subset K',\ |E|<\delta\quad\Longrightarrow\quad
\int_E|u|<\epsilon/2.
$$

由 Lusin 定理及连续延拓，可取连续紧支集 $h$，$|h|\le1$，使 $h$ 与 $g$ 只在测度小于 $\delta$ 的集合上不同。令 $\psi=\eta h$，则 $\psi\in C_c(\Omega)$，$|\psi|\le1$，且 $\psi-g$ 的非零集合包含在 $K'$ 内的一个测度小于 $\delta$ 的集合中。

于是

$$
\begin{aligned}
\int_K|u|
&=\int ug
=\int u\psi+\int u(g-\psi)\\
&\le 0+\int|u|\,|g-\psi|
\le2\int_{\{g\ne\psi\}\cap K'}|u|
<\epsilon.
\end{aligned}
$$

$\epsilon$ 任意，所以 $\int_K|u|=0$。以紧集穷竭即可。

必须固定一个共同的紧邻域 $K'$：$u$ 只是局部可积，不能把“误差集合测度小”直接用到可能跑向无穷远或边界的集合上。

### 8.8 §3.32：弱梯度为零，函数几乎处处为常数

若 $u\in L^1_{\mathrm{loc}}(B)$，所有 $D_ju=0$，则

$$
D_jT_u=0
\overset{3.30}{\Longrightarrow}
T_u=c
\Longrightarrow T_{u-c}=0
\overset{3.31}{\Longrightarrow}u=c\quad\text{几乎处处}.
$$

对任意连通开集也成立：在每个内部小矩形上先得到一个常数；相交的两个矩形的交集是非空开集，有正测度，因此常数相同；沿连通开集中的有限重叠链即可把常数传遍整个区域。

若区域不连通，只能说在每个连通分支上为常数。§3.20 的左右矩形例子正好说明不同分支可以取不同常数。

## 9. §3.24—§3.25、§3.28、§3.33—§3.39：只需了解的边界判据

### 9.1 极集的意思

以下讨论 $1<p<\infty$，$p'=p/(p-1)$。闭集 $F\subset\mathbb R^n$ 称为 $(m,p')$-极集，若

$$
T\in W^{-m,p'}(\mathbb R^n),\quad\operatorname{supp}T\subset F
\quad\Longrightarrow\quad T=0.
$$

它表达：这个集合太“小”，承载不了该负阶空间中的非零分布。这里的小不是单纯指 Lebesgue 测度小。

正测度闭集不是极集：在其中取有限正测度的紧集 $K$，$\mathbf1_K$ 就给出一个非零 $L^{p'}$ 分布。反过来，零测集未必极，例如当 $mp>n$、点值由 Sobolev 嵌入控制时，$\delta_x\in W^{-m,p'}$，所以单点也不是这种极集。

### 9.2 §3.28 的准确空间不要看错

$$
\boxed{C_c^\infty(\Omega)\text{ 在 }W^{m,p}(\mathbb R^n)\text{ 中稠密}
\iff\Omega^c\text{ 是 }(m,p')\text{-极集}.}
$$

左边的目标空间是全空间的 Sobolev 空间。其对偶思想很简单：稠密子空间的消灭子只有零；不稠密则由 Hahn–Banach 找到一个非零连续泛函，恰好是支撑在 $\Omega^c$ 上的分布。

这并不是直接把 $W_0^{m,p}(\Omega)=W^{m,p}(\Omega)$ 换了个说法；两个问题之间还需要零延拓及后面的判据。

### 9.3 §3.33—§3.38

下表仅列结论，不列证明。参数沿用 $1<p<\infty$、$m\ge1$。

| 编号 | 要知道的关系 |
|---|---|
| 3.33 | $W_0^{m,p}=W^{m,p}\Rightarrow\Omega^c$ 为 $(m,p')$-极集；若补集同时为 $(1,p)$-极集和 $(m,p')$-极集，则两空间相等。 |
| 3.34 | $p=2$ 时上述两个极性条件可归结为 $(m,2)$-极性。 |
| 3.35 | 极性是局部的：$F$ 极当且仅当每个 $F\cap K$ 极，$K$ 遍历紧集。 |


### 9.4 §3.39：正交分解只了解含义

在 Hilbert 情形 $p=2$，闭子空间 $W_0^{m,2}$ 有正交补，所以

$$
W^{m,2}(\Omega)=W_0^{m,2}(\Omega)\oplus(W_0^{m,2}(\Omega))^\perp.
$$

若 $v$ 在正交补中，则测试紧支集光滑函数并分部积分，得到分布方程

$$
\sum_{|\alpha|\le m}(-1)^{|\alpha|}D^{2\alpha}v=0.
$$

例如 $m=1$ 时是 $v-\Delta v=0$，因为这里使用的完整 $H^1$ 内积还包含 $\int v\phi$。先理解为分布方程即可，不需要由此直接讨论高阶导数的逐点值。图片标注“没讲”，不展开证明。

## 10. §3.40—§3.41：坐标变换保持 Sobolev 空间

### 10.1 先把映射方向画在公式里

设

$$
\Phi:\Omega\longrightarrow G,\qquad
y=\Phi(x),\qquad\Psi=\Phi^{-1}:G\longrightarrow\Omega.
$$

$u$ 原本定义在 $\Omega$，变到 $G$ 上的函数是

$$
\boxed{Au(y)=u(\Psi(y)).}
$$

因为输入是 $y\in G$，必须先用 $\Psi$ 回到 $\Omega$，然后才能代入 $u$。逆算子为

$$
A^{-1}v(x)=v(\Phi(x)).
$$

这里的“有界”是算子范数有界：存在一个不依赖于 $u$ 的常数 $C$，使 $\|Au\|\le C\|u\|$；不是说每个 $u$ 都逐点有界。

### 10.2 $m$-光滑不能只理解为内部可微

教材以 $\Phi,\Psi$ 的分量属于相应的 $C^m(\overline\Omega)$、$C^m(\overline G)$ 表述 $m$-光滑。要得到全局范数估计，关键是正反变换的导数都有统一界。

为避免不同教材对带闭包符号的 $C^m$ 有不同约定，以下明确采用证明实际需要的充分条件：$\Phi,\Psi$ 是互逆的 $C^m$ 微分同胚，并且

$$
\sup_\Omega|D^\alpha\Phi|<\infty,\qquad
\sup_G|D^\alpha\Psi|<\infty,
\qquad1\le|\alpha|\le m.
$$

这个表述也覆盖无界区域上的非退化仿射变换；不要求坐标函数本身在无界区域上有界。

由逆函数公式

$$
D\Psi(\Phi(x))D\Phi(x)=I,
$$

得

$$
\det D\Psi(\Phi(x))\det D\Phi(x)=1.
$$

正反一阶导数的统一上界控制两个行列式的上界，因此存在常数 $c_0,C_0>0$，使

$$
\boxed{c_0\le|\det D\Phi(x)|\le C_0.}
$$

单纯说“每一点行列式非零”不够：它仍可能靠近边界时趋零。统一正下界才能保证全局范数等价。

### 10.3 $L^p$ 估计：直接换元

对 $1\le p<\infty$，由 $y=\Phi(x)$，

$$
\begin{aligned}
\|Au\|_{L^p(G)}^p
&=\int_G|u(\Psi(y))|^p\,dy\\
&=\int_\Omega|u(x)|^p|\det D\Phi(x)|\,dx.
\end{aligned}
$$

因此

$$
\boxed{c_0^{1/p}\|u\|_{L^p(\Omega)}
\le\|Au\|_{L^p(G)}
\le C_0^{1/p}\|u\|_{L^p(\Omega)}.}
$$

互逆 $C^1$ 微分同胚在局部 Lipschitz，因而正反方向都把零测集映为零测集。所以复合不依赖于 $u$ 在零测集上的选值，确实定义了 Sobolev 等价类之间的算子。对 $p=\infty$，有 $\|Au\|_\infty=\|u\|_\infty$。

### 10.4 先对光滑函数写一阶、二阶链式法则

设 $u$ 光滑。对 $i=1,\ldots,n$，

$$
\partial_{y_i}(Au)(y)
=\sum_{j=1}^n(\partial_{x_j}u)(\Psi(y))\,\partial_{y_i}\Psi_j(y).
$$

向量形式为

$$
\nabla_y(Au)=D\Psi(y)^{\mathsf T}(\nabla_xu)(\Psi(y)).
$$

再求一次导数：

$$
\begin{aligned}
\partial_{y_i y_k}(Au)
={}&\sum_{j,\ell=1}^n
(\partial_{x_jx_\ell}u)\circ\Psi\,
\partial_{y_i}\Psi_j\,\partial_{y_k}\Psi_\ell\\
&+\sum_{j=1}^n(\partial_{x_j}u)\circ\Psi\,
\partial_{y_iy_k}\Psi_j.
\end{aligned}
$$

所以非线性换坐标会把同阶导数和低阶导数混合起来。这也是使用包含所有 $0\le|\alpha|\le m$ 阶导数的完整 Sobolev 范数很自然的原因。

### 10.5 高阶链式法则：指标必须按总阶数写

对 $1\le|\alpha|\le m$，可写

$$
\boxed{D_y^\alpha(Au)
=\sum_{1\le|\beta|\le|\alpha|}
M_{\alpha\beta}(y)(D_x^\beta u)(\Psi(y)).}
$$

$M_{\alpha\beta}$ 是 $\Psi$ 的一阶到 $|\alpha|$ 阶导数的有限多项式组合，故一致有界。零阶另写成 $Au=u\circ\Psi$。

**教材式 (11) 的求和记号需要澄清。** 若写成 $\beta\le\alpha$ 并按通常“逐分量不超过”解释，一般是不正确的。最简单的反例是交换坐标

$$
\Psi(y_1,y_2)=(y_2,y_1),\qquad
\partial_{y_1}(u\circ\Psi)=(\partial_{x_2}u)\circ\Psi.
$$

此时 $\alpha=(1,0)$、$\beta=(0,1)$，后者并不逐分量小于前者。本讲义统一采用 $1\le|\beta|\le|\alpha|$ 的正确范围。不要与 Leibniz 公式中合法的 $\beta\le\alpha$ 混淆。

### 10.6 由链式法则得到光滑函数的范数估计

每个系数有界，有限和三角不等式与 $L^p$ 换元估计给出

$$
\begin{aligned}
\|D_y^\alpha(Au)\|_{L^p(G)}
&\le\sum_{1\le|\beta|\le|\alpha|}
\|M_{\alpha\beta}\|_\infty
\|(D_x^\beta u)\circ\Psi\|_{L^p(G)}\\
&\le C_\alpha\sum_{1\le|\beta|\le|\alpha|}
\|D_x^\beta u\|_{L^p(\Omega)}.
\end{aligned}
$$

连同零阶估计，对有限多个 $\alpha$ 求和，可得

$$
\boxed{\|Au\|_{m,p,G}\le C\|u\|_{m,p,\Omega}.}
$$

常数依赖于 $m,n,p$ 及正反变换的导数界，不依赖于 $u$。

### 10.7 从光滑函数传到一般 Sobolev 函数：完整证明

先设 $1\le p<\infty$。由 §3.17，取 $u_j\in C^\infty(\Omega)\cap W^{m,p}(\Omega)$，使 $u_j\to u$ 于 $W^{m,p}$。

**第一步：复合序列是 Cauchy 列。** 对光滑差 $u_j-u_k$ 使用上一估计：

$$
\|Au_j-Au_k\|_{m,p,G}
\le C\|u_j-u_k\|_{m,p,\Omega}\to0.
$$

注意当 $\Psi$ 只有 $C^m$ 时，$Au_j$ 未必 $C^\infty$，但至少是 $C^m$，足够进行 $m$ 阶经典求导，且各导数由上述估计属于 $L^p$。

**第二步：用完备性得到极限，再识别它。** 由 $W^{m,p}(G)$ 完备，$Au_j\to v$ 于 $W^{m,p}(G)$。另一方面，$L^p$ 有界性给出

$$
\|Au_j-u\circ\Psi\|_{L^p(G)}
\le C_0^{1/p}\|u_j-u\|_{L^p(\Omega)}\to0.
$$

$L^p$ 极限唯一，所以 $v=u\circ\Psi$。因此 $Au\in W^{m,p}(G)$，范数估计也传到极限。

**第三步：链式法则在弱意义下仍成立。** 每项

$$
M_{\alpha\beta}(D^\beta u_j)\circ\Psi
\longrightarrow M_{\alpha\beta}(D^\beta u)\circ\Psi
\quad\text{于 }L^p(G).
$$

左边的 $D^\alpha(Au_j)$ 也在 $L^p$ 中收敛到 $D^\alpha(Au)$，所以式子传到极限，得到弱链式法则。

也可以完全按教材写测试函数：对 $\theta\in\mathcal D(G)$，

$$
(-1)^{|\alpha|}\int_GAu_jD^\alpha\theta
=\sum_{1\le|\beta|\le|\alpha|}
\int_GM_{\alpha\beta}(D^\beta u_j\circ\Psi)\theta,
$$

两边用 Hölder 通过极限即可。图片中“$D^\beta u_j\to u$”应读为 $D^\beta u_j\to D^\beta u$。

**第四步：用逆变换证明满射和下界。** 对 $A^{-1}v=v\circ\Phi$ 重复同一论证，得

$$
\|A^{-1}v\|_{m,p,\Omega}\le C'\|v\|_{m,p,G}.
$$

于是

$$
\boxed{(C')^{-1}\|u\|_{m,p,\Omega}
\le\|Au\|_{m,p,G}
\le C\|u\|_{m,p,\Omega}.}
$$

$A$ 是有界线性双射，逆也有界，即两个 Sobolev 空间之间的拓扑同构。

### 10.8 如果包括 $p=\infty$，证明必须另补一步

不能使用 $W^{m,\infty}$ 中的光滑范数稠密性，§3.18 已说明它失败。

可以先局部证明弱链式法则：对测试函数支集 $K\Subset G$，$\Psi(K)\Subset\Omega$；取包含它的相对紧开集 $V$。由于 $V$ 有限测度，$u\in W^{m,\infty}(V)$ 蕴含 $u\in W^{m,1}(V)$。在 $V$ 上用有限指数的光滑逼近，按上一节的局部测试函数论证得到链式法则。

再利用各 $D^\beta u$ 与系数的全局本性有界性，得到全域 $W^{m,\infty}$ 估计；对逆变换同理。因此结论也成立，只是不能照抄 $p<\infty$ 的稠密性步骤。

### 10.9 仿射变换与尺度公式

若 $\Phi(x)=Bx+b$，$B$ 可逆，则 $\Psi(y)=B^{-1}(y-b)$，一阶导数为常矩阵，高于一阶的导数全为零。换元和导数估计特别简单。

例如 $y=ax$，$a>0$，$G=a\Omega$，$Au(y)=u(y/a)$，则

$$
D_y^\alpha Au(y)=a^{-|\alpha|}D_x^\alpha u(y/a),
$$

$$
\boxed{\|D_y^\alpha Au\|_{L^p(a\Omega)}
=a^{n/p-|\alpha|}\|D_x^\alpha u\|_{L^p(\Omega)}.}
$$

检查时记住两部分：面积/体积变化给 $a^{n/p}$，每求一次导数给 $a^{-1}$。完整 $W^{m,p}$ 范数包括不同阶数，因此通常没有一个统一的单一缩放幂。

在这些坐标变换条件下，$A$ 也把 $W_0^{m,p}(\Omega)$ 映到 $W_0^{m,p}(G)$：先复合内部紧支集光滑逼近函数；复合后支集仍内部紧，若只剩 $C^m$，再在内部磨光即可。

## 11. 补充：单位分解能否用于协方差


### 11.1 分解一个函数，不等于分解出独立随机变量

单位分解当然给出

$$
f=\sum_j\psi_jf.
$$

但若 $X(x)$ 是随机场，设 $X_j(x)=\psi_j(x)X(x)$，这些 $X_j$ 共同来源于同一个 $X$，通常并不独立。记协方差为 $K(x,y)$，就有

$$
\operatorname{Cov}(X_j(x),X_k(y))
=\psi_j(x)\psi_k(y)K(x,y).
$$

所以正确公式是

$$
\operatorname{Cov}\left(\sum_jX_j(x),\sum_kX_k(y)\right)
=\sum_{j,k}\operatorname{Cov}(X_j(x),X_k(y)),
$$

而不是随意删掉 $j\ne k$ 的交叉项。

对称的双变量代数分解

$$
K(x,y)=\sum_{j,k}\psi_j(x)K(x,y)\psi_k(y)
$$

是成立的，因为两个单位分解的总和均为一。但是单独一个 $j\ne k$ 的交叉项未必是对称的正半定核，不能把它直接称为协方差核。

### 11.2 怎样检验“某一块是协方差核”

实对称核 $K$ 的正半定性要求：任意有限点组 $x_1,\ldots,x_N$ 和实数 $c_1,\ldots,c_N$ 都满足

$$
\sum_{a,b=1}^Nc_ac_bK(x_a,x_b)\ge0.
$$

对协方差矩阵 $\Sigma\succeq0$，同样要求 $c^{\mathsf T}\Sigma c\ge0$。简单地将矩阵的某些元素或某些区域截掉，并不自动保持这个条件。

例如 $D_j\Sigma D_j$ 总是正半定的，但一般

$$
\sum_jD_j\Sigma D_j\ne\Sigma
$$

即使 $\sum_jD_j=I$；缺少的是交叉项 $D_j\Sigma D_k$。

### 11.3 高斯核的一个真正的正半定分解

明确假设 $x,y\in\mathbb R^d$，距离是欧氏距离，长度参数 $\ell>0$。令

$$
K(x,y)=\exp\left(-\frac{|x-y|^2}{\ell^2}\right),\qquad
q_z(x)=\exp\left(-\frac{2|x-z|^2}{\ell^2}\right).
$$

配方得到

$$
|x-z|^2+|y-z|^2
=2\left|z-\frac{x+y}{2}\right|^2+\frac12|x-y|^2.
$$

故由高斯积分，

$$
\int_{\mathbb R^d}q_z(x)q_z(y)\,dz
=\left(\frac{\pi\ell^2}{4}\right)^{d/2}K(x,y).
$$

记 $C_\ell=(4/(\pi\ell^2))^{d/2}$。现在把单位分解放在积分变量 $z$ 上，而不是直接截断矩阵元素：

$$
\boxed{K_j(x,y)=C_\ell\int_{\mathbb R^d}
\psi_j(z)q_z(x)q_z(y)\,dz.}
$$

若 $\psi_j\ge0$ 且 $\sum_j\psi_j=1$，Tonelli 定理给出

$$
\boxed{K(x,y)=\sum_jK_j(x,y).}
$$

并且对任意有限实系数，

$$
\sum_{a,b}c_ac_bK_j(x_a,x_b)
=C_\ell\int\psi_j(z)\left(\sum_ac_aq_z(x_a)\right)^2dz\ge0.
$$

所以每一个 $K_j$ 都是真正的正半定核。对有限采样点，对应的矩阵也满足

$$
\Sigma=\sum_j\Sigma_j,\qquad\Sigma_j\succeq0.
$$

若另行构造互相独立的中心高斯向量 $Z_j$，使 $\operatorname{Cov}(Z_j)=\Sigma_j$，则其和具有协方差 $\Sigma$。可数项时，$\sum_j\operatorname{tr}\Sigma_j=\operatorname{tr}\Sigma<\infty$ 保证独立中心向量之和在 $L^2$ 中收敛。

这里的独立性来自“另外构造独立高斯向量”，而不是单位分解自动带来的。该分解的每一块在隐变量 $z$ 上局部化，并不意味着每个 $K_j(x,y)$ 在 $x,y$ 上都具有紧支集。


单位分解可以把函数或核写成局部项之和；但协方差分解还必须保持对称性和正半定性，独立性也需额外保证。对欧氏高斯核，可以先写成特征函数乘积的积分，再在积分变量上插入非负单位分解，从而得到一族正半定协方差核，其和恰好等于原核。

## 12. 最容易混淆的地方：做题前逐项检查

| 容易写错的话 | 准确说法 |
|---|---|
| 光滑函数稠密，所以紧支集光滑函数也稠密 | 先问支集是在 $\Omega$ 内部，还是在 $\mathbb R^n$ 中；两者不同。 |
| §3.17 要求边界光滑 | 不要求；它只逼近成内部光滑函数。 |
| 每项光滑，所以无穷和光滑 | 需要局部有限或足够强的导数收敛条件。 |
| 一次固定半径的磨光能处理整个开集 | 靠近边界时没有统一安全半径；需要逐块选半径。 |
| 零延拓总保持弱导数 | $W_0$ 元素有保证；一般元素会产生边界分布。 |
| 零延拓属于 $W^{m,p}$ 就一定属于 $W_0$ | 对任意开集不成立，删去单点的区间是反例。 |
| $D_ju=0$，所以 $u$ 在任意开集都取同一个常数 | 需要连通；否则每个连通分支可不同。 |
| $T_u=0$ 意味着每一点 $u(x)=0$ | 只能推出几乎处处为零。 |
| $u\in L^1_{\mathrm{loc}}$，所以可直接控制全空间积分 | 先把支集放进固定紧集。 |
| 坐标变换是 $Au=u\circ\Phi$ | 本文方向为 $\Phi:\Omega\to G$，故 $Au=u\circ\Phi^{-1}$。 |
| 行列式处处非零就有全局范数等价 | 需要统一的上下界和导数界。 |
| 复合求导只出现逐分量 $\beta\le\alpha$ | 正确限制是总阶数 $\lvert\beta\rvert\le\lvert\alpha\rvert$。 |
| 坐标变换证明对 $p=\infty$ 直接用光滑稠密性 | 不行；应局部用有限指数逼近，再利用本性有界性。 |
| 单位分解后的随机部分自然独立 | 不成立，要检查交叉协方差或另行构造独立分量。 |

## 13. 自测题与答案要点

先遮住答案，自行写出证明。能说出“用什么定理、在哪个空间通过极限”，才算真正掌握。

### 题 1：为什么 $W^{1,p}$ 逼近不能只检查函数本身

因为范数还包含弱导数。例子 $u_k(x)=\sin(kx)/k$ 在 $(0,2\pi)$ 上一致趋零，但 $u_k'(x)=\cos(kx)$ 不在 $L^p$ 范数下趋零。因此一致收敛也不能直接替代 $W^{1,p}$ 收敛。

### 题 2：在区间上，为什么 $C_c^\infty$ 不能逼近常数一

若可以，§3.27 将推出 $\mathbf1_{(0,1)}\in W^{1,p}(\mathbb R)$，但其导数为 $\delta_0-\delta_1$，矛盾。也可以用一维边界迹估计。

### 题 3：$\int\phi=0$ 在求紧支集原函数时起什么作用

使从左端积分到支集右方后的累计积分回到零。否则原函数会留下非零常数尾巴，无法紧支撑。

### 题 4：用一句话区分 §3.30 和 §3.31

§3.30 说“零梯度的分布是常数分布”；§3.31 说“由局部可积函数诱导的分布能唯一确定函数的几乎处处等价类”。两者结合才得到 §3.32。

### 题 5：给出 $p=\infty$ 时平移不连续的例子

在 $\mathbb R$ 上取阶跃函数 $g=\mathbf1_{(0,\infty)}$。对每个 $h\ne0$，平移后在一个长度为 $|h|$ 的区间上与原函数相差一，因此 $\|g(\cdot-h)-g\|_\infty=1$。

### 题 6：若 $v(y)=u(y/2)$，一阶导数的 $L^p$ 范数如何缩放

$$
\|\partial_{y_i}v\|_{L^p(2\Omega)}
=2^{n/p-1}\|\partial_{x_i}u\|_{L^p(\Omega)}.
$$

不要漏掉体积变化和求导带来的两个因子。

### 题 7：为什么不能将 $-\Delta u\in L^2$ 直接解释为 $u\in H^2$

这只控制若干二阶分布导数之和，不能直接分别控制全部二阶导数；还涉及边界几何与椭圆正则性。上一课心形凹角问题就是对应例子。

