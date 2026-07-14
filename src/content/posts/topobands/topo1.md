---
title: Notes on Topological Band Theory 1
published: 2026-06-28
description: ''
image: ''
tags: [Basics, TopoPhysics, Theory]
category: 'Textbook Notes'
draft: false
lang: 'zh-CN'
---

> 最初发表于知乎
> https://zhuanlan.zhihu.com/p/2043930219019505956

# 1. 实用知识

## 1.1 固体物理结论

我们从一些固体物理的结论开始，首先静止晶格近似下 (取PBC)，周期势的 Hamiltonian 是

$$
H=\frac{\mathbf{p}^{2}}{2m} +V(\mathbf{r}) \\
$$

其本征态可由量子数$\mathbf{k}$标记，其$|\psi _{n\mathbf{k}} \rangle $满足

$$
\psi _{n\mathbf{k}}(\mathbf{r}) =\mathrm{e}^{i\mathbf{k} \cdot \mathbf{r}} u_{n\mathbf{k}}(\mathbf{r})
$$

其中$u_{n\mathbf{k}}(\mathbf{r})$是周期函数，且满足

$$
H_{\mathbf{k}} u_{nk}(\mathbf{r}) =\mathcal{E}_{n\mathbf{k}} u_{nk}(\mathbf{r})
$$

这里

$$
H_{\mathbf{k}} =\mathrm{e}^{i\mathbf{k} \cdot \mathbf{r}} H\mathrm{e}^{-i\mathbf{k} \cdot \mathbf{r}} =\frac{1}{2m}( -i\hbar \nabla +\hbar \mathbf{k})^{2} +V(\mathbf{r})
$$

给出一个关系

$$
\frac{\partial H_{\mathbf{k}}}{\partial \mathbf{k}} =\frac{\hbar }{m}( -i\hbar \nabla +\hbar \mathbf{k})
$$

并且

$$
\langle u_{n\mathbf{k}} |\frac{\partial H_{\mathbf{k}}}{\partial \mathbf{k}} |u_{n^{\prime }\mathbf{k}} \rangle =\langle \psi _{n\mathbf{k}} |\frac{\hbar }{m}( -i\hbar \nabla ) |\psi _{n^{\prime }\mathbf{k}} \rangle =\langle \psi _{n\mathbf{k}} |\mathbf{p} |\psi _{n^{\prime }\mathbf{k}} \rangle 
$$

我们可以用Hellman-Feynman计算这个矩阵元，由于

$$
\langle u_{n\mathbf{k}} |H_{\mathbf{k}} |u_{n^{\prime }\mathbf{k}} \rangle =\mathcal{E}_{n\mathbf{k}} \delta _{n,n^{\prime }}
$$

求导

$$
\frac{\partial }{\partial \mathbf{k}} \langle u_{n\mathbf{k}} |H_{\mathbf{k}} |u_{n^{\prime }\mathbf{k}} \rangle =\langle u_{n\mathbf{k}} |\frac{\partial H_{\mathbf{k}}}{\partial \mathbf{k}} |u_{n^{\prime }\mathbf{k}} \rangle +\mathcal{E}_{n\mathbf{k}} \langle \partial _{\mathbf{k}} u_{n\mathbf{k}} |u_{n^{\prime }\mathbf{k}} \rangle +\mathcal{E}_{n^{\prime }\mathbf{k}} \langle u_{n\mathbf{k}} |\partial _{\mathbf{k}} u_{n^{\prime }\mathbf{k}} \rangle 
$$

又由于分部积分

$$
\int \mathrm{d}^{3}\mathbf{r} \partial _{\mathbf{k}} u_{n\mathbf{k}}(\mathbf{r}) u_{n^{\prime }\mathbf{k}}(\mathbf{r}) =-\int \mathrm{d}^{3}\mathbf{r} u_{n\mathbf{k}}(\mathbf{r}) \partial _{\mathbf{k}} u_{n^{\prime }\mathbf{k}}(\mathbf{r})
$$

得到

$$
\langle u_{n\mathbf{k}} |\frac{\partial H_{\mathbf{k}}}{\partial \mathbf{k}} |u_{n^{\prime }\mathbf{k}} \rangle =\frac{\partial \mathcal{E}_{n\mathbf{k}}}{\partial \mathbf{k}} \delta _{n,n^{\prime }} -(\mathcal{E}_{n\mathbf{k}} -\mathcal{E}_{n^{\prime }\mathbf{k}}) \langle u_{n\mathbf{k}} |\partial _{\mathbf{k}} u_{n^{\prime }\mathbf{k}} \rangle 
$$

取$n=n^{\prime }$得到A&M中的有效质量定理一阶项。

## 1.2 Berry curvature

我们知道，如果一个本征态$|\psi _{n}(\mathbf{\theta }) \rangle $按一个参数 $\mathbf{\theta }$ 的路径$C$绝热演化回自身，也就是忽略跃迁，他会获得一个可观测的相位$\mathrm{e}^{i\gamma _{\mathbf{\theta }}}$，就是所谓Berry phase，可以写成 Berry connection 
$$
\mathcal{A}(\mathbf{\theta }) =i\langle \psi _{n}(\mathbf{\theta }) |\nabla _{\mathbf{\theta }} |\psi _{n}(\mathbf{\theta }) \rangle 
$$
在$C$上的环路积分
$$
\gamma _{C} =\oint _{C}\mathcal{A}_{n}(\mathbf{\theta }) \cdot \mathrm{d}\mathbf{\theta }
$$
注意$\mathcal{A}( \theta )$本身是gauge dependent的，取决于各种$|\psi (\mathbf{\theta }) \rangle $的相对相位，因为总是可以 redefine $|\psi ^{\prime }( \theta ) \rangle =\mathrm{e}^{i\alpha ( \theta )} |\psi ( \theta ) \rangle $.

如果可以找到一个gauge，使得$\mathcal{A}(\mathbf{\theta })$在以$C$为边的$S$上光滑单值无奇点，则可以用Stokes定理
$$
\gamma _{C} =\int _{S}\mathrm{d} \theta _{\mu }\mathrm{d} \theta _{\nu }( \partial _{\mu }\mathcal{A}_{\nu } -\partial _{\nu }\mathcal{A}_{\mu })
$$
这里出现了 Berry curvature $\Omega _{\mu \nu } =\partial _{\mu }\mathcal{A}_{\nu } -\partial _{\nu }\mathcal{A}_{\mu }$，同时也可直接表为
$$
\Omega _{\mu \nu } =i( \langle \partial _{\mu } \psi _{n} |\partial _{\nu } \psi _{n} \rangle -\langle \partial _{\nu } \psi _{n} |\partial _{\mu } \psi _{n} \rangle )
$$

从分部积分注意到，
$$
\langle \partial _{\mu } \psi _{n} |\psi _{n} \rangle \langle \psi _{n} |\partial _{\nu } \psi _{n} \rangle =\langle \psi _{n} |\partial _{\mu } \psi _{n} \rangle \langle \partial _{\nu } \psi _{n} |\psi _{n} \rangle 
$$
那么利用本征函数展开以后，
$$
\begin{align*}
\Omega _{\mu \nu } & =i\sum\limits _{m}( \langle \partial _{\mu } \psi _{n} |\psi _{m} \rangle \langle \psi _{m} |\partial _{\nu } \psi _{n} \rangle -( \mu \leftrightarrow \nu ))\\
 & =i\sum\limits _{m\neq n}( \langle \partial _{\mu } \psi _{n} |\psi _{m} \rangle \langle \psi _{m} |\partial _{\nu } \psi _{n} \rangle -( \mu \leftrightarrow \nu ))
\end{align*}
$$
再利用FH公式带入$\langle \psi _{m} |\partial _{\nu } \psi _{n} \rangle $得到
$$
\Omega _{\mu \nu } =i\sum\limits _{m\neq n}\left(\frac{\langle \psi _{n} |\partial _{\mu } H|\psi _{m} \rangle \langle \psi _{m} |\partial _{\nu } H|\psi _{n} \rangle }{(\mathcal{E}_{n} -\mathcal{E}_{m})^{2}} -( \mu \leftrightarrow \nu )\right)
$$
从这个形式可以说明 Berry curvature 是规范不变的。

Berry curvature 描述了不同波函数之间的某种距离，当然只是虚部，他可以视为所谓 quantum geometry tensor
$$
Q_{\mu \nu } =\langle \partial _{\mu } \psi _{n} |1-P_{n} |\partial _{\nu } \psi _{n} \rangle 
$$
的虚部，确实描述了在参数空间上的面积元大小。不过此处我们不涉及更高阶的QG动力学，点到为止。


对于能带电子，我们选取$|u_{n\mathbf{k}} \rangle $在一个晶胞里的变化，比起$|\psi _{n\mathbf{k}} \rangle $，他消去了平面波因子而专注于一个cell内的演化，方便讨论。Berry phase 定义为
$$
\mathcal{A}_{n}(\mathbf{k}) =i\langle \psi _{n\mathbf{k}} |\nabla _{\mathbf{k}} |\psi _{n\mathbf{k}} \rangle 
$$
而 Berry curvature 直接用叉乘定义：
$$
\Omega _{n}(\mathbf{k}) =\nabla \times \mathcal{A}_{n}(\mathbf{k})
$$
在半经典近似下，2D情形，$\Omega _{n}(\mathbf{k})$作为所谓依赖于$\mathbf{k}$的磁场来影响波包运动，总的来说是让$\mathbf{k}$转圈（但并非像匀强磁场一样统一地转圈），我们知道$\mathbf{k}$转圈同时$\mathbf{r}$也转圈，从而在实空间得到反常霍尔效应。对于充满的能带，需要对$\Omega _{n}(\mathbf{k})$积分，而$\Omega _{n}(\mathbf{k})$的积分是量子化的。我们可以证明
$$
\sigma _{xy} =-\frac{e^{2}}{\hbar }\int _{\mathbf{k}} \Omega (\mathbf{k}) =-\frac{e^{2}}{h} C
$$

量子描述也是可行的。对于一条充满的能带，加入$x$方向电场以后$\dot{\mathbf{k}} =-\frac{e}{\hbar }\mathbf{E}$，从而$\mathbf{k}$开始变化，当一个$\mathbf{k}$走完一圈以后，他会积累一个Berry phase。注意：如果$\mathcal{A}_{n}(\mathbf{k})$在路径上不解析，则需要取分片规范或者规定补丁相位。我们之后需要用到 Kubo formula （线性响应理论）来看出$\sigma _{xy}$的关系，单单在这里思考只不过是在零阶里打转。

:::important
一句话概括这里在说什么。一个基态在缓慢的演化下，只要有能隙，就还是基态。但是在这个过程中会积累 Berry phase，在回到原来时，这个 Berry phase 是规范不变的从而可以观测。对于绝缘体的能带电子来说，给不是太强的电场，那么价带的电子不会跑到导带上，也就是不会击穿，从而保持绝缘。但同时电子积累的 Berry phase 直接给出量子化的电导。
:::

## Example: 二能级系统的 Berry phase

考虑磁场中的自旋，或任何一个二能级系统
$$
H=-\gamma _{B}\mathbf{n} \cdot \mathbf{\sigma }
$$
其基态为
$$
\begin{pmatrix}
\cos\frac{\theta }{2}\\
\sin\frac{\theta }{2}\mathrm{e}^{i\phi }
\end{pmatrix} \ \text{or} \ \begin{pmatrix}
\cos\frac{\theta }{2}\mathrm{e}^{-i\phi }\\
\sin\frac{\theta }{2}
\end{pmatrix} \ 
$$
分别会在南极和北极出现奇点问题，所以我们打两个补丁去计算。北半球
$$
\mathcal{A}_{\theta } =0,\mathcal{A}_{\phi } =\sin^{2}\frac{\theta }{2}
$$
南半球
$$
\mathcal{A}_{\theta } =0,\mathcal{A}_{\phi } =\cos^{2}\frac{\theta }{2}
$$
得到整个球面的Berry curvature积分是$-2\pi $，是量子化的，Chern number 为1，且在三维空间的表述中类似于一个点电荷的场。

对于二能带系统，$\mathcal{H}(\mathbf{k}) =d(\mathbf{k}) \cdot \sigma $，不过是把上面的东西重新参数化一下，且可以通过$d(\mathbf{k})$在球面上覆盖的面积来计算其 Chern number。对于单个 Dirac point，则可以看 $d(\mathbf{k})$ 是怎么转的。假设一个 Dirac point 的有效 Hamiltonian 是
$$
\mathcal{H}(\mathbf{q}) =q_{x} \sigma _{x} +q_{y} \sigma _{y}
$$
那么 $d(\mathbf{q}) =( q_{x} ,q_{y})$，$\mathbf{q}$ 逆时针走一圈的时候，$d(\mathbf{k})$ 也逆时针走一圈，给出 $1/2$ 的 Chern number。对于另一种 $d(\mathbf{q}) =( -q_{x} ,q_{y})$，是反过来的，给出负的 Chern number。我们说他有相反的 chirality。

## Berry curvature 积分的量子化

我们来证明二维能带 Chern number 的量子化，我们需要计算
$$
\int _{\mathbf{k}} \Omega _{n}(\mathbf{k}) =\int \frac{\mathrm{d}^{2}\mathbf{k}}{( 2\pi )^{2}} \Omega _{n}(\mathbf{k})
$$
对于 nonzero Chern number, Berry connection 必须要打补丁，我们假设有两个区域$U_{N} ,U_{S}$，其connection分别为 $\mathcal{A}_{N} ,\mathcal{A}_{S}$，他们给出相同的curvature，所以类似于磁场的 vector potential，他们之间差一个任意函数的梯度
$$
\mathcal{A}_{N}(\mathbf{k}) =\mathcal{A}_{S}(\mathbf{k}) +\nabla \phi (\mathbf{k})
$$
这个任意函数就是经过交界区域之后要打的一个补丁相位。我们把总的积分写成
$$
\int _{U_{N}}\frac{\mathrm{d}^{2}\mathbf{k}}{( 2\pi )^{2}} \Omega _{n}(\mathbf{k}) +\int _{U_{S}}\frac{\mathrm{d}^{2}\mathbf{k}}{( 2\pi )^{2}} \Omega _{n}(\mathbf{k})
$$
分别做格林定理得到
$$
\begin{align*}
 & \int _{U_{N}}\frac{\mathrm{d}^{2}\mathbf{k}}{( 2\pi )^{2}} \Omega _{n}(\mathbf{k}) +\int _{U_{S}}\frac{\mathrm{d}^{2}\mathbf{k}}{( 2\pi )^{2}} \Omega _{n}(\mathbf{k})\\
= & \frac{1}{( 2\pi )^{2}}\left(\int _{\partial U_{N}}\mathrm{d}\mathbf{k} \cdot \mathcal{A}_{N}(\mathbf{k}) +\int _{\partial U_{S}}\mathrm{d}\mathbf{k} \cdot \mathcal{A}_{S}(\mathbf{k})\right)\\
= & \frac{1}{( 2\pi )^{2}}\int _{\partial U_{N}}\mathrm{d}\mathbf{k} \cdot (\mathcal{A}_{N}(\mathbf{k}) -\mathcal{A}_{S}(\mathbf{k}))\\
= & \frac{1}{( 2\pi )^{2}}\int _{\partial U_{N}}\mathrm{d}\mathbf{k} \cdot \nabla \phi (\mathbf{k})\\
= & \frac{1}{( 2\pi )^{2}} \cdot 2\pi C
\end{align*}
$$
由于$\phi $是个相位，起点回到终点的积分必定为$2\pi C$，否则变多值函数了，其中$C$是整数。对于其他维数的情况可以用类似的微分形式语言证明。这里我们可以看到 Chern number 像是一种 winding number，是在数经过一个闭合路径以后 Berry connection 转了几圈。