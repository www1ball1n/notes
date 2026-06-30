---
title: 物理学家用扩散模型 Chap. 0
published: 2026-06-30
description: ''
image: ''
tags: [Diffusion Model, Nonequilibrium]
category: 'Exploration'
draft: false 
lang: 'zh-CN'
---

> 为了看懂 Mizore 的东西做一些准备。因为好像我也可以搞搞大学习。

> 标题名字的来源是 侯伯元、侯伯宇著《物理学家用微分几何》，句读很明显**不是**物理学\/家用\/微分几何。

> 先从熟悉的东西开始，比如布朗运动和 Langevin 方程

# 1D 随机行走

我们从经典的随机行走开始，假设我从原点开始，以 $1/2$ 的概率向左或向右走 $l$ 的长度，那么在走了 $n$ 步以后，且 $n\rightarrow \infty $ 时，我处在 $xl,x\in \mathbb{Z}$ 的概率是什么？

这是一个伯努利分布，要走到 $xl$，那么就要走 $\frac{n+x}{2}$ 步向右和 $\frac{n-x}{2}$ 步向左。所以概率是

$$
P( X=n_{r} l) =\begin{pmatrix}
n\\
\tfrac{n-n_{r}}{2}
\end{pmatrix} \times \left(\frac{1}{2}\right)^{n}
$$

很容易得到：$E( X) =0,E\left( X^{2}\right) =nl^{2}$，我们对这个概率取$n\rightarrow \infty $极限，运用Stirling公式，再做小量展开，得到：

$$
P( X=n_{r} l) \approx \sqrt{\frac{2}{\pi n}}\exp\left( -\frac{n_{r}^{2}}{2n}\right)
$$

写成连续概率密度函数，则$p( x) \Delta x\approx P( n_{r})$，而$\Delta x=2l$，因此：

$$
p( x) =\sqrt{\frac{1}{2\pi nl^{2}}}\exp\left( -\frac{x^{2}}{2n}\right)
$$

假设每部需要耗费的时间是$\tau $，那么$n$步耗费的时间是$n\tau $，则

$$
E\left( X^{2}( t)\right) =\frac{nl^{2}}{n\tau } \cdot n\tau \equiv 2D\cdot ( n\tau )
$$

其中我们定义了扩散系数 $D=\frac{l^{2}}{2\tau }$。假设总共时间$n\tau =t$，则连续极限下，粒子处在$x=n_{r} l$的概率是

$$
p( x,t) =\sqrt{\frac{1}{4\pi Dt}}\exp\left( -\frac{x^{2}}{4Dt}\right)
$$

我们发现它满足扩散方程

$$
\frac{\partial p}{\partial t} =D\frac{\partial ^{2} p}{\partial x^{2}} ,p( x,0) =\delta ( x)
$$

这是一个一维 Brownian motion type 随机运动，我们发现他在长时间上类似于一种扩散，其结果是随时间变化的高斯分布，如果你有大量粒子的话。三维的话类似，此时，$\langle r^{2} \rangle =3\langle x^{2} \rangle =6Dt$。

# Langevin equation：第一个随机微分方程

我们尝试把这种噪声放在运动方程里面，加上耗散项，就得到 Langevin 方程：

$$
M\ddot{\mathbf{r}} =-\frac{1}{B}\dot{\mathbf{r}} +\mathbf{F}( t)
$$

其中$\mathbf{F}( t)$是一个随机驱动力，而第一项是一个耗散力，假设他满足：

$$
\langle \mathbf{F}( t) \rangle =0,\langle \mathbf{F}( t) \cdot \mathbf{r}( t) \rangle =0
$$

也就是时间平均为0，并且时间平均不做功。我们这里偷偷把时间平均换成系综平均，反正不严谨无所谓。

我们可以得到

$$
\langle \frac{\mathrm{d}\mathbf{v}}{\mathrm{d} t} \rangle =-\frac{1}{MB} \langle \mathbf{v} \rangle 
$$

也就是任何初始速度都会以$\tau =MB$的时间常数以指数形式$\mathrm{e}^{-t/\tau }$遗忘。

此外，我们看一下能量的变化

$$
\begin{align*}
\langle \mathbf{r} \cdot \frac{\mathrm{d}\mathbf{v}}{\mathrm{d} t} \rangle  & =-\langle \mathbf{r} \cdot \frac{\mathbf{v}}{\tau } \rangle +\frac{1}{M} \langle \mathbf{F} \cdot \mathbf{r} \rangle \\
 & =-\frac{1}{\tau } \langle \mathbf{r} \cdot \mathbf{v} \rangle 
\end{align*}
$$

左边恰好等于

$$
\langle \frac{\mathrm{d}}{\mathrm{d} t}(\mathbf{r} \cdot \mathbf{v}) \rangle =\frac{1}{2} \langle \frac{\mathrm{d}^{2}}{\mathrm{d} t^{2}}\left(\mathbf{r}^{2}\right) \rangle -\langle \mathbf{v}^{2} \rangle 
$$

因此：

$$
\langle \frac{\mathrm{d}^{2}}{\mathrm{d} t^{2}}\left(\mathbf{r}^{2}\right) \rangle +\frac{1}{\tau } \langle \frac{\mathrm{d}}{\mathrm{d} t}\left(\mathbf{r}^{2}\right) \rangle =2\langle \mathbf{v}^{2} \rangle 
$$

我们知道随机力下$\langle \mathbf{r}^{2} \rangle $有扩散行为，而$\langle \mathbf{v}^{2} \rangle $可以用气体的结果来近似，那么设

$$
\langle \mathbf{r}^{2} \rangle =3\langle r_{x}^{2} \rangle =6Dt,\langle \mathbf{v}^{2} \rangle =\frac{3k_{B} T}{M}
$$

那么用系综平均把时间导数拉出来，得到

$$
\frac{6D}{\tau } =\frac{6k_{B} T}{M} \Longrightarrow D=Bk_{B} T
$$

可以看到，耗散越小，或者温度越大，扩散越快。如果耗散$\frac{1}{B}$大了，就扩散不出去。

另外，通过定义力的关联函数

$$
K( t) =\frac{1}{M^{2}} \langle \mathbf{F}( t_{0}) \cdot \mathbf{F}( t_{0} +t) \rangle 
$$

可以得到涨落-耗散定理的一种表现。硬解这个方程，设$K( t) =\Gamma \delta ( t)$也就是没有记忆，发现最终达到平衡时：

$$
\Gamma =\frac{6k_{B} T}{M^{2} B}
$$

也就是说平衡态时随机力的激励作用刚好和耗散力要相互抵消掉，这是平衡态的要求。

:::important
通过这里我们建立了第一个随机微分方程，不过为了研究更加有意思的东西，我们来推一些数学。
:::