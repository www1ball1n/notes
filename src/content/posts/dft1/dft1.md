---
title: 密度泛函理论 (DFT) 的基础 I
published: 2026-07-19
description: ''
image: ''
tags: [Basics, DFT, Theory]
category: 'Learning Notes'
draft: false 
lang: ''
---

# 电子的量子多体理论摘要

> 本笔记混淆一二次量子化，定义遵循 2024 年基于某本讲 Keldysh 的书。

我们回到已经看了无数次比亲妈还熟悉的 $N$ 电子 Schrödinger 方程：
$$
H\Psi (\mathbf{r}_{1} ,\dotsc ,\mathbf{r}_{N}) =E\Psi (\mathbf{r}_{1} ,\dotsc ,\mathbf{r}_{N})
$$
其中：
$$
H=\hat{T} +V_{ee} +\sum\limits _{i=1}^{N} v_{\text{ext}}(\mathbf{r}_{i})
$$
各项分别是：
$$
\begin{aligned}
\hat{T} & =-\sum\limits _{i=1}^{N}\frac{\hbar ^{2}}{2m} \nabla _{i}^{2}\\
V_{ee} & =\frac{e^{2}}{4\pi \epsilon _{0}}\frac{1}{2}\sum\limits _{i\neq j}\frac{1}{| \mathbf{r}_{i} -\mathbf{r}_{j}| }\\
v_{\text{ext}}(\mathbf{r}_{i}) & =-\frac{e^{2}}{4\pi \epsilon _{0}}\sum\limits _{A}\frac{Z_{A}}{| \mathbf{r}_{i} -\mathbf{R}_{A}| }
\end{aligned}
$$
多体波函数的问题是其巨大的维数，假设我们把空间分成 $L^{3}$ 个格点，则一个多体波函数的信息需要的存储空间$\varpropto L^{3N}$。相比而言，我们知道其实单粒子密度矩阵 1PDM 本身就包含了我们需要的很多信息，定义：
$$
\Gamma _{1}(\mathbf{y} ;\mathbf{x}) =\frac{1}{( N-1) !}\int \mathrm{d}\mathbf{r}_{1} \cdots \mathrm{d}\mathbf{r}_{N-1} \Psi ^{*}(\mathbf{x} ,\mathbf{r}_{1} ,\cdots ,\mathbf{r}_{N-1}) \Psi (\mathbf{y} ,\mathbf{r}_{1} ,\cdots ,\mathbf{r}_{N-1})
$$
或者用二次量子化来写：
$$
\Gamma _{1}(\mathbf{y} ;\mathbf{x}) =\langle \Psi |\psi ^{\dagger }(\mathbf{x}) \psi (\mathbf{y}) |\Psi \rangle 
$$
其对角元 $\Gamma _{1}(\mathbf{r} ;\mathbf{r}) =\langle \Psi |\psi ^{\dagger }(\mathbf{r}) \psi (\mathbf{r}) |\Psi \rangle =n(\mathbf{r})$ 就是电子密度。任何单粒子算符的期望值都可以用这个 1PDM 来求：
$$
\langle \Psi |\sum\limits _{i} h_{i} |\Psi \rangle =\int \mathrm{d}\mathbf{x}\mathrm{d}\mathbf{y} \langle \mathbf{x} |\hat{h} |\mathbf{y} \rangle \Gamma _{1}(\mathbf{y} ;\mathbf{x})
$$
比如说 $\sum\nolimits _{i=1}^{N} v_{\text{ext}}(\mathbf{r}_{i})$，由于在位置表象下是 diagonal，直接就是：
$$
\langle V_{\text{ext}} \rangle =\int v_{\text{ext}}(\mathbf{r}) n(\mathbf{r})\mathrm{d}^{3}\mathbf{r}
$$
DFT 就是使用 $n(\mathbf{r})$ 的理论，其中 $\mathbf{r}$ 的维数大大减小，只需要 $L^{3}$ 的空间。并且由 Hohenberg-Kohn theorems 我们知道 $n(\mathbf{r})$ 已经包括了大量信息。在此之前我们做一个简单的计算，就是 Slater determinent 或者 free Hamiltonian 的电子密度，假设
$$
|\Psi \rangle =|\chi _{1} ,\cdots ,\chi _{N} \rangle 
$$
其波函数为 Slater determinent：
$$
\langle \mathbf{r}_{1} ,\cdots ,\mathbf{r}_{N} |\chi _{1} ,\cdots \chi _{N} \rangle =\begin{vmatrix}
\chi _{1}(\mathbf{r}_{1}) & \cdots  & \chi _{1}(\mathbf{r}_{N})\\
\vdots  & \ddots  & \vdots \\
\chi _{N}(\mathbf{r}_{1}) & \cdots  & \chi _{N}(\mathbf{r}_{N})
\end{vmatrix}
$$
因为我们定义：
$$
|\chi _{1} ,\cdots \chi _{N} \rangle =\frac{1}{\sqrt{N!}}\sum\limits _{P}( -1)^{P} |\chi _{P( 1)} \rangle \cdots |\chi _{P( N)} \rangle 
$$
并且 $|\mathbf{r}_{1} \cdots \mathbf{r}_{N} \rangle $ 也这么定义，求波函数的时候有一个 $N!$ 正好消掉，注意其他文献可能并不这么定义。求电子密度的时候，直接二次量子化：
$$
\begin{aligned}
n(\mathbf{r}) & =\langle \chi _{1} \cdots \chi _{N} |\psi ^{\dagger }(\mathbf{r}) \psi (\mathbf{r}) |\chi _{1} \cdots \chi _{N} \rangle \\
 & =\sum\limits _{i=1}^{N}| \chi _{i}(\mathbf{r})| ^{2}
\end{aligned}
$$
就得到了很简单的结果。

# Hohenberg-Kohn theorems

H-K 定理是 DFT 的基础了，我们再来回顾一下，不证明，这个证明用反证法一下就出来了。但是我们需要讨论清楚一些情况。

首先，假设基态 $|\Psi _{0} \rangle $ is non-degenerate。那么，每一个外势的等价类 $\{v_{\text{ext}}(\mathbf{r}) +C\}$ 都有其一一对应的 $n_{0}(\mathbf{r})$ 和一一对应的 $|\Psi _{0} \rangle $。那么：存在一个 functional $|\Psi [ n] \rangle $，使得代入某个基态的电子密度 $n_{0}(\mathbf{r})$ 后，$|\Psi [ n_{0}] \rangle $ 是相应的基态波函数。
$$
n_{0}(\mathbf{r}) =\langle \Psi [ n_{0}] |\hat{n}(\mathbf{r}) |\Psi [ n_{0}] \rangle 
$$
并且这个 functional 是普适的，适用于一切电子体系。之后，所有算符的期待值也是基态电子密度 $n(\mathbf{r})$ 的泛函，尤其是总能量
$$
E[ n] =F[ n] +\int \mathrm{d}^{3}\mathbf{r} v_{\text{ext}}(\mathbf{r}) n(\mathbf{r})
$$
其中 $F[ n]$ 是一个普适的泛函。并且由于变分法，对给定的 $v_{\text{ext}}(\mathbf{r})$ 也就是给定了一个问题，其基态电子密度最小化这个总能量泛函。
$$
E_{0} =\underset{n\in \mathscr{N}}{\min} E[ n]
$$
注意 $n(\mathbf{r})$ 的范围必须从所有合法 potential 求出来的基态密度的集合 $\mathscr{N}$ 当中取，不能随便乱取。

这里就有几个变化：假设基态有简并，那么一个 $v_{\text{ext}}(\mathbf{r})$ 只能和他的基态空间，以及对应的电子密度的集合有一一对应。不过总能量关于 $n$ 的泛函依旧存在，并且所有基态的 $n$ 都最小化这个泛函 $E[ n]$。

加上磁场，对于非均匀的磁场，需要考虑 $( n(\mathbf{r}) ,\mathbf{m}(\mathbf{r}))$ 四个量而非一个。对于均匀磁场，$( n(\mathbf{r}) ,m_{z}(\mathbf{r}))$ 就足够，或者等价地 $n_{\uparrow }(\mathbf{r}) ,n_{\downarrow }(\mathbf{r})$。如果没有磁场，还是可以使用 $n_{\uparrow }(\mathbf{r}) ,n_{\downarrow }(\mathbf{r})$ 来最小化能量，因为这两个量本质上还是 $n(\mathbf{r})$ 的泛函，只不过在表达某些能量泛函的时候这样的取法比较方便。

有个 $v$-representability problem，也就是如何确保我们最小化时取到的 $n$ 真的在这个 $\mathscr{N}$ 里面？如何刻画这个 $\mathscr{N}$？这就要看 Lieb 的做法了，但我们之后再补充。

# 原子单位制

原子单位制很简单，我们定义：
$$
\frac{1}{2} \ \text{Hartree} =1\ \text{Ry} =13.6\ \text{eV} =\frac{e^{2}}{8\pi \epsilon _{0} a_{0}} =\frac{\hbar ^{2}}{2m_{e} a_{0}^{2}}
$$
那么三项分别变成：
$$
\begin{aligned}
\hat{T} & =-\frac{E_{\text{Hartree}}}{2}\sum\limits _{i=1}^{N}( a_{0} \nabla _{i})^{2}\\
V_{ee} & =E_{\text{Hartree}}\sum\limits _{i< j}\frac{1}{| \mathbf{r}_{i} -\mathbf{r}_{j}| /a_{0}}\\
v_{\text{ext}}(\mathbf{r}_{i}) & =-E_{\text{Hartree}}\sum\limits _{A}\frac{Z_{A}}{| \mathbf{r}_{i} -\mathbf{R}_{A}| /a_{0}}
\end{aligned}
$$
因此如果把距离用 $a_{0}$ 做单位，能量用 Hartree 做单位，那么：
$$
\hat{H}_{e} =-\frac{1}{2}\sum\limits _{i} \nabla _{i}^{2} +\sum\limits _{i,j}^{i< j}\frac{1}{r_{ij}} -\sum\limits _{iA}\frac{Z_{A}}{r_{iA}}
$$
得到简化，要恢复一般单位的话，就分别对距离和能量乘上 $a_{0}$ 和 Hartree 就可以了。

之后 KS 的推导我们使用原子单位制，可以少写一些东西。

# Kohn-Sham theory

K-S theory 实际上把 DFT map 到一个单电子方程上面，从而可以使用各种单电子计算的技术，比如各种基的选取、pseudopotential 等等。我们来看他是怎么做的。

K-S theory 的基础假设是：存在一个单粒子外势 $v_{s}(\mathbf{r})$ ，使得其对应单粒子 Hamiltonian 的基态，也就是一个 Slater determinant 态 $|\phi _{1} ,\cdots ,\phi _{N} \rangle $，其得到的 $n(\mathbf{r})$ 和我们需要求的基态 $|\Psi \rangle $ 相同。于是给定一个 $n(\mathbf{r})$ ，这个 determinant $\{\phi _{i}\}$ 可以定义为使得动能项最小的任意一组 $\{\phi _{i}\}$，可能不唯一。
$$
\{\phi _{i}\} \in \underset{\{\phi _{i}\}\rightarrow n}{\text{argmin}} \ \left\{-\frac{1}{2}\sum\limits _{i}\int \mathrm{d}\mathbf{r}\left( \phi _{i}^{*} \nabla ^{2} \phi _{i}\right)\right\}
$$
再定义 $T_{s}[ n]$ 为这个动能项的最小值：
$$
T_{s}[ n] =\underset{\{\phi _{i}\}\rightarrow n}{\text{min}} \ \left\{-\frac{1}{2}\sum\limits _{i}\int \mathrm{d}\mathbf{r}\left( \phi _{i}^{*} \nabla ^{2} \phi _{i}\right)\right\}
$$
再定义 exchange-correlation functional $E_{xc}[ n]$ 为：
$$
E_{xc}[ n] =F[ n] -T_{s}[ n] -E_{\text{H}}[ n]
$$
其中 Hartree term
$$
E_{\text{H}}[ n] =\frac{1}{2}\int \mathrm{d}\mathbf{r}\mathrm{d}\mathbf{r}^{\prime }\frac{n(\mathbf{r}) n\left(\mathbf{r}^{\prime }\right)}{\left| \mathbf{r} -\mathbf{r}^{\prime }\right| }
$$
这个 functional 基本上包含了电子的关联还有动能的差异部分。整个能量泛函 $E[ n]$ 写成：
$$
E[ n] =T_{s}[ n] +E_{xc}[ n] +E_{\text{H}}[ n] +\int n(\mathbf{r}) v_{\text{ext}}(\mathbf{r})\mathrm{d}\mathbf{r}
$$

由于我们上面有一个假设，在这个假设成立的情况下，我们在所有的 non-interacting $v$-representable $n(\mathbf{r})$ 里变分，也可以期望得到正确的基态电子密度 $n_{0}(\mathbf{r})$。又根据定义可以转化为在 $\{\phi _{i}\}$ 当中变分，因为取两次最小值等价于取一次最小值。这样，我们就把对基态电子密度的变分转换成对 auxilliary non-interacting fermion state 的变分，后面用简单的变分法，在各轨道正交归一的情况下，得出 Kohn-Sham 方程：
$$
\left[ -\frac{1}{2} \nabla ^{2} +v_{\text{ext}}(\mathbf{r}) +v_{\text{H}}(\mathbf{r}) +v_{xc}(\mathbf{r})\right] \phi _{i}(\mathbf{r}) =\sum\limits _{j} \epsilon _{ij} \phi _{j}(\mathbf{r})
$$
那么注意这个 $\phi _{j}$ 构造出的 1PDM $\tilde{\Gamma }_{1}\left(\mathbf{r}^{\prime } ;\mathbf{r}\right)$ 和真实基态的 1PDM 只有对角元是相同的，非对角元可以完全不同。这个 Hermitian 矩阵 $\epsilon _{ij}$ 可以被一个幺正变换对角化，而电子密度是保持的，最后得到变换后的 orbitals 的标准 KS equation
$$
\left[ -\frac{1}{2} \nabla ^{2} +v_{\text{ext}}(\mathbf{r}) +v_{\text{H}}(\mathbf{r}) +v_{xc}(\mathbf{r})\right] \phi _{i}(\mathbf{r}) =\epsilon _{i} \phi _{i}(\mathbf{r})
$$
但是此处没有 Koopsman 定理，也就是 $\epsilon _{i}$ 不完全等同于准粒子能量。这其中只有 $v_{xc}(\mathbf{r})$ 是我们不知道的，其拟设就是所谓 Jacob's ladder 所说的，从 LDA 开始有一大堆经验上的东西。

# LDA and beyond

我们大致列出一些和 $E_{xc}$ 相关的拟设，一般会区分交换和关联。最常用的有 LDA：
$$
E_{\text{LDA}} =\int \mathrm{d}\mathbf{r} \ f( n(\mathbf{r}))
$$
以及 GGA
$$
E_{\text{GGA}} =\int \mathrm{d}\mathbf{r} \ f( n(\mathbf{r}) ,\nabla n(\mathbf{r}))
$$
其中最著名的是 PBE 泛函，其交换能。
$$
E_{\text{PBE}}^{x} =-\int n^{4/3} \cdot \frac{3}{4}\left(\frac{3}{\pi }\right)^{1/3}\left( 1+\frac{\mu s^{2}}{1+\mu s^{2} /\kappa }\right)\mathrm{d}\mathbf{r}
$$
那么第一项是均匀电子气的交换，通过均匀电子气就可以算出来。LDA 的关联部分一般来自于电子气的 Monte Carlo。括号内第二项是 GGA 修正，这里的 $s$ 定义为
$$
s=\frac{1}{2k_{F}}\frac{| \nabla n| }{n} ,k_{F} =\left( 3\pi ^{2} n\right)^{1/3}
$$
是一个无量纲的梯度。一般在 $n$ 变化时 PBE 的交换关联比 LDA 要大。关联能则有其他修正。

HF 泛函：
$$
E_{\text{HF}}^{x} =-\frac{1}{2}\sum\limits _{ij\sigma }\int \mathrm{d}\mathbf{r}\mathrm{d}\mathbf{r}^{\prime } \ \frac{\phi _{i\sigma }^{*}(\mathbf{r}) \phi _{j\sigma }^{*}(\mathbf{r}) \phi _{j\sigma }\left(\mathbf{r}^{\prime }\right) \phi _{i\sigma }\left(\mathbf{r}^{\prime }\right)}{\left| \mathbf{r} -\mathbf{r}^{\prime }\right| }
$$
还有杂化泛函，比如 B3LYP
$$
E_{\text{B3LYP}} =0.2E_{\text{HF}}^{x} +0.8E_{\text{LDA}}^{x} +0.72\Delta E_{\text{B88}}^{x} +0.81E_{\text{LYP}}^{c} +0.19E_{\text{VWN}}^{c}
$$