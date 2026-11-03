# 第九课：Lᵖ 对偶、混合范数、弱 Lᵖ 与 Marcinkiewicz 插值

> 范围：教材 2.43–2.58；依据本次提供的教材第 46–58 页及课堂批注整理。
> 重点：2.43 的两个唯一性证明、混合范数换序、分布函数积分公式，以及 2.58 的截断证明。

## 0. 本节的逻辑路线与记号

本节分为三条相互衔接的线索。

1. **对偶与几何**：一致凸性保证泛函取得范数；Clarkson 不等式保证单位向量的支撑泛函唯一；由此证明 Riesz 表示，再得到自反性。
2. **混合范数**：不同变量采用不同积分指数。逐变量 Hölder 控制乘积，积分型 Minkowski 比较计算范数的顺序。
3. **插值**：分布函数把函数积分转化为水平集测度的积分；弱型估计控制水平集；依赖于输出阈值的截断，把两个端点的弱型估计组合为中间指数的强型估计。

约定：

- $\Omega\subset\mathbb R^n$ 为非空开集，使用 Lebesgue 测度；函数按几乎处处相等识别。
- $X'$ 表示连续线性对偶，$X''=(X')'$。
- $p'$ 表示共轭指数：$1/p+1/p'=1$，约定 $1/\infty=0$。
- 为与教材一致，使用双线性配对 $L_v(u)=\int_\Omega uv$。对复值函数，构造取等函数时必须相应加入复共轭。
- $\delta_u(t)=\mu\{x:|u(x)|>t\}$ 是本节的分布函数，与 Dirac 分布 $\delta_0$ 是不同概念。
- $C_c^\infty(\Omega)$ 与本书的 $C_0^\infty(\Omega)$ 表示同一测试函数空间。

后文调用已学结论：$L^p$ 的完备性；$1<p<\infty$ 时的一致凸性；Clarkson 不等式；Hölder、积分型 Minkowski、Tonelli 和单调收敛定理。

## 1. 2.43：两个方向的存在性与唯一性

### 1.1 准确区分两个命题

设 $1<p<\infty$。

**命题 A：给定泛函，寻找取到范数的向量。** 若 $L\in(L^p)'$ 且 $\|L\|=1$，则存在唯一 $w\in L^p$，使

$$
\|w\|_p=1,\qquad L(w)=1.
$$

**命题 B：给定向量，寻找支撑泛函。** 若 $\|w\|_p=1$，则存在唯一 $L\in(L^p)'$，使

$$
\|L\|=1,\qquad L(w)=1.
$$

“唯一”的对象不同。A 的唯一性来自严格凸性，存在性利用一致凸性和完备性；B 的唯一性还需要 $L^p$ 范数的相应光滑性，教材通过另一组 Clarkson 不等式直接证明。不能把 B 简单归结为“一致凸，所以显然”。

### 1.2 命题 A：从极大化序列得到实际极大点

由算子范数定义，存在 $\|w_j\|_p=1$，使 $|L(w_j)|\to1$。对充分大的 $j$，乘以模为 $1$ 的复数

$$
\frac{\overline{L(w_j)}}{|L(w_j)|},
$$

可令 $L(w_j)>0$ 且 $L(w_j)\to1$，同时保持 $\|w_j\|_p=1$。

任取 $\varepsilon>0$。一致凸性的逆否表述是：存在 $\delta>0$，对单位球中的 $a,b$，

$$
\left\|\frac{a+b}{2}\right\|_p>1-\delta
\quad\Longrightarrow\quad
\|a-b\|_p<\varepsilon.
$$

当 $j,k$ 足够大时，

$$
\left\|\frac{w_j+w_k}{2}\right\|_p
\ge
\left|L\left(\frac{w_j+w_k}{2}\right)\right|
=\frac{L(w_j)+L(w_k)}2
>1-\delta.
$$

所以 $\|w_j-w_k\|_p<\varepsilon$。因此 $(w_j)$ 是 Cauchy 列。由 $L^p$ 完备性，存在 $w$ 使 $w_j\to w$；范数与 $L$ 的连续性给出

$$
\|w\|_p=1,\qquad L(w)=1.
$$

若 $w,z$ 都满足条件，则

$$
1=L\left(\frac{w+z}{2}\right)
\le\left\|\frac{w+z}{2}\right\|_p\le1.
$$

如果 $w\ne z$，一致凸性会使中点范数严格小于 $1$，矛盾。因此 $w=z$。

**证明的关键**：极大化序列一般未必收敛；一致凸性把“两个函数都几乎取到泛函范数”变成“两个函数彼此很近”。

### 1.3 命题 B 的存在性：直接构造

给定 $\|w\|_p=1$，定义

$$
v(x)=
\begin{cases}
|w(x)|^{p-2}\overline{w(x)},&w(x)\ne0,\\
0,&w(x)=0.
\end{cases}
$$

因为 $(p-1)p'=p$，

$$
\int_\Omega |v|^{p'}=\int_\Omega |w|^p=1.
$$

故 $v\in L^{p'}$，$\|v\|_{p'}=1$。令

$$
L_v(u)=\int_\Omega u v.
$$

Hölder 给出 $\|L_v\|\le1$，而

$$
L_v(w)=\int_\Omega|w|^p=1
$$

又给出 $\|L_v\|\ge1$。于是 $\|L_v\|=L_v(w)=1$。

这里无需预先使用 Riesz 表示定理：我们只是从一个已知的 $v$ 构造泛函，并没有断言所有泛函都可如此表示。

### 1.4 命题 B 的唯一性：补全教材省略的代数步骤（课堂作业 1）

假设 $L_1,L_2$ 满足

$$
\|L_1\|=\|L_2\|=1,\qquad L_1(w)=L_2(w)=1.
$$

反设 $L_1\ne L_2$。则存在 $z$，使

$$
d=L_1(z)-L_2(z)\ne0.
$$

先令 $a=2z/d$，则 $L_1(a)-L_2(a)=2$；再令

$$
h=a-\bigl(L_1(a)-1\bigr)w.
$$

逐项计算：

$$
L_1(h)=1,\qquad
L_2(h)=L_2(a)-L_1(a)+1=-1.
$$

这就是教材“乘以适当常数，再加上适当倍数的 $w$”的具体含义；复数域也同样成立。

对任意实数 $t>0$，

$$
\|w+th\|_p\ge |L_1(w+th)|=1+t,
\qquad
\|w-th\|_p\ge |L_2(w-th)|=1+t.
$$

**情形一：$1<p\le2$。** 使用教材 Clarkson 不等式 (33)，取 $a=w+th,b=w-th$：

$$
\left\|\frac{a+b}{2}\right\|_p^p+
\left\|\frac{a-b}{2}\right\|_p^p
\ge\frac{\|a\|_p^p+\|b\|_p^p}{2}.
$$

由于 $(a+b)/2=w$、$(a-b)/2=th$，得到

$$
1+t^p\|h\|_p^p\ge(1+t)^p.
$$

两边减 $1$ 再除以 $t$：

$$
t^{p-1}\|h\|_p^p\ge\frac{(1+t)^p-1}{t}.
$$

令 $t\downarrow0$，左边趋于 $0$，右边趋于 $p>0$，矛盾。

**情形二：$2\le p<\infty$。** 使用教材 Clarkson 不等式 (31)：

$$
\left\|\frac{a+b}{2}\right\|_p^{p'}+
\left\|\frac{a-b}{2}\right\|_p^{p'}
\ge
\left(\frac{\|a\|_p^p+\|b\|_p^p}{2}\right)^{p'/p}.
$$

注意 $p'/p=p'-1$。同样代入可得

$$
1+t^{p'}\|h\|_p^{p'}\ge(1+t)^{p'}.
$$

减 $1$、除以 $t$、令 $t\downarrow0$，因为 $p'>1$，仍得到矛盾。

因此 $L_1=L_2$。

**为什么矛盾发生在小 $t$？** 右边 $(1+t)^s=1+st+o(t)$ 有一阶增长；左边 $1+t^s\|h\|^s$ 的新增项是 $o(t)$，其中 $s>1$。比较的是增长阶数，而非某个大 $t$ 的取值。

## 2. 2.44–2.47：Riesz 表示、自反性及端点

### 2.1 2.44：$1<p<\infty$ 的对偶表示

**定理。** 对每个 $L\in(L^p(\Omega))'$，存在唯一 $v\in L^{p'}(\Omega)$，使

$$
L(u)=\int_\Omega uv,\qquad u\in L^p(\Omega),
\qquad \|L\|=\|v\|_{p'}.
$$

**证明。** $L=0$ 时取 $v=0$。否则令 $M=\|L\|>0$，$\ell=L/M$。由 2.43 A，存在 $\|w\|_p=1$ 且 $\ell(w)=1$。令

$$
v_0=|w|^{p-2}\overline w
$$

并在 $w=0$ 处定义为 $0$。由上一节，$\|L_{v_0}\|=L_{v_0}(w)=1$。由 2.43 B 的唯一性，

$$
\ell=L_{v_0}.
$$

故取 $v=Mv_0$ 即得表示，且 $\|v\|_{p'}=M$。

若 $v_1,v_2$ 表示同一个 $L$，令 $d=v_1-v_2$，取

$$
u=|d|^{p'-2}\overline d
$$

（零点处定义为 $0$）。则 $u\in L^p$，并且

$$
0=\int_\Omega ud=\int_\Omega|d|^{p'}.
$$

所以 $v_1=v_2$ a.e.。

因此 $v\mapsto L_v$ 是 $L^{p'}$ 到 $(L^p)'$ 的线性等距满射，记作

$$
(L^p)' \cong L^{p'}.
$$

### 2.2 2.45：为什么 $(L^1)'$ 等于 $L^\infty$

设 $L\in(L^1)'$，记 $M=\|L\|$。以下证明同时解释教材的“先有限体积，再一般区域”。

**第一步：$\mu(\Omega)<\infty$ 时，限制到 $L^r$。**

任取 $1<r<\infty$。由有限测度嵌入，

$$
|L(u)|\le M\|u\|_1
\le M\mu(\Omega)^{1/r'}\|u\|_r.
$$

因此 $L|_{L^r}$ 是 $L^r$ 上的有界泛函。由 2.44，存在 $v_r\in L^{r'}$，满足

$$
L(u)=\int_\Omega uv_r,\qquad u\in L^r,
\qquad
\|v_r\|_{r'}\le M\mu(\Omega)^{1/r'}.
$$

**第二步：不同 $r$ 得到的表示函数实际上相同。**

对任意 $\varphi\in C_c^\infty(\Omega)$，

$$
\int_\Omega\varphi(v_r-v_s)=0.
$$

$v_r-v_s\in L^1_{\mathrm{loc}}$，故由正则分布的唯一性，$v_r=v_s$ a.e.。固定一个代表 $v$，即可得到

$$
\|v\|_a\le M\mu(\Omega)^{1/a},\qquad 1<a<\infty.
$$

这里无须对不可数个 $r$ 的例外零测集取并；固定一个 $v$ 后，各个范数结论都对其等价类成立。

**第三步：让积分指数趋于无穷，得到本性有界性。**

对 $b>M$，Chebyshev 不等式给出

$$
\mu\{|v|>b\}
\le b^{-a}\|v\|_a^a
\le\mu(\Omega)(M/b)^a.
$$

令 $a\to\infty$，可得 $\mu\{|v|>b\}=0$，从而 $\|v\|_\infty\le M$。

**第四步：把表示推广到全部 $L^1$。**

对 $u\in L^1$，令 $u_N=u\mathbf1_{\{|u|\le N\}}$。由于区域测度有限，$u_N\in L^r$，且 $u_N\to u$ 于 $L^1$。因此

$$
L(u)=\lim_NL(u_N)
=\lim_N\int_\Omega u_Nv
=\int_\Omega uv.
$$

最后 Hölder 给出 $M\le\|v\|_\infty$，所以 $\|v\|_\infty=M$。

**第五步：$\mu(\Omega)$ 可以无限。**

取 $\Omega_j=\Omega\cap B_j(0)$。把 $L^1(\Omega_j)$ 的函数零延拓到 $\Omega$，再作用 $L$，得到范数不超过 $M$ 的限制泛函。由有限体积情形，存在

$$
v_j\in L^\infty(\Omega_j),\qquad \|v_j\|_\infty\le M.
$$

表示函数的唯一性保证 $v_{j+1}=v_j$ a.e. 于 $\Omega_j$。去掉可数个零测集后，可拼成 $v\in L^\infty(\Omega)$，且 $\|v\|_\infty\le M$。

因为 $u\mathbf1_{\Omega_j}\to u$ 于 $L^1(\Omega)$，再次取极限即得 $L(u)=\int uv$，并有范数相等。唯一性可在每个有限测度子集上用复相位测试函数证明。

所以

$$
\boxed{(L^1(\Omega))'\cong L^\infty(\Omega).}
$$

### 2.3 2.46：自反性必须核对自然嵌入

**定理。** 在本书的非空 Lebesgue 开集情形，$L^p(\Omega)$ 在 $1\le p\le\infty$ 中自反，当且仅当 $1<p<\infty$。

对 $1<p<\infty$，设 $X=L^p$，任取 $\Phi\in X''$。定义

$$
\Psi(v)=\Phi(L_v),\qquad v\in L^{p'}.
$$

由于 $\|L_v\|=\|v\|_{p'}$，$\Psi$ 是 $L^{p'}$ 上的有界线性泛函。再次应用 Riesz 表示，存在 $u\in L^p$，使

$$
\Phi(L_v)=\Psi(v)=\int_\Omega vu=L_v(u).
$$

又因每个 $L\in X'$ 都是某个 $L_v$，故

$$
\Phi(L)=L(u),\qquad L\in X'.
$$

这正说明 $\Phi=J(u)$，其中 $J:X\to X''$ 是自然映射 $J(u)(L)=L(u)$。所以 $J$ 满射，$X$ 自反。

**注意**：仅写 $X''\cong X$ 不足以完成一般 Banach 空间的自反性论证；这里已经证明同构确实由自然嵌入实现。

端点方面，$L^1(\Omega)$ 可分，而 $L^\infty(\Omega)$ 不可分。结合“可分自反空间的对偶可分”和“$X$ 自反当且仅当 $X'$ 自反”，可知两个端点均不自反。这是本书测度空间下的结论；有限原子测度空间可能是有限维，不能不加条件照搬。

### 2.4 2.47：为什么 $(L^\infty)'$ 不等于 $L^1$

每个 $v\in L^1$ 仍然给出 $L^\infty$ 上的泛函

$$
L_v(u)=\int_\Omega uv,\qquad \|L_v\|=\|v\|_1.
$$

但此映射不是满射；否则自然的两次对偶表示会推出 $L^1$ 自反，与上述结论矛盾。

更一般的描述涉及定义在可测集上的有界变差、有限可加集合函数，并要求其在 Lebesgue 零测集上为零。这里的“有限可加”不能擅自换成“可数可加”；本节只需牢记

$$
L^1\ \text{等距嵌入}\ (L^\infty)',\qquad
L^1\ \text{并不穷尽}\ (L^\infty)'.
$$

### 2.5 课堂补充：弱收敛加范数收敛何时推出强收敛

任意赋范空间中，强收敛推出弱收敛；反向通常不成立。

在一致凸空间中，若 $u_j\rightharpoonup u$ 且 $\|u_j\|\to\|u\|$，则 $u_j\to u$ 强收敛。

若 $u=0$，结论直接来自范数收敛。若 $u\ne0$，对充分大的 $j$ 定义

$$
a_j=\frac{u_j}{\|u_j\|},\qquad a=\frac{u}{\|u\|}.
$$

则 $a_j\rightharpoonup a$。取 $\|L\|=1$ 且 $L(a)=1$ 的支撑泛函，由 Hahn–Banach 定理可得。于是

$$
1\ge\left\|\frac{a_j+a}{2}\right\|
\ge\operatorname{Re}L\left(\frac{a_j+a}{2}\right)\longrightarrow1.
$$

一致凸性推出 $\|a_j-a\|\to0$，再结合范数收敛即得结论。特别地，此性质适用于 $1<p<\infty$ 的 $L^p$。

在 Hilbert 空间可直接展开

$$
\|u_j-u\|^2
=\|u_j\|^2+\|u\|^2-2\operatorname{Re}(u_j,u)\to0.
$$

## 3. 2.48—2.52：混合范数，先算哪个变量非常重要

### 3.1 定义与记号

对二维可测函数 $u=u(x,y)$，定义

$$
\|u\|_{L_y^b(L_x^a)}
=\left(\int_{\mathbb R}
\left(\int_{\mathbb R}|u(x,y)|^a\,dx\right)^{b/a}dy\right)^{1/b},
\qquad 0<a,b<\infty.
$$

**从内向外读：先对 $x$ 取 $L^a$，得到关于 $y$ 的函数，再对它取 $L^b$。** 若某指数为 $\infty$，就把该步骤替换为本质上确界。

例如

$$
\|u\|_{L_y^\infty(L_x^a)}
=\operatorname*{ess\,sup}_y
\left(\int_{\mathbb R}|u(x,y)|^a\,dx\right)^{1/a},
$$

而

$$
\|u\|_{L_x^a(L_y^\infty)}
=\left(\int_{\mathbb R}
\left(\operatorname*{ess\,sup}_y|u(x,y)|\right)^a dx\right)^{1/a}.
$$

这两个表达式通常不同。

一般地，对指数向量 $\mathbf p=(p_1,\dots,p_n)$，

$$
\|u\|_{\mathbf p}
=\big\|\cdots\|\|u\|_{L^{p_1}(dx_1)}
\|_{L^{p_2}(dx_2)}\cdots\big\|_{L^{p_n}(dx_n)}.
$$

$L^{\mathbf p}$ 是此量有限的可测函数的几乎处处等价类所组成的空间。所有 $p_i\ge1$ 时，它是 Banach 空间；若某指数小于 $1$，对应的表达式一般只能作为拟范数使用。

两个基本核对例子：

1. 所有指数都等于 $p$ 时，由 Tonelli 定理，混合范数等于通常的 $L^p(\mathbb R^n)$ 范数。
2. 若 $u(x,y)=f(x)g(y)$，则

$$
\|u\|_{L_y^b(L_x^a)}=\|f\|_a\|g\|_b.
$$

第二个例子说明：混合范数允许不同方向具有不同的可积性。

**关于完备性的补充。** 当所有指数至少为 $1$ 时，逐层使用 Minkowski 得到三角不等式；逐层使用单调收敛得到混合范数的单调收敛性质。对 Cauchy 序列选取子列，使相邻差的混合范数之和有限，再对这些差的绝对值求和，便得到几乎处处收敛的望远镜级数及混合范数收敛。这与通常 $L^p$ 完备性的证明相同；遇到 $\infty$ 指数时，对应步骤使用本质上确界的单调性质。

### 3.2 2.49：混合范数 Hölder 不等式

设 $0<p_i,q_i\le\infty$，并逐坐标定义 $r_i$：

$$
\frac1{r_i}=\frac1{p_i}+\frac1{q_i}.
$$

那么

$$
\boxed{\|uv\|_{\mathbf r}\le
\|u\|_{\mathbf p}\|v\|_{\mathbf q}.}
$$

下面用二维情形说明证明的全部机制。对几乎处处的 $y$，先在 $x$ 变量使用 Hölder：

$$
\|u(\cdot,y)v(\cdot,y)\|_{r_1}
\le \|u(\cdot,y)\|_{p_1}\|v(\cdot,y)\|_{q_1}.
$$

记右侧两个因子为 $U(y),V(y)$。再对 $y$ 使用 Hölder：

$$
\begin{aligned}
\|uv\|_{L_y^{r_2}(L_x^{r_1})}
&\le\|UV\|_{r_2}\\
&\le\|U\|_{p_2}\|V\|_{q_2}\\
&=\|u\|_{L_y^{p_2}(L_x^{p_1})}
\|v\|_{L_y^{q_2}(L_x^{q_1})}.
\end{aligned}
$$

高维情形逐变量重复即可。

为什么允许某些指数小于 $1$？因为对于一维乘积估计，实际对 $|u|^{r_i}|v|^{r_i}$ 使用的是共轭指数 $p_i/r_i$ 与 $q_i/r_i$，它们满足倒数之和为 $1$。这不是直接对一个小于 $1$ 的指数使用经典 Hölder。涉及 $\infty$ 的情形直接用本质上界估计。

同理，多因子版本为

$$
\left\|\prod_{j=1}^m u_j\right\|_{\mathbf r}
\le\prod_{j=1}^m\|u_j\|_{\mathbf p_j},
\qquad
\frac1{r_i}=\sum_{j=1}^m\frac1{p_{j,i}}.
$$

### 3.3 2.50—2.51：交换计算顺序的方向

设 $0<a\le b\le\infty$，则

$$
\boxed{
\|u\|_{L_y^b(L_x^a)}
\le
\|u\|_{L_x^a(L_y^b)}.
}
\tag{M}
$$

记忆方式是：**保持每个变量对应的指数不变，从内到外先小指数后大指数，得到的量较小。**

这不是有限测度空间上 $L^b\subset L^a$ 的结论；这里比较的是同一个函数的两种迭代顺序，无需底空间具有有限测度。

**证明：$b<\infty$。** 设 $r=b/a\ge1$，对 $|u|^a$ 使用积分型 Minkowski：

$$
\begin{aligned}
\|u\|_{L_y^b(L_x^a)}^a
&=\left\|\int_{\mathbb R}|u(x,\cdot)|^a\,dx\right\|_{L_y^r}\\
&\le\int_{\mathbb R}\big\||u(x,\cdot)|^a\big\|_{L_y^r}\,dx\\
&=\int_{\mathbb R}
\left(\int_{\mathbb R}|u(x,y)|^b\,dy\right)^{a/b}dx\\
&=\|u\|_{L_x^a(L_y^b)}^a.
\end{aligned}
$$

再取 $a$ 次根。若右边无穷大，不等式自动成立；一般可通过非负截断与单调收敛理解上述计算。

**证明：$b=\infty$，$a<\infty$。** 使用

$$
\operatorname*{ess\,sup}_y\int |u(x,y)|^a\,dx
\le\int\operatorname*{ess\,sup}_y|u(x,y)|^a\,dx.
$$

两边取 $a$ 次根即得。若两指数都是 $\infty$，两种顺序给出相同的本质上确界。

多变量情形，通过相邻交换可把任意顺序排成从内到外非降序或非升序；相邻交换不等式和外层取范数的单调性说明：

- 从内到外指数非降序：所有排列中最小；
- 从内到外指数非升序：所有排列中最大。

注意：交换的是“变量及其对应指数”的位置，不能把 $x$ 方向的指数直接改成 $y$ 方向的指数。

### 3.4 作业 2：两个具体混合范数的大小

令

$$
A=\left[\int_{\mathbb R}
\left(\int_{\mathbb R}|u(x,y)|^3\,dx\right)^{2/3}dy\right]^{1/2},
$$

$$
B=\left[\int_{\mathbb R}
\left(\int_{\mathbb R}|u(x,y)|^2\,dy\right)^{3/2}dx\right]^{1/3}.
$$

则

$$
\boxed{B\le A.}
$$

这里 $A=L_y^2(L_x^3)$，$B=L_x^3(L_y^2)$；$B$ 从内到外是 $2,3$，所以较小。

可直接核对：

$$
\begin{aligned}
B^2
&=\left\|\int_{\mathbb R}|u(\cdot,y)|^2\,dy\right\|_{L_x^{3/2}}\\
&\le\int_{\mathbb R}
\big\||u(\cdot,y)|^2\big\|_{L_x^{3/2}}\,dy\\
&=\int_{\mathbb R}
\left(\int_{\mathbb R}|u(x,y)|^3\,dx\right)^{2/3}dy=A^2.
\end{aligned}
$$

一般不能改成等号。例如取

$$
u(x,y)=\sum_{j=1}^N
\mathbf1_{[j,j+1)}(x)\mathbf1_{[j,j+1)}(y).
$$

直接计算得到 $A=N^{1/2}$，$B=N^{1/3}$。当 $N>1$ 时严格不等；当函数可分离为 $f(x)g(y)$ 时，两边相等。

### 3.5 2.52：离散及混合版本

把 Lebesgue 积分换成计数测度下的求和，同一论证给出混合 $\ell^p$ 不等式。例如 $0<a\le b<\infty$ 时，

$$
\left[\sum_j\left(\sum_i|a_{ij}|^a\right)^{b/a}\right]^{1/b}
\le
\left[\sum_i\left(\sum_j|a_{ij}|^b\right)^{a/b}\right]^{1/a}.
$$

某一方向积分、另一方向求和也完全相同。本质都是在乘积测度空间上使用 Minkowski。

## 4. 2.53—2.57：把函数大小转化为水平集大小

### 4.1 2.53：分布函数及基本性质

对可测函数 $u$ 定义

$$
\Omega_{u,t}=\{x\in\Omega:|u(x)|>t\},
\qquad d_u(t)=\mu(\Omega_{u,t}),\quad t\ge0.
$$

$d_u(t)$ 回答：“函数绝对值超过高度 $t$ 的地方，占多大体积？”教材把它记为 $\delta_u(t)$，这里写成 $d_u$，避免与 Dirac 分布混淆。

**性质一：单调性。** 若 $s<t$，则 $\Omega_{u,t}\subset\Omega_{u,s}$，所以 $d_u(t)\le d_u(s)$。若 $|u|\le|v|$ 几乎处处，则 $d_u\le d_v$。

**性质二：右连续。** 因为

$$
\{|u|>t\}=\bigcup_{k=1}^\infty\{|u|>t+1/k\},
$$

右边是递增集合列，测度的下连续性给出

$$
d_u(t+1/k)\longrightarrow d_u(t).
$$

结合单调性即得右连续，允许值为 $+\infty$。一般不要求左连续；水平集 $\{|u|=t\}$ 可能造成跳跃。

**性质三：单调逼近。** 若 $|u_j|\uparrow|u|$ 几乎处处，则对每个 $t\ge0$，

$$
\{|u|>t\}=\bigcup_j\{|u_j|>t\}
\quad\text{（忽略一个零测集）},
$$

所以 $d_{u_j}(t)\uparrow d_u(t)$。

**性质四：齐次性。** $c\ne0$ 时，

$$
d_{cu}(t)=d_u(t/|c|).
$$

**性质五：和的水平集估计。** 对 $s,t>0$，

$$
\{|u+v|>s+t\}\subset
\{|u|>s\}\cup\{|v|>t\},
$$

于是

$$
d_{u+v}(s+t)\le d_u(s)+d_v(t).
$$

特别地，

$$
\boxed{d_{u+v}(2t)\le d_u(t)+d_v(t).}
$$

**性质六：Chebyshev 不等式。** 若 $u\in L^p$，$0<p<\infty$，则

$$
t^p d_u(t)
\le\int_{\{|u|>t\}}|u|^p
\le\|u\|_p^p,
$$

从而

$$
\boxed{d_u(t)\le t^{-p}\|u\|_p^p,\qquad t>0.}
$$

### 4.2 2.54：层蛋糕公式——作业 3

对任意可测 $u$ 和 $0<p<\infty$，有

$$
\boxed{\int_\Omega|u(x)|^p\,dx
=p\int_0^\infty t^{p-1}d_u(t)\,dt.}
\tag{LC}
$$

等式允许两边同时为 $+\infty$，因此证明之前不必假设 $u\in L^p$。

**证明一：Tonelli，最适合记忆和考试。**

对每个 $x$，

$$
|u(x)|^p
=\int_0^{|u(x)|}p\,t^{p-1}\,dt
=\int_0^\infty p\,t^{p-1}
\mathbf1_{\{t<|u(x)|\}}\,dt.
$$

被积函数非负，Tonelli 定理允许换序：

$$
\begin{aligned}
\int_\Omega|u(x)|^p\,dx
&=\int_0^\infty p\,t^{p-1}
\left(\int_\Omega\mathbf1_{\{|u(x)|>t\}}\,dx\right)dt\\
&=p\int_0^\infty t^{p-1}d_u(t)\,dt.
\end{aligned}
$$

这里应引用 **Tonelli**，因为尚未证明绝对可积；不能把“先知道积分有限”作为换序前提。

**证明二：教材的简单函数逼近方法。**

若 $s=\sum_{j=1}^m a_j\mathbf1_{E_j}$，其中 $a_j\ge0$、$E_j$ 两两不交，则

$$
d_s(t)=\sum_{j=1}^m\mu(E_j)\mathbf1_{[0,a_j)}(t),
$$

所以

$$
p\int_0^\infty t^{p-1}d_s(t)\,dt
=\sum_j a_j^p\mu(E_j)=\int_\Omega s^p.
$$

再取非负简单函数 $s_j\uparrow|u|$。由 $s_j^p\uparrow|u|^p$ 和 $d_{s_j}\uparrow d_u$，对两边分别使用单调收敛定理，即得一般情形。

几何解释：$\int |u|^p$ 是按空间位置累计；右边是按高度累计。后面的插值证明正是先估计“超过每个高度的集合”，再把所有高度积分起来。

### 4.3 2.55：弱 $L^p$ 空间

对 $0<p<\infty$ 定义

$$
[u]_p=\sup_{t>0}t\,d_u(t)^{1/p},
\qquad
L^{p,\infty}(\Omega)
=\{u:[u]_p<\infty\}.
$$

这就是教材的 weak-$L^p$。等价地，

$$
[u]_p\le C
\quad\Longleftrightarrow\quad
d_u(t)\le(C/t)^p\quad\text{对所有 }t>0.
$$

由 Chebyshev，

$$
\boxed{L^p\subset L^{p,\infty},\qquad [u]_p\le\|u\|_p.}
$$

但反向包含通常不成立。设 $x_0\in\Omega$，取

$$
u(x)=|x-x_0|^{-n/p}.
$$

在 $x_0$ 的取值任意指定。若 $\omega_n$ 是单位球体积，则

$$
d_u(t)\le
\mu(B(x_0,t^{-p/n}))
=\omega_n t^{-p}.
$$

所以 $u\in L^{p,\infty}(\Omega)$。然而在某个 $B(x_0,\rho)\subset\Omega$ 上，

$$
\int_{B(x_0,\rho)}|u|^p\,dx
=n\omega_n\int_0^\rho r^{-1}\,dr=\infty.
$$

这是临界奇性：恰好满足弱 $L^p$，却不能属于强 $L^p$。

弱 $L^p$ 的“弱”描述的是可积性要求，**不是 $L^p$ 的弱拓扑，也不是弱收敛**。

**拟三角不等式。** 由水平集估计，

$$
[u+v]_p^p\le2^p([u]_p^p+[v]_p^p),
$$

因此

$$
[u+v]_p\le
2([u]_p^p+[v]_p^p)^{1/p}.
$$

当 $p\ge1$ 时，进一步有

$$
[u+v]_p\le2([u]_p+[v]_p).
$$

当 $0<p<1$ 时，可以用常数 $2^{1/p}$ 得到
$[u+v]_p\le2^{1/p}([u]_p+[v]_p)$。

图片最后一行把 $2([u]_p^p+[v]_p^p)^{1/p}$ 直接写成 $2([u]_p+[v]_p)$ 的等号不成立；对于 $p\ge1$，应使用不等号。这不影响“拟范数”的结论。

为什么单独的弱估计不能推出强估计？把 $d_u(t)\le C^p t^{-p}$ 直接代入层蛋糕公式，只能得到

$$
\|u\|_p^p\le pC^p\int_0^\infty\frac{dt}{t},
$$

右侧发散。要得到强估计，必须在不同高度使用不同的信息；这正是插值中的截断思想。

### 4.4 2.56：次线性算子、强型与弱型

设 $F$ 把一个可测函数向量空间映到另一个可测函数空间。这里称 $F$ 次线性，是指

$$
|F(u+v)|\le|F(u)|+|F(v)|,\qquad
|F(cu)|=|c|\,|F(u)|
$$

几乎处处成立。线性算子满足这些条件，但次线性算子不一定线性。

对于 $1\le p\le\infty$：

- **强型 $(p,q)$**：存在与 $u$ 无关的 $C$，使 $\|F(u)\|_q\le C\|u\|_p$。
- **弱型 $(p,q)$**，$q<\infty$：存在 $C$，使 $[F(u)]_q\le C\|u\|_p$。
- 弱型 $(p,\infty)$ 按本节约定就是强型 $(p,\infty)$。

有限 $q$ 时，弱型条件等价于

$$
d_{F(u)}(t)\le
\left(\frac{C\|u\|_p}{t}\right)^q
\quad(t>0).
$$

强型推出弱型，反向通常不成立。输入空间 $\Omega$ 与输出空间 $\Omega'$ 可以不同，二者的维数也不必相同。

### 4.5 2.57：为什么定义域是两个空间之和

$$
L^{p_1}+L^{p_2}
=\{f+g:f\in L^{p_1},\ g\in L^{p_2}\}.
$$

若 $p_1<p<p_2$，对 $u\in L^p$ 及 $T>0$，定义

$$
u_{>T}=u\mathbf1_{\{|u|>T\}},
\qquad
u_{\le T}=u\mathbf1_{\{|u|\le T\}}.
$$

则

$$
\int|u_{>T}|^{p_1}
\le T^{p_1-p}\|u\|_p^p,
\qquad
\int|u_{\le T}|^{p_2}
\le T^{p_2-p}\|u\|_p^p.
$$

若 $p_2=\infty$，第二个估计改为 $\|u_{\le T}\|_\infty\le T$。

所以 $u=u_{>T}+u_{\le T}\in L^{p_1}+L^{p_2}$。在无限测度空间，$u$ 不一定同时属于两个端点空间，但可以拆成分别属于它们的两部分。由此也可看出：

> 大幅值部分交给较小的输入指数；小幅值部分交给较大的输入指数。

这句话中的“大小”是函数的幅值，不是空间位置，也不是输出指数 $q_i$ 的大小。

## 5. 2.58：Marcinkiewicz 插值定理——本节重点

### 5.1 完整陈述

设

$$
1\le p_1\le q_1<\infty,\qquad
1\le p_2\le q_2\le\infty,\qquad q_1<q_2.
$$

取 $0<\theta<1$，令

$$
\frac1p=\frac{1-\theta}{p_1}+\frac{\theta}{p_2},
\qquad
\frac1q=\frac{1-\theta}{q_1}+\frac{\theta}{q_2}.
\tag{I}
$$

约定 $1/\infty=0$。设 $F$ 是从
$L^{p_1}(\Omega)+L^{p_2}(\Omega)$ 到 $\Omega'$ 上可测函数空间的次线性算子，且

$$
[F(f)]_{q_i,\Omega'}\le K_i\|f\|_{p_i,\Omega},
\qquad i=1,2,
$$

其中 $q_i=\infty$ 时，左边按 $L^\infty$ 范数理解。则

$$
\boxed{\|F(u)\|_{q,\Omega'}\le C\|u\|_{p,\Omega}
\quad\text{对所有 }u\in L^p(\Omega).}
$$

常数 $C$ 只依赖于这些指数及 $K_1,K_2$，不依赖于 $u$。

可将端点常数适当增大，故下文涉及除法时均取 $K_1,K_2>0$。

以下省略积分区域的下标。所有输入积分在 $\Omega$ 上，所有 $F(u)$ 的分布函数及输出范数在 $\Omega'$ 上。

**读定理时先检查四件事。**

1. 两个端点只要求弱型，结论却是中间点的强型。
2. 插值的是倒数指数 $(1/p,1/q)$，不是 $(p,q)$ 本身。
3. 假设明确要求 $p_i\le q_i$。证明中这使 $q_i/p_i\ge1$，从而能使用积分型 Minkowski。
4. $q_1<q_2$ 不推出 $p_1<p_2$；输入指数可能同序、反序或相等。不同情形的截断分工必须区别处理。

### 5.2 证明的五个动作

$$
\begin{gathered}
\text{幅值截断}\ \longrightarrow\ \text{次线性与水平集包含}
\ \longrightarrow\ \text{两个弱型估计}\\
\longrightarrow\ \text{层蛋糕与 Minkowski}
\ \longrightarrow\ \text{指数配平}.
\end{gathered}
$$

对每个输出高度 $t$，单独选择输入截断高度 $T=T(t)$。因此不同的 $t$ 使用不同的分解，这是合法且必要的。若固定一个 $T$ 对所有高度积分，通常会在 $0$ 或 $\infty$ 处得到发散的积分。

下面先给出计算较直接的“硬截断”完整证明，再解释它与教材“削顶截断”的关系。两种分解都满足 $u=$大部分$+$小部分，但各自的分布函数公式不能混用。

### 5.3 主情形：$q_2<\infty$ 且 $p_1<p_2$

此时 $p_1<p<p_2$，$q_1<q<q_2$。由齐次性，只需对

$$
\|u\|_p=1
$$

证明一个与 $u$ 无关的界。若 $u=0$，结论由齐次性直接成立。

**第一步：选择使指数配平的截断高度。**

令

$$
r_i=\frac{q_i}{p_i}\ge1,
$$

$$
c=
\frac{p_1(q-q_1)}{q_1(p-p_1)}
=\frac{p_2(q_2-q)}{q_2(p_2-p)}>0,
\qquad T=t^c.
\tag{C}
$$

两个表达式相等来自插值关系 (I)。具体地，

$$
\frac{q-q_1}{q q_1}
=\theta\left(\frac1{q_1}-\frac1{q_2}\right),
\qquad
\frac{p-p_1}{p p_1}
=\theta\left(\frac1{p_1}-\frac1{p_2}\right),
$$

在另一端点用 $1-\theta$ 可得到相同的比值。

后面真正使用的形式是

$$
\boxed{
p_i+\frac{q-q_i}{c r_i}=p,\qquad i=1,2.
}
\tag{B}
$$

选择 $c$ 的目的，就是最终把积分中的 $|u|$ 的幂次化为 $p$。

令

$$
B_t=u\mathbf1_{\{|u|>t^c\}},\qquad
S_t=u\mathbf1_{\{|u|\le t^c\}}.
$$

由第 4.5 节，$B_t\in L^{p_1}$，$S_t\in L^{p_2}$。

**第二步：把两个弱型估计加在不同部分上。**

次线性给出

$$
|F(u)|\le|F(B_t)|+|F(S_t)|.
$$

因此

$$
\{|F(u)|>2t\}
\subset\{|F(B_t)|>t\}\cup\{|F(S_t)|>t\}.
$$

两个端点弱型估计推出

$$
\begin{aligned}
d_{F(u)}(2t)
&\le K_1^{q_1}t^{-q_1}
\left(\int_{\{|u|>t^c\}}|u|^{p_1}\,dx\right)^{r_1}\\
&\quad+
K_2^{q_2}t^{-q_2}
\left(\int_{\{|u|\le t^c\}}|u|^{p_2}\,dx\right)^{r_2}.
\end{aligned}
\tag{D}
$$

注意：次线性不保证
$|F(B_t+S_t)|\le|F(B_t)+F(S_t)|$。
证明只需要上面的绝对值之和与集合包含。

**第三步：层蛋糕公式转成两个积分。**

即使暂时不知道 $F(u)\in L^q$，层蛋糕等式仍在扩展实数意义下成立。变量代换给出

$$
\|F(u)\|_q^q
=2^q q\int_0^\infty t^{q-1}d_{F(u)}(2t)\,dt.
$$

定义

$$
I_1=\int_0^\infty t^{q-q_1-1}
\left(\int_{\{|u|>t^c\}}|u|^{p_1}\,dx\right)^{r_1}dt,
$$

$$
I_2=\int_0^\infty t^{q-q_2-1}
\left(\int_{\{|u|\le t^c\}}|u|^{p_2}\,dx\right)^{r_2}dt.
$$

则

$$
\|F(u)\|_q^q\le2^q q
\big(K_1^{q_1}I_1+K_2^{q_2}I_2\big).
\tag{E}
$$

**第四步：详细估计 $I_1$。**

在测度 $t^{q-q_1-1}dt$ 下使用积分型 Minkowski：

$$
\begin{aligned}
I_1^{1/r_1}
&\le\int_\Omega |u(x)|^{p_1}
\left(
\int_0^\infty
t^{q-q_1-1}\mathbf1_{\{t^c<|u(x)|\}}\,dt
\right)^{1/r_1}dx\\
&=\int_\Omega |u(x)|^{p_1}
\left(\int_0^{|u(x)|^{1/c}}t^{q-q_1-1}\,dt\right)^{1/r_1}dx\\
&=(q-q_1)^{-1/r_1}
\int_\Omega |u(x)|^{p_1+(q-q_1)/(c r_1)}\,dx\\
&=(q-q_1)^{-1/r_1}\int_\Omega|u|^p\,dx.
\end{aligned}
$$

在 $u(x)=0$ 处原被积项为零，按零处理即可。积分在 $t=0$ 处收敛，恰好因为 $q>q_1$。由归一化，

$$
\boxed{I_1\le\frac1{q-q_1}.}
$$

**第五步：详细估计 $I_2$。**

同样在测度 $t^{q-q_2-1}dt$ 下使用 Minkowski：

$$
\begin{aligned}
I_2^{1/r_2}
&\le\int_\Omega |u(x)|^{p_2}
\left(
\int_0^\infty
t^{q-q_2-1}\mathbf1_{\{|u(x)|\le t^c\}}\,dt
\right)^{1/r_2}dx\\
&=\int_\Omega |u(x)|^{p_2}
\left(\int_{|u(x)|^{1/c}}^\infty t^{q-q_2-1}\,dt\right)^{1/r_2}dx\\
&=(q_2-q)^{-1/r_2}
\int_\Omega|u(x)|^{p_2+(q-q_2)/(c r_2)}\,dx\\
&=(q_2-q)^{-1/r_2}\int_\Omega|u|^p\,dx.
\end{aligned}
$$

这里在 $\{|u|=0\}$ 上直接把原函数视为零，不写 $0$ 与无穷大的乘积。积分在 $t=\infty$ 处收敛，恰好因为 $q<q_2$。所以

$$
\boxed{I_2\le\frac1{q_2-q}.}
$$

上述 Minkowski 可以先在有界积分区间、幅值和空间均截断的函数上应用，再用单调收敛；因此不存在以待证可积性作为前提的循环。

**第六步：恢复一般范数。**

代回 (E)，当 $\|u\|_p=1$ 时，

$$
\|F(u)\|_q
\le
2\left[
q\left(
\frac{K_1^{q_1}}{q-q_1}
+\frac{K_2^{q_2}}{q_2-q}
\right)
\right]^{1/q}
=:C.
$$

对一般非零 $u$，将结果用于 $u/\|u\|_p$，再用齐次性：

$$
\|F(u)\|_q
=\|u\|_p
\left\|F\left(\frac{u}{\|u\|_p}\right)\right\|_q
\le C\|u\|_p.
$$

这也证明了 $F(u)\in L^q$。这里的 $C$ 是一个有效常数，不宣称最优；考试若只要求有界性，不必追求最优常数。

### 5.4 有限端点的另外两种情况

**情况 A：$p_2<p_1$。**

此时 $p_2<p<p_1$，公式 (C) 中的 $c<0$，且 (B) 仍成立。端点分工应改为：

$$
\text{端点 }(p_1,q_1)\text{ 控制 }S_t,\qquad
\text{端点 }(p_2,q_2)\text{ 控制 }B_t.
$$

因为 $c<0$，对于 $a>0$，

$$
a\le t^c\Longleftrightarrow t\le a^{1/c},
\qquad
a>t^c\Longleftrightarrow t>a^{1/c}.
$$

于是端点 $1$ 的内层 $t$ 积分仍是
$\int_0^{|u|^{1/c}}t^{q-q_1-1}dt$，
端点 $2$ 的仍是
$\int_{|u|^{1/c}}^\infty t^{q-q_2-1}dt$。
其余计算逐行与第 5.3 节相同，包括最终常数。

| 输入指数关系 | $c$ 的符号 | 端点 $1$ 接收 | 端点 $2$ 接收 |
|---|---:|---|---|
| $p_1p_2$ | 负 | 小幅值 | 大幅值 |

**情况 B：$p_1=p_2=p$。**

此时不能使用分母含 $p_i-p$ 的公式。令 $A=\|u\|_p$。两个弱型估计直接给出

$$
d_{F(u)}(t)
\le\min\left\{
\left(\frac{K_1A}{t}\right)^{q_1},
\left(\frac{K_2A}{t}\right)^{q_2}
\right\}.
$$

不妨把 $K_i$ 选为正数。令

$$
s_0=
\left(\frac{K_2^{q_2}}{K_1^{q_1}}\right)^{1/(q_2-q_1)},
\qquad t_0=As_0.
$$

在 $(0,t_0)$ 使用 $q_1$ 估计，在 $(t_0,\infty)$ 使用 $q_2$ 估计：

$$
\begin{aligned}
\|F(u)\|_q^q
&\le qK_1^{q_1}A^{q_1}
\frac{t_0^{q-q_1}}{q-q_1}
+qK_2^{q_2}A^{q_2}
\frac{t_0^{q-q_2}}{q_2-q}\\
&=q\left[
\frac{K_1^{q_1}s_0^{q-q_1}}{q-q_1}
+\frac{K_2^{q_2}s_0^{q-q_2}}{q_2-q}
\right]A^q.
\end{aligned}
$$

这给出了所需强型估计，也说明输入指数相等并非定理的例外，只是证明方式要改变。

### 5.5 $q_2=\infty$：让一个输出部分消失

这个端点的基本思想是：选择 $T$，使分给第二端点的部分满足

$$
\|F(\text{该部分})\|_\infty\le t.
$$

于是这一部分在高度 $t$ 以上的水平集为空，原来两个分布函数只剩一个要估计。

**先设 $p_2<\infty$ 且 $p_1\ne p_2$。**

归一化 $\|u\|_p=1$。令

$$
c=\frac{p_2}{p_2-p},
\qquad T=(t/K_2)^c.
$$

若 $p_2>p$，把小幅值部分 $u_{\le T}$ 分给第二端点；若 $p_2<p$，把大幅值部分 $u_{>T}$ 分给第二端点。两种情况下都由第 4.5 节的幂次比较得到

$$
\|\text{第二端点部分}\|_{p_2}
\le T^{1-p/p_2},
$$

从而

$$
\|F(\text{第二端点部分})\|_\infty
\le K_2T^{1-p/p_2}=t.
$$

剩下的部分记为 $R_t$，交给 $(p_1,q_1)$。于是

$$
d_{F(u)}(2t)\le
K_1^{q_1}t^{-q_1}\|R_t\|_{p_1}^{q_1}.
$$

令 $r_1=q_1/p_1$。插值关系保证

$$
p_1+\frac{q-q_1}{c r_1}=p.
$$

不论 $c$ 正负，对于固定的 $|u(x)|>0$，该点出现在 $R_t$ 中的条件都对应于

$$
0<t<K_2|u(x)|^{1/c}
$$

（端点是否包含不影响 $t$ 积分）。因此 Minkowski 给出

$$
\begin{aligned}
&\left[
\int_0^\infty t^{q-q_1-1}
\|R_t\|_{p_1}^{q_1}\,dt
\right]^{1/r_1}\\
&\quad\le
\int_\Omega|u(x)|^{p_1}
\left(\int_0^{K_2|u(x)|^{1/c}}
t^{q-q_1-1}\,dt\right)^{1/r_1}dx\\
&\quad=
\left(\frac{K_2^{q-q_1}}{q-q_1}\right)^{1/r_1}
\int_\Omega|u|^p\,dx.
\end{aligned}
$$

故在归一化下

$$
\|F(u)\|_q^q
\le
\frac{2^q q}{q-q_1}
K_1^{q_1}K_2^{q-q_1}.
$$

齐次性再次给出一般 $u$ 的结论。

**若 $p_2=\infty$。**

取 $T=t/K_2$，把小幅值部分交给第二端点即可：

$$
\|F(u_{\le T})\|_\infty
\le K_2\|u_{\le T}\|_\infty\le t.
$$

上面的计算现在取 $c=1$。由 (I) 有 $q/p=q_1/p_1$，所以

$$
p_1+\frac{q-q_1}{q_1/p_1}=p.
$$

同样得到上述强型估计。

**若 $p_1=p_2=p<\infty$。**

不必分解 $u$。记 $A=\|u\|_p$，则

$$
d_{F(u)}(t)\le(K_1A/t)^{q_1},
\qquad
d_{F(u)}(t)=0\quad(t\ge K_2A).
$$

因此

$$
\begin{aligned}
\|F(u)\|_q^q
&\le q(K_1A)^{q_1}
\int_0^{K_2A}t^{q-q_1-1}\,dt\\
&=\frac{q}{q-q_1}
K_1^{q_1}K_2^{q-q_1}A^q.
\end{aligned}
$$

至此定理的所有指数情形均已覆盖。

### 5.6 对应教材第 55—57 页的证明

上面使用的是按集合切开的“硬截断”。教材使用的是“削顶截断”。两者都可以证明定理，但它们的分布函数公式不能混用。

对 $T>0$，教材定义

$$
u_{S,T}(x)=
\begin{cases}
u(x),&|u(x)|\le T,\\
T\,u(x)/|u(x)|,&|u(x)|>T,
\end{cases}
\qquad u_{B,T}=u-u_{S,T}.
$$

因此

$$
|u_{S,T}|=\min\{|u|,T\},
\qquad |u_{B,T}|=(|u|-T)_+.
$$

几何上，小部分是把超过高度 $T$ 的部分压到高度 $T$；大部分是削掉的剩余高度。二者一般在同一个点上都不为零。

**第一步：求分布函数。** 对 $s>0$，

$$
d_{u_{S,T}}(s)=
\begin{cases}
d_u(s),&s<T,\\
0,&s\ge T,
\end{cases}
\qquad
d_{u_{B,T}}(s)=d_u(s+T).
$$

第一式在 $s=T$ 时取零，是因为分布函数用的是严格超水平集 $\{|u|>s\}$。

**第二步：用层蛋糕公式求截断函数的范数。** 对 $1\le r<\infty$，

$$
\|u_{S,T}\|_r^r
=r\int_0^T s^{r-1}d_u(s)\,ds,
$$

$$
\begin{aligned}
\|u_{B,T}\|_r^r
&=r\int_0^\infty s^{r-1}d_u(s+T)\,ds\\
&=r\int_T^\infty(\tau-T)^{r-1}d_u(\tau)\,d\tau\\
&\le r\int_T^\infty\tau^{r-1}d_u(\tau)\,d\tau.
\end{aligned}
$$

这里最后一步使用 $r-1\ge0$。这些公式也直接说明：当 $p_1<p<p_2$ 时，小部分属于 $L^{p_2}$，大部分属于 $L^{p_1}$。

**第三步：先控制超水平集，再积分。**

次线性给出

$$
|F(u)|\le |F(u_{S,T})|+|F(u_{B,T})|.
$$

从而

$$
d_{F(u)}(2t)
\le d_{F(u_{S,T})}(t)+d_{F(u_{B,T})}(t).
$$

注意：一般不能写成

$$
|F(u)|\le |F(u_{S,T})+F(u_{B,T})|.
$$

后者只有在额外条件下才成立；一般次线性只控制两个绝对值的和。教材相应行应按超水平集包含关系来理解。

以下仍先考虑 $p_1<p_2$、$q_2<\infty$。取第 5.3 节中的 $c>0$，令 $T=t^c$。弱型估计产生

$$
\|F(u)\|_q^q
\le 2^q q
\left(
K_1^{q_1}p_1^{q_1/p_1}I_1+
K_2^{q_2}p_2^{q_2/p_2}I_2
\right),
$$

其中

$$
I_1=\int_0^\infty t^{q-q_1-1}
\left(\int_{t^c}^\infty
\tau^{p_1-1}d_u(\tau)\,d\tau\right)^{q_1/p_1}\,dt,
$$

$$
I_2=\int_0^\infty t^{q-q_2-1}
\left(\int_0^{t^c}
\tau^{p_2-1}d_u(\tau)\,d\tau\right)^{q_2/p_2}\,dt.
$$

**第四步：准确使用积分型 Minkowski 不等式。**

令 $r_2=q_2/p_2\ge1$。把外层积分看成带权测度
$t^{q-q_2-1}dt$ 下的 $L^{r_2}$ 范数，则

$$
\begin{aligned}
I_2^{1/r_2}
&\le
\int_0^\infty \tau^{p_2-1}d_u(\tau)
\left(\int_{\tau^{1/c}}^\infty
t^{q-q_2-1}\,dt\right)^{1/r_2}d\tau\\
&=(q_2-q)^{-1/r_2}
\int_0^\infty
\tau^{p_2-1+(q-q_2)/(cr_2)}
d_u(\tau)\,d\tau\\
&=(q_2-q)^{-1/r_2}
\int_0^\infty\tau^{p-1}d_u(\tau)\,d\tau.
\end{aligned}
$$

最后使用配平恒等式

$$
p_2+\frac{q-q_2}{cr_2}=p.
$$

所以正确的结果是

$$
\boxed{
I_2\le
\frac{1}{q_2-q}
\left(\frac{\|u\|_p^p}{p}\right)^{q_2/p_2}.
}
$$

同理，

$$
\boxed{
I_1\le
\frac{1}{q-q_1}
\left(\frac{\|u\|_p^p}{p}\right)^{q_1/p_1}.
}
$$

**常数核对。** 第 57 页把 $(q_2-q)^{-1}$ 放进了之后要取 $q_2/p_2$ 次方的括号中。这一步一般不成立。外层取幂前，正确因子应为 $(q_2-q)^{-p_2/q_2}$；取幂后才是 $(q_2-q)^{-1}$。$I_1$ 同理。

归一化 $\|u\|_p=1$ 后，一组正确的削顶截断证明常数是

$$
C^q=
2^q q\left[
\frac{K_1^{q_1}}{q-q_1}
\left(\frac{p_1}{p}\right)^{q_1/p_1}
+
\frac{K_2^{q_2}}{q_2-q}
\left(\frac{p_2}{p}\right)^{q_2/p_2}
\right].
$$

这里只需得到有限常数，不追求最优常数。硬截断与削顶截断得到不同的常数，不构成矛盾。

若 $p_1>p_2$，需要调换大小部分所对应的端点，并重新判断积分区域；若 $p_1=p_2$，不能使用含 $p_i-p$ 分母的 $c$，应使用第 5.4 节的直接分布函数估计。这些都不是可以省略的除零或符号问题。

### 5.7 为什么整个证明必须这样组织

可以把证明中的每个工具与它解决的问题一一对应：

| 遇到的问题 | 使用的工具 | 得到什么 |
|---|---|---|
| 中间空间中的 $u$ 未必同时属于两个端点空间 | 按幅值截断 | 两部分分别属于端点空间 |
| $F$ 可能不是线性的 | 次线性与超水平集包含 | 输出的尾部由两部分输出控制 |
| 端点只知道弱型估计 | 分布函数定义 | 将输出尾部换成输入截断范数 |
| 要证明强型，而非弱型 | 层蛋糕公式 | 对所有输出高度积分 |
| 出现嵌套积分及 $q_i/p_i$ 次幂 | 积分型 Minkowski | 交换“积分”与“范数”的顺序 |
| 最后必须还原 $\int|u|^p$ | 选 $T=t^c$ 并配平指数 | 内层积分恰好产生 $p$ 次幂 |
| 中间估计出现不齐次的范数幂次 | 先归一化，再用齐次性 | 恢复线性尺度的最终估计 |

条件 $p_i\le q_i$ 在这里的具体作用是保证 $q_i/p_i\ge1$，从而可以应用通常方向的 Minkowski 不等式。不能只记住定理结论而忽略这个条件。

## 6. 考试专题：把 2.58 拆成可独立完成的证明

Marcinkiewicz 插值定理为考试重点。

### 6.1 特例一：弱型 $(1,1)$ 与强型 $(\infty,\infty)$

**题目。** 设 $F$ 是定义在 $L^1+L^\infty$ 上的次线性算子，满足

$$
d_{F(f)}(t)\le \frac{K_1\|f\|_1}{t},
\qquad
\|F(g)\|_\infty\le K_\infty\|g\|_\infty.
$$

证明：对任意 $1<p<\infty$，存在 $C_p<\infty$，使

$$
\|F(u)\|_p\le C_p\|u\|_p.
$$

**完整证明。** 可取 $K_1,K_\infty>0$；若原常数为零，可先用更大的正数作为上界。

固定 $t>0$，取

$$
T=\frac{t}{2K_\infty},
\qquad
S=u\mathbf1_{\{|u|\le T\}},
\qquad
B=u\mathbf1_{\{|u|>T\}}.
$$

则 $S\in L^\infty$，且

$$
\|F(S)\|_\infty\le K_\infty T=\frac t2.
$$

另一方面，$u\in L^p$ 蕴含

$$
\|B\|_1
=\int_{\{|u|>T\}}|u|
\le T^{1-p}\|u\|_p^p<\infty.
$$

由次线性，若 $|F(u)|>t$，则 $|F(B)|>t/2$，所以

$$
d_{F(u)}(t)
\le\frac{2K_1}{t}
\int_{\{|u|>t/(2K_\infty)\}}|u(x)|\,dx.
$$

将其代入层蛋糕公式，并对非负函数使用 Tonelli 定理：

$$
\begin{aligned}
\|F(u)\|_p^p
&=p\int_0^\infty t^{p-1}d_{F(u)}(t)\,dt\\
&\le2pK_1\int_0^\infty t^{p-2}
\int_{\{|u|>t/(2K_\infty)\}}|u(x)|\,dx\,dt\\
&=2pK_1\int_\Omega |u(x)|
\int_0^{2K_\infty|u(x)|}t^{p-2}\,dt\,dx\\
&=\frac{2^pp}{p-1}
K_1K_\infty^{p-1}\|u\|_p^p.
\end{aligned}
$$

故可以取

$$
\boxed{
C_p=
2\left(\frac p{p-1}\right)^{1/p}
K_1^{1/p}K_\infty^{1-1/p}.
}
$$

**应当理解的三点。**

1. 小部分用 $L^\infty$ 端点，使它对高度 $t$ 的超水平集没有贡献。
2. 大部分用弱 $(1,1)$ 端点，得到可交换次序的尾积分。
3. $p>1$ 用在 $\int_0^a t^{p-2}dt<\infty$；证明不能延伸到 $p=1$。

这个特例中 $\theta=1-1/p$，插值所得输出指数也是 $p$。

### 6.2 特例二：两个有限的对角端点

**题目。** 设 $1\le a<p<b<\infty$，$F$ 次线性并同时满足弱型 $(a,a)$ 和 $(b,b)$ 估计：

$$
d_{F(f)}(t)\le K_a^a t^{-a}\|f\|_a^a,
\qquad
d_{F(g)}(t)\le K_b^b t^{-b}\|g\|_b^b.
$$

证明 $F$ 为强型 $(p,p)$。

**完整证明。** 固定 $t>0$，定义

$$
B_t=u\mathbf1_{\{|u|>t\}},
\qquad
S_t=u\mathbf1_{\{|u|\le t\}}.
$$

则

$$
\|B_t\|_a^a\le t^{a-p}\|u\|_p^p,
\qquad
\|S_t\|_b^b\le t^{b-p}\|u\|_p^p.
$$

因此可以分别应用两个端点估计，得到

$$
d_{F(u)}(2t)
\le K_a^at^{-a}\int_{\{|u|>t\}}|u|^a
+K_b^bt^{-b}\int_{\{|u|\le t\}}|u|^b.
$$

由层蛋糕公式，

$$
\|F(u)\|_p^p
=2^pp\int_0^\infty t^{p-1}d_{F(u)}(2t)\,dt.
$$

分别计算两个非负积分。第一项：

$$
\begin{aligned}
\int_0^\infty t^{p-a-1}
\int_{\{|u|>t\}}|u(x)|^a\,dx\,dt
&=\int_\Omega |u(x)|^a
\int_0^{|u(x)|}t^{p-a-1}\,dt\,dx\\
&=\frac{\|u\|_p^p}{p-a}.
\end{aligned}
$$

第二项：

$$
\begin{aligned}
\int_0^\infty t^{p-b-1}
\int_{\{|u|\le t\}}|u(x)|^b\,dx\,dt
&=\int_{\{|u|>0\}}|u(x)|^b
\int_{|u(x)|}^\infty t^{p-b-1}\,dt\,dx\\
&=\frac{\|u\|_p^p}{b-p}.
\end{aligned}
$$

零值点的被积函数恒为零，第二行将其去掉以避免形式上的 $0\cdot\infty$。

于是

$$
\boxed{
\|F(u)\|_p^p
\le2^pp\left(
\frac{K_a^a}{p-a}+
\frac{K_b^b}{b-p}
\right)\|u\|_p^p.
}
$$

**为什么这个版本更短？** 两个端点都是对角型，$q_i/p_i=1$，所以一般证明中的 Minkowski 步骤退化为直接交换非负积分；同时配平参数 $c=1$，可直接取 $T=t$。

### 6.3 一般有限指数版本：应当能补出的关键步骤

假设

$$
p_1<p<p_2<\infty,\qquad
q_1<q<q_2<\infty,\qquad p_i\le q_i,
$$

并且两组倒数指数按同一个 $\theta$ 插值。以下六个问题应当能脱离教材回答。

**问题一：为什么选 $T=t^c$？**

因为对大部分换序积分后产生

$$
|u|^{p_1+(q-q_1)/(c(q_1/p_1))}.
$$

为了使此幂次等于 $p$，必须选

$$
c=\frac{p_1(q-q_1)}{q_1(p-p_1)}.
$$

插值条件恰好保证小部分也得到同一个 $p$ 次幂。

**问题二：两个换序区域分别是什么？**

$$
|u(x)|>t^c
\iff 0<t<|u(x)|^{1/c},
$$

$$
|u(x)|\le t^c
\iff t\ge|u(x)|^{1/c}.
$$

这决定了一个积分从零开始，另一个积分延伸到无穷。

**问题三：为什么两个内层积分都收敛？**

$$
\int_0^A t^{q-q_1-1}dt
=\frac{A^{q-q_1}}{q-q_1}
$$

需要 $q>q_1$；

$$
\int_A^\infty t^{q-q_2-1}dt
=\frac{A^{q-q_2}}{q_2-q}
$$

需要 $q<q_2$。

**问题四：哪里使用了 $p_i\le q_i$？**

在以 $r_i=q_i/p_i$ 为指数的积分型 Minkowski 不等式中，需要 $r_i\ge1$。

**问题五：为什么先设 $\|u\|_p=1$？**

因为两个中间项通常分别含有
$\|u\|_p^{p q_1/p_1}$ 和 $\|u\|_p^{p q_2/p_2}$，不能直接都改成 $\|u\|_p^q$。归一化后先得到单位球上的统一估计，再利用 $F$ 的绝对齐次性恢复任意大小的 $u$。

**问题六：次线性究竟用于哪里？**

用于

$$
\{|F(u)|>2t\}
\subset
\{|F(B_t)|>t\}\cup\{|F(S_t)|>t\}.
$$

这一步不要求 $F(u)=F(B_t)+F(S_t)$。

**一个不应把 $T$ 误写成 $t$ 的例子。**

取

$$
(p_1,q_1)=(1,1),\qquad
(p_2,q_2)=(2,4),\qquad \theta=\frac12.
$$

则

$$
p=\frac43,\qquad q=\frac85,\qquad c=\frac95.
$$

此时正确的截断尺度是 $T=t^{9/5}$。核对：

$$
1+\frac{(8/5)-1}{(9/5)\cdot1}=\frac43,
\qquad
2+\frac{(8/5)-4}{(9/5)\cdot2}=\frac43.
$$

这说明 $c$ 的作用是精确配平输入与输出的不同指数。

## 7. 本节课的易错点与复习顺序

### 7.1 必须区分的概念

| 容易混淆的说法 | 正确理解 |
|---|---|
| 对每个 $v\in L^{p'}$ 能定义 $L_v$，所以 $(L^p)^*=L^{p'}$ | 前者只证明等距嵌入；还要证明每个连续线性泛函都能表示 |
| 两个泛函在一个单位向量上都取值 $1$，所以相等 | 一般空间中不成立；2.43 第二部分需要 $L^p$ 的几何性质 |
| $X^{**}$ 与 $X$ 抽象同构，所以 $X$ 自反 | 要检查自然嵌入 $J:X\to X^{**}$ 满射 |
| 弱 $L^p$ 就是 $L^p$ 上的弱拓扑 | 前者是尾部大小控制定义的函数空间，后者是一种收敛概念 |
| 混合范数可以按 Fubini 任意交换顺序 | 指数不同时一般不能得到等号，应使用置换不等式 |
| 两个弱型估计直接积分就得到强型 | 直接积分通常发散；需随输出高度改变截断阈值 |
| 分布函数恒等式只能在已知 $u\in L^p$ 时使用 | 对任意可测 $u$ 成立，允许两边同时为 $+\infty$ |
| $q_2=\infty$ 可直接代入有限指数公式 | 必须利用本质上界消去一个超水平集项 |
| 所有次线性算子都满足输出差的范数估计 | 本文只使用定义给出的绝对值次可加性；不能擅自添加更强性质 |

### 7.2 对公式的核对说明

1. **2.43：** 将教材“乘以合适常数，再加一个 $w$ 的倍数”补成了显式公式；将“不可能对所有 $t>0$ 成立”补成了除以 $t$ 后令 $t\downarrow0$ 的反证。
2. **2.45：** 在得到 $v\in L^\infty$ 后，还必须用稠密性或截断把表示公式从较小函数类推广到所有 $L^1$ 函数。
3. **2.55：** 准三角估计的最后一步通常是“不等号”，不是图片中所写的等号；若考虑 $0<p<1$，常数也需相应调整。
4. **2.56：** 齐次性一行的算子字母应统一为 $F$；不是另有一个算子 $T$。
5. **2.58：** 次线性控制绝对值的和，不能直接替换为输出之和的绝对值。
6. **2.58：** 第 57 页 Minkowski 计算后的常数幂次按第 5.6 节修正；定理结论不受影响。
7. **2.58：** 第 58 页最后一种情形的计算结果应当含 $\|u\|_p^q$，不是 $\|u\|_p^{q_1}$，因为代入上限 $K_2\|u\|_p$ 还会产生 $q-q_1$ 次幂。

### 7.3 分三遍复习

**第一遍：理清对象。** 能写出连续线性泛函、混合范数、分布函数、弱 $L^p$、强型与弱型的定义。特别区分配对 $\int uv$ 与 Hilbert 内积 $\int u\overline v$ 的约定。

**第二遍：独立完成短证明。** 依次完成 2.43 第二部分、混合范数比较作业、层蛋糕公式、弱 $(1,1)$ 与强 $(\infty,\infty)$ 的插值特例。

**第三遍：完成一般证明。** 能在纸上按“归一化—分解—超水平集—层蛋糕—端点估计—Minkowski—指数配平—恢复尺度”写出 2.58 的有限指数证明，并说明哪些步骤在端点或指数次序变化时必须改动。

### 7.4 教材编号与本讲义位置

| 教材编号 | 内容 | 本讲义位置 |
|---|---|---|
| 2.43 | 范数取得与支撑泛函唯一性 | 第 1 节；作业 1 |
| 2.44—2.45 | $L^p$ 与 $L^1$ 的对偶表示 | 第 2 节 |
| 2.46—2.47 | 自反性及 $L^\infty$ 对偶的区别 | 第 2 节 |
| 2.48—2.49 | 混合范数、混合 Hölder 不等式 | 第 3 节 |
| 2.50—2.52 | 混合范数置换及离散版本 | 第 3 节；作业 2 |
| 2.53—2.54 | 分布函数、Chebyshev、层蛋糕公式 | 第 4 节；作业 3 |
| 2.55—2.57 | 弱 $L^p$、算子类型、和空间 | 第 4 节 |
| 2.58 | Marcinkiewicz 插值定理及完整分情况证明 | 第 5 节 |
| 课堂考试标注 | 限制情形的证明训练、填空步骤、指数检查 | 第 6 节 |


