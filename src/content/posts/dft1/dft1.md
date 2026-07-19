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

## Lieb 的构造

# 原子单位制

# Kohn-Sham theory

K-S theory 实际上把 DFT map 到一个单电子方程上面，从而可以使用各种单电子计算的技术，比如各种基的选取、pseudopotential 等等。我们来看他是怎么做的。
