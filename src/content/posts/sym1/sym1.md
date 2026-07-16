---
title: Inversion Symmetry and misc.
published: 2026-07-15
description: ''
image: ''
tags: [Basics, Theory]
category: 'Learning Notes'
draft: false 
lang: 'zh-CN'
---

# Symmetry
我们来集中考虑一下空间反演对称性和时间反演对称性的效果，以及他们破缺之后会产生什么样的结构。和时间反演（一般是一个外磁场或者自发磁化）不同，空间反演在普通的教材里面并没有过多的涉及，不过他还是对应于很多非常简洁的物理现象。由于 inversion 是一个幺正对称性，属于晶体点群的对称性的一种，我们把它放在一个正常对称性的框架中去考虑。

我们先来定义什么是对称性。在我们的语境中，暂时先不考虑磁性带来的影响，也就是只考虑使得不带磁化的晶体结构不变的群，我们称为空间群 $G$，$G$ 中的操作称为 $R$。而 $R$ 操作的对象是各个原子的位置矢量 $\mathbf{r}_{i} \in \mathbb{R}^{3}$，所以 $R\in \mathbb{R}^{3\times 3}$。

什么是群呢？简单的来说，连续做两个 $G$ 中的操作，其效果都可以等同于 $G$ 中另一个操作。并且一定有一个什么都不做，并且每个操作都有逆，并且简单写个结合律，我们就完成了群的定义。

:::important
不严格、跳步、trying to be kirakira dokidoki 是本博客特色。虽然还没有做到闪闪发光心动不已，但是在此之前，请首先成为非人类。
:::

我们现在把他拉到 Hamiltonian 里面，对 Hamiltonian 的操作的集合我们暂且称为 $\{U_{R} :R\in G\}$，可以证明，$U_{R}$ 是 $R$ 诱导的一个群，且基本为 $R$ 的同态。如果不考虑自旋，则往往是一个同构。

我们先具体来看一下 $U_{R}$ 是什么。算符 $U_{R}$ 对一个波函数的作用以后，变换到的新波函数可以表示为
$$
\psi (\mathbf{r})\rightarrow U_{R} \psi (\mathbf{r}) =D( R) \psi \left( R^{-1}\mathbf{r}\right)
$$
这个式子表明：变换后的波函数在新坐标 $\mathbf{r}$ 的值等于原来坐标 $R^{-1}\mathbf{r}$ 的值，并且还会改变其中的内部自由度，比如自旋或者轨道。

举个例子，绕 $z$ 轴转 $2\pi $：
$$
\psi ^{\prime }(\mathbf{r}) =D_{1/2}( R_{z}) \psi \left( R_{z}^{-1}\mathbf{r}\right)
$$
其中：
$$
D_{1/2}( R_{z}) =\begin{pmatrix}
\mathrm{e}^{-i\pi } & 0\\
0 & \mathrm{e}^{i\pi }
\end{pmatrix}
$$
那么：
$$
\psi ^{\prime }( x,y,z) =-\psi ( -x,-y,z)
$$

同样的变换作用到 $p$ 轨道上，作用效果则是截然不同的。新的 $p$ 轨道是旧的三个 $p$ 轨道的混合，并且不会有其他的轨道混入。具体到这里，是这样的（我们把具体推导放在后面）
$$
\begin{pmatrix}
p_{x}(\mathbf{r})\\
p_{y}(\mathbf{r})\\
p_{z}(\mathbf{r})
\end{pmatrix}\rightarrow \begin{pmatrix}
\cos \theta  & -\sin \theta  & 0\\
\sin \theta  & \cos \theta  & 0\\
0 & 0 & 1
\end{pmatrix}\begin{pmatrix}
p_{x}\left( R^{-1}\mathbf{r}\right)\\
p_{y}\left( R^{-1}\mathbf{r}\right)\\
p_{z}\left( R^{-1}\mathbf{r}\right)
\end{pmatrix}
$$
我们发现，如果只考虑绕着 $z$ 轴转动，$p_{z}$ 自己跟自己玩；$p_{x} ,p_{y}$ 则是互相混，而且不会有其他成分混入。如果考虑所有的其他转动，则三个 $p$ 轨道是互相混但是不会有其他的混入。而 $s$ 轨道则是自己跟自己混。

如果在 $p$ 轨道基础上考虑自旋呢？我们就要变六个函数，这六个函数在一般的旋转下都会混在一起，但是不会有其他的混入。

做个总结，如果一个函数空间在某个操作群 $D( G)$ 下互相混，但是不会有其他的混入，我们称这个空间是这个群 $D( G)$ 的表示，由于往往 $G$ 和 $D( G)$ 同构，也可以不严格地称为 $G$ 的表示。

表示可以约化，也就是这个互相混可能是一群函数混在一起，其他一群混在一起，还有一些各玩各的，这时候可以把他们的空间拉出来写成 direct sum $V_{1} \oplus V_{2}$，因为他们不是互相影响的。约化到不能再约化就称为不可约表示。比如这个 $z$ 旋转群，$p_{z}$ 就是一个一维不可约表示，$\{p_{x} ,p_{y}\}$ 是一个二维不可约表示。维数就遵循向量空间的定义了。

同样的变换可以拉到产生湮灭算符上面，遵循态 / 波函数的变换。

我们现在知道什么是操作和群了，现在来看什么是普通的对称。普通的对称，其核心就是
$$
D( R) HD^{-1}( R) =H
$$
注意这里是对大 Hamiltonian 做的！如果是二次量子化，带产生湮灭算符！里面的**尚未对角化的**东西 $\mathcal{H}(\mathbf{k})$ 变的就是千奇百怪了。这个 $D( R)$ 就是作用在波函数上的算符。

一个核心的定理就是：$H$ 的所有本征态必构成 $D( R)$ 的表示，约化以后，同一不可约表示里的本征态能量必相同。不同的一般不同可能有偶然简并。因为同一不可约表示里的东西，假设有一个 $\psi _{1}$，要考虑另一个 $\psi _{2}$，把 $\psi _{2}$ 转一下就变成 $\psi _{1}$ 了而 Hamiltonian 没变过，所以能量是简并的。

我们进一步简化，只考虑有限群，晶体的话取个 PBC。有限群的表示就那么几种，而且都可以搞成幺正表示，所以那些 $D( R)$ 全是幺正的（很容易理解因为他不能凭空变东西出来）。表示可以用特征标表去 label，特征标表有两个正交定理。所以我们解出来的东西每个都能 label，或者我们知道其中一个东西可以去通过特征标表计算得到他属于什么表示或者是分裂成什么表示。但是那个能量的顺序没办法通过群论直接得到。

当然这些只是一个概述，而且群论我也忘记太多了，我们还是上具体例子。

于是群论主要分成两条线：第一个是研究空间群的结构，第二个是研究各种量怎么变化，我们先看后者，从最简单的 inversion symmetry 开始。

# Inversion, or centrosymmetry
我们考虑这个晶体对称群：
$$
G=\{1,i\}
$$
其中反演操作
$$
i=\begin{pmatrix}
-1 & 0 & 0\\
0 & -1 & 0\\
0 & 0 & -1
\end{pmatrix}
$$
这不是一个 proper rotation。我们来看看他对各个东西的作用，对于波函数，假设自旋守恒或者分离：
$$
D( i) \psi _{n\mathbf{k}}(\mathbf{r}) :=\hat{P} \psi _{n\mathbf{k}}(\mathbf{r}) =\psi _{n\mathbf{k}}( -\mathbf{r})
$$
那么由 Bloch 定理：
$$
\psi _{n\mathbf{k}}( -\mathbf{r}) =u_{n\mathbf{k}}( -\mathbf{r})\mathrm{e}^{+i\mathbf{k} \cdot \mathbf{r}}
$$
所以实际上得到了一个 $-\mathbf{k}$ 的态，按照不严格的语言写，可以称为 $\mathbf{k}\xrightarrow{i} -\mathbf{k}$。但问题是我们并不知道这个 $-\mathbf{k}$ 是由那些态组成的，如果没有简并，则就是 $\psi _{n,-\mathbf{k}}(\mathbf{r})$ 同一条能带。但如果有简并，反演以后可能得到多个能带的组合，也就是
$$
\hat{P} \psi _{n\mathbf{k}}(\mathbf{r}) =\sum\limits _{m} B_{mn}(\mathbf{k}) \psi _{m,-\mathbf{k}}(\mathbf{r})
$$
这个 $B_{mn}$ 称为 sewing matrix。但是反演不会跑到非简并的 $-\mathbf{k}$ 态上，由于相同表示基本就等同于相同能量（暂时不讨论偶然简并，因为我们始终假设微扰的存在）可以得到
$$
B_{mn}(\mathbf{k}) =\langle \psi _{m,-\mathbf{k}} |\hat{P} |\psi _{n,\mathbf{k}} \rangle 
$$
可以得到 $B_{mn}( -\mathbf{k}) =( B_{nm}(\mathbf{k}))^{*}$。这个类似的东西对于时间反演对称性也有，并且在 TRIM point 的 TR sewing matrix 可以用来求 $\mathbb{Z}_{2}$ topological invariant。注意在 IIM point 时，波函数为 parity 的本征态。

破坏了自旋旋转对称性，则还是有 $E_{n}(\mathbf{k}) =E_{n}( -\mathbf{k})$，只不过 $n$ 是 spin-orbit labeled band index 了，inversion 并不操作自旋。

如果同时有 time reversal symmetry，则
$$
PT:\mathbf{k} ,\mathbf{S}\rightarrow \mathbf{k} ,-\mathbf{S}
$$
因此对于每个点 $E_{\mathbf{k} \uparrow } =E_{\mathbf{k} \downarrow }$，不需要 spin rotation symmetry 也能保证这点。

我们再来看对于产生湮灭算符的操作，和态是一样的。
$$
Pc_{n\mathbf{k}}^{\dagger } P^{-1} =\sum\limits _{m} B_{mn}(\mathbf{k}) c_{m,-\mathbf{k}}^{\dagger }
$$
对于轨道则需要加上轨道的变换，比如说石墨烯：
$$
Pc_{A\mathbf{k}}^{\dagger } P^{-1} =c_{B,-\mathbf{k}}^{\dagger }
$$
那么，$\left\{c_{A\mathbf{k}}^{\dagger } ,c_{B\mathbf{k}}^{\dagger }\right\}$ 是一组基，表现为
$$
P\Psi _{\mathbf{k}} P^{-1} =P\begin{pmatrix}
c_{A\mathbf{k}}\\
c_{B\mathbf{k}}
\end{pmatrix} P^{-1} =\begin{pmatrix}
c_{B-\mathbf{k}}\\
c_{A-\mathbf{k}}
\end{pmatrix} =\tau _{x} \Psi _{-\mathbf{k}}
$$
所以表现为 $\tau _{x}$，不过定义方式依赖于基相位规范和位置（其实也是规范）的选取。对于 NN graphene Hamiltonian，假如他是 inversion invariant 的，则应该有
$$
PHP^{-1} =H
$$
作用到 $\mathcal{H}(\mathbf{k})$ 上则有
$$
\tau _{x}\mathcal{H}(\mathbf{k}) \tau _{x} =\mathcal{H}( -\mathbf{k})
$$
我们发现的确满足。之前我们推过了 Kagome，我们来看一下 Kagome 会发生什么，先从位置的产生湮灭算符开始，定义反演中心为六边形的中心：
$$
\begin{align*}
c_{\mathbf{R} A}^{\dagger } & \rightarrow c_{-\mathbf{R} -\mathbf{a}_{1} ,A}^{\dagger }\\
c_{\mathbf{R} B}^{\dagger } & \rightarrow c_{-\mathbf{R} -\mathbf{a}_{2} ,B}^{\dagger }\\
c_{\mathbf{R} C}^{\dagger } & \rightarrow c_{-\mathbf{R} +\mathbf{a}_{1} -\mathbf{a}_{2} ,C}^{\dagger }
\end{align*}
$$
代入之前的定义
$$
c_{A\mathbf{k}}^{\dagger } =\frac{1}{\sqrt{N}}\sum\limits _{\mathbf{R}}\mathrm{e}^{i\mathbf{k} \cdot (\mathbf{R} +\mathbf{r}_{A})} c_{\mathbf{R} A}^{\dagger }
$$
得到：
$$
c_{A\mathbf{k}}^{\dagger }\rightarrow \frac{1}{\sqrt{N}}\sum\limits _{\mathbf{R}}\mathrm{e}^{i( -\mathbf{k}) \cdot (\mathbf{R} +\mathbf{r}_{A})} c_{\mathbf{R} ,A}^{\dagger } =c_{-A\mathbf{k}}^{\dagger }
$$
其他两个类似，因此我们得到
$$
P\Psi _{\mathbf{k}} P^{-1} =\Psi _{\mathbf{k}}
$$
由此我们也看到这个变换的形式依赖于相位的选取。如果 $c_{\mathbf{k}}$ 选取的规范不一样，比如不把 $\mathbf{r}_i$ 放到相位里面去，那么最后得到的矩阵就是不一样的，并非单位矩阵，而是一个三个相位的对角矩阵。

推导这些的时候，最安全的做法当然是从 position space 开始。


# Lack of inversion symmetry: Dresselhaus or Rashba SOC

我们来看一下 lack of inversion symmetry 的结果。如果在结构上就缺少 inversion symmetry，比如说一个表面，那么有可能会有一个电场（参见功函数有关），我们记为 $E\hat{z}$，或者是外加电场。

> 顺带一提，缺乏空间反演对称性可能造成一个自发的电场，也就是铁电，往往有压电效应。（不严谨）

考虑自旋轨道耦合，其作用一般是劈裂自旋的简并：
$$
E_{\pm }(\mathbf{k}) =E_{0}(\mathbf{k}) \pm | b(\mathbf{k})| 
$$
可以看成是随动量变化的有效磁场，不过如果 TRS 还在，仍会有 Kramers pair，也就是一个 $\mathbf{k}$ 和另一个 $-\mathbf{k}$ 的能量一样，但是具体的能带编号我们是不知道的；而在 TRIM 点则是保证二重简并。

说回来，表面的一个电场可能造成如下的 Rashba term：
$$
H_{R} =\alpha _{R}(\mathbf{\sigma } \times \mathbf{k}) \cdot \hat{z} =\alpha _{R}( \sigma _{x} k_{y} -\sigma _{y} k_{x})
$$
这是最简单的形式，并且是 TR 不变的。此时，有效磁场是垂直于动量的，导致手性自旋纹理。我们看有效磁场
$$
b_{R}(\mathbf{k}) \varpropto \alpha _{R}(\hat{z} \times \mathbf{k})
$$
那么 $\alpha _{R}$ 的两种符号就代表了两种旋转方向, e.g. chirality。算出的能量则是有一个和 $\mathbf{k}$ 有关的偏移
$$
E_{\pm }(\mathbf{k}) =E_{0}(\mathbf{k}) \pm \alpha _{R}| \mathbf{k}| 
$$
这个用简并微扰法可以很简单地求出，我们在这里画个图。

![alt text](image1.png)

> Dirac fermion 的话，就是 Kane-Mele model 了，这里还要区分 intrinsic 和 exrinsic，而 Rashba 是 extrinsic。关于 Kane-Mele model，之后再讲，在目前的这个路线下只能算是支线。

另外一种是晶体本身缺乏 inversion symmetry，称为 Dresselhaus SOC。二维情况常写成
$$
H_{D} =\beta ( \sigma _{x} k_{x} -\sigma _{y} k_{y})
$$
有效磁场是 $\beta ( k_{x} ,-k_{y})$，他的自旋方向由晶轴决定。除此之外还有立方项
$$
H_{D}^{( 3)} \varpropto +\beta d^{2} k_{x} k_{y}( \sigma _{x} k_{y} -\sigma _{y} k_{x})
$$
bulk 则可以写成
$$
H_{D} \varpropto p_{x} \sigma _{x}\left( p_{y}^{2} -p_{z}^{2}\right) +\text{other 2 rotation of } xyz
$$

> 这个具体怎么推好像又是一个新坑。

# DM Interaction


# Time reversal symmetry








