---
title: 冷原子物理 笔记 Chap. 1
published: 2026-08-10
description: ''
image: ''
tags: []
category: 'Learning Note'
draft: false 
lang: ''
---

# 1. Electronic Structure

我们先从单个原子的电子结构入手。原子中有一个 separation of energy scales，使得我们能分别处理不同的相互作用。

## Coulomb, fine structure and hyperfine structure

先来看 eV 量级的电子 Coulomb interaction。

单电子在 $\frac{1}{r}$ potential 当中是一个 $\mathrm{SO(4)}$ 对称性，量子数是 $n,\ell ,m$，而能量只和 $n$ 有关。

电子的 screening 把这个对称性破到 $\mathrm{SO(3)}$，不考虑 SOC 的话，$\mathrm{SO(3)}$ 的量子数由 $\ell $ 表示，不同的 $( n,\ell )$ 能量造成分裂。经典图像来看，electronic states with identical $n$ and larger $\ell $ stay farther away from the nucleus. 这就造成 2s 2p 的 splitting。

另一件事，如果两个电子分别在 $\psi _{1} ,\psi _{2}$ 上，那么他的 triplet state 的空间部分波函数是反对称的，这导致两个电子不会出现在同一个地方，从而减小 Coulomb repulsion。在原子当中，这个能量很大，因此推广开来有最大 $S$ 的 Hund's first rule。2nd rule 也来自于 Coulomb 排斥，越大的 $L$ 有利于电子在角方向上错开。

接下来考虑 SOC，他的量级是 meV，约合 $10^{11}$ Hz，一个 eV 大概是 $10^{14}$ Hz。SOC 源自于相对论效应，每个电子都能感受到核绕他旋转 (orbital) 导致的一个有效磁场，产生的类似于 Zeeman effect 这样的东西，因此有
$$
H_{\text{SO}} =\sum\limits _{i} \alpha _{f}^{i}\hat{s}_{i} \cdot \hat{\ell }_{i}
$$
做一个近似，由于 Hund's first rule 更强，所以我们把他近似成
$$
\alpha _{f}\mathbf{L} \cdot \mathbf{S} +( \cdots )
$$
叫他 L-S coupling，在这一项下，$L,S$ 重新变成好量子数，而 $J$ 一直都是 $\mathrm{SO(3)}$ 的好量子数，一个电子态于是可以用 $^{2S+1} L_{J}$ 来表示，这里有 Hund's third rule: 对于小于半充满，$\alpha _{f}  >0$，和单个电子的情况一致，因此取最小的 $J$，大于半充满反之 (particle-hole 变换之后和小于半充满的情况一致，但是轨道角动量会反号，可以这么理解)

:::note
这里注意，一般性的 SOC 来自 Dirac 方程当中得到的 $( \sigma \times p) \cdot \nabla V$ 这种东西，所以在固体当中，他的形式会不一样，$\nabla V$ 对于导带电子可能来自自发电极化，表面或者是外加电场。
:::

最后再次要的效应就是 hyperfine structure 也就是电子和核的 coupling，energy scale is approximately $10^{-6}$ eV。我们在 $J$ 的基础上写出
$$
H_{hf} \simeq \alpha _{hf} \ \mathbf{I} \cdot \mathbf{J}
$$
那么 $L,S,J,I,F,m_{f}$ 是一套新的好量子数。不过原则上 $\mathbf{I}$ interacts differently with orbital and spin, but we just neglect it because the effect is too weak, and this is usually enough.

## Lande projection theorem, g factor

在继续前进之前，我们先来回顾一下 Lande projection theorem。任意一个 rank-1 tensor operator 在 $|Jm_{j} \rangle $ 这个 $( 2J+1)$ manifold 当中的投影都可以这么求：
$$
P_{J}\mathbf{V} P_{J} =C\mathbf{J}
$$
其中 $C$ 这个常数是 dot product 求出来的
$$
C=\frac{\langle \mathbf{J} \cdot \mathbf{V} \rangle }{\mathbf{J}^{2}} =\frac{\langle \mathbf{J} \cdot \mathbf{V} \rangle }{J( J+1)}
$$
因为在 $J$ manifold 当中，所以角动量平方是个数。这可以由 Wigner-Eckart 定理得到：
$$
\langle JM^{\prime } |V_{q} |JM\rangle =\frac{\langle J||V_{q} ||J\rangle }{\sqrt{2J+1}} C_{JM,1q}^{JM^{\prime }}
$$
那么他就正比于同样的 rank-1 tensor operator $\mathbf{J}$，二者成正比，因为前面的矩阵元只和 $J$ 有关，C-G 系数都是一样的。我们之前推导 Stevens operator 也是同样的路数。

因此，对于 $\mathbf{L}$ 和 $\mathbf{S}$，分别有
$$
\begin{aligned}
\langle \mathbf{L} \cdot \mathbf{J} \rangle  & =\frac{1}{2} \langle \mathbf{J}^{2} +\mathbf{L}^{2} -\mathbf{S}^{2} \rangle =\frac{1}{2}( J( J+1) +L( L+1) -S( S+1))\\
\langle \mathbf{S} \cdot \mathbf{J} \rangle  & =\frac{1}{2} \langle \mathbf{J}^{2} -\mathbf{L}^{2} +\mathbf{S}^{2} \rangle =\frac{1}{2}( J( J+1) -L( L+1) +S( S+1))
\end{aligned}
$$
磁矩 $\mathbf{\mu } =-\mu _{B}(\mathbf{L} +2\mathbf{S})$ 在 $|J\rangle $ 的投影就是
$$
\mathbf{\mu } =-\mu _{B}\mathbf{J}\frac{\langle \mathbf{J} \cdot \mathbf{L} \rangle +2\langle \mathbf{J} \cdot \mathbf{S} \rangle }{J( J+1)} =-g_{J} \mu _{B} J
$$
这个系数就是 Lande $g$-factor
$$
g_{J} =1+\frac{1}{2}\frac{J( J+1) -L( L+1) +S( S+1)}{J( J+1)}
$$
之后我们会用到这个结果。

## Electronic Structure of Selected Atoms

接下来我们需要讨论常见的三类原子的光谱。

第一类是碱金属，其电子组态是 $ns^{1}$，因此可以知道三个量子数 $L=0,S=1/2,J=1/2$，记为 $^{2} S_{1/2}$。第一激发态是 $np^{1}$，因此 $L=1,S=1/2$，对应的 $J$ 有两种可能，$J=3/2$ 或者 $J=1/2$，而 $J=3/2$ 的能量高一些。分别记为 $^{2} P_{1/2} ,^{2} P_{3/2}$。历史上，Na 的 $^{1} S\rightarrow ^{2} P$ 的双线分别称为 $D_{1} ,D_{2}$ 线。如果考虑超精细结构的话，比如 $^{87}\text{Rb}$，其核自旋为 $I=3/2$，不考虑 hyperfine splitting，简并度就是 $( 2J+1)( 2I+1) =8$。

:::note
**核物理小课堂**

核模型最简单的是 shell model，可以解释很多东西，原子核内的吸引 potential 可以当成一个带修正的三维谐振子模型来看待，然后在此之上有能级分裂，并且更大的角动量能量更低。并且，核的 nuclear potential 非常陡，因此 SOC 也是 MeV 量级的，综合考虑之后，有这样的 shell model
$$
1s_{1/2}< 1p_{3/2} < 1p_{1/2} < 1d_{5/2} < 2p_{3/2} < 1f_{5/2} < \cdots 
$$
靠这套东西可以解释很多 magic number，还有核的角动量。质子和中子分别填充各自的 shell model，而且他们喜欢填同一个轨道然后 singlet pairing，因为是 strong interaction 导致的吸引。

alkali metal 的质子数是奇数，而且没有什么稳定的 odd-odd 核 (只有 5 种稳定的 odd-odd 核，由于 pairing 很强，even-even 比相同质量数的 odd-odd 稳定很多，一般 odd-odd 都会 $\beta $ 衰变掉。)，所以我们只考虑 odd-even 核，其核自旋由 shell model 里面成单的 particle 或者 hole 决定。偶数个质子或者中子直接两两成对 singlet，从而在核自旋中不起作用。 $^{87}\text{Rb}$ 核自旋为 $I=3/2$，按照 shell model，50 个中子两两配对填满，37 个 proton 其中除了一个 $2p_{3/2}$ 其他都是填满的。和能查到的 shell model diagram 不一样的是，对于 Rb 来说是填 $2p_{3/2}$ 比 $1f_{5/2}$ 能量更低。
:::

第二类是 alkali earth，基态是两个电子配对 $1s^{2}$，$S=0$，记为 $^{1} S_{0}$。激发态为 $ns^{1} np^{1}$，因为 Hund's rule，singlet 态 $^{1} P_{1}$ 能量比较高。而 triplet 态 $S=1$ 分成三条线：$L=1,S=1$ 因此可以有 $J=0,1,2$。对于 even-even 核，$I=0$ 所以没有 hyperfine，对于 even-odd 核，有核自旋从而会有 hyperfine coupling。

![alt text](fig1.png)

各个态的寿命是不一样的，高能级的态会通过自发辐射跳到低能级的态，这源自于原子和电磁波，尤其是电场的相互作用，一阶项是所谓的偶极跃迁，也就是看 $-e\langle f|\mathbf{r} |i\rangle $ 这个矩阵元谁到谁的跃迁是对称性所允许的。

对于 $ ^{1} P_{1} \rightarrow {^{1}S}_{0}$，他的 $\Delta J=1,$ 同时 parity 变了，符合跃迁条件，所以寿命很短，大概在 ns 级别。而 triplet 态 $S=1$，光子不改变 $S$，因此跃迁能级就弱很多。但是考虑 SOC 的其他项之后，$S$ 不再是好量子数，但 $J$ 仍然是，也就是说 triplet 能级中，$J=1$ 的态会混入 $S=0$ 的成分，导致跃迁也是可能的，其寿命大约是 100 ns。

对于其他两个 $J=0,2$ 的态，只有 hyperfine 才会使得他们和 $J=1$ 的态耦合，其寿命大概在 s 的量级，因此可以用来做光钟。记得我们的原子钟是用的 hyperfine 能级之间的跃迁，用的光是在微波的波段，而这里是在用可见光波段。对于 even-even 核，$I=0$，所以 $\mathbf{I} \cdot \mathbf{J}$ 的 hyperfine 就没有，此时两个 $J=0,2$ 的寿命特别长。 

第三种原子是磁性原子，比如说一些稀土，过渡金属。他们一般会有没充满的 $d$ 或 $f$ shell，导致他的 $J$ 会很大，这有几个后果：
- 如果磁化了，他们的电子云是各向异性的，因此 spin-spin interaction 会是各向异性的
- 电子云的 anisotropy 会导致他的 vdW interaction 也是 anisotropic 的
- 磁矩没有极化时，他像一个 $\mathrm{SU(N)}$ model。