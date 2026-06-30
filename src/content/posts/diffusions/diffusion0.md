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

# Diffusion Model：第二个随机微分方程

> 我发现我可以直接看懂，所以我们直接来吧！

## Diffusion model 的假设, 训练

我们考虑这样一个动力学过程，把一组抽象化的数据 $X^{\mu }$ 不断地加噪声，直到他成为纯噪声，对于每一步，都设定一个参数 $\tilde{\alpha }_{i} ,\tilde{\sigma }_{i}$ 并且抽取一个噪声 $\tilde{\epsilon }_{i}$，则有一个线性关系d

$$
X_{t+1}^{\mu } =\tilde{\alpha }_{t} X_{t}^{\mu } +\tilde{\sigma }_{t}\tilde{\epsilon }_{t}^{\mu }
$$

由于线性，两步以后仍然保持这个形式：

$$
\begin{align*}
X_{i+2}^{\mu } & =\tilde{\alpha }_{i+1} X_{i+1}^{\mu } +\tilde{\sigma }_{i+1}\tilde{\epsilon }_{i+1}^{\mu }\\
 & =\tilde{\alpha }_{i+1}\tilde{\alpha }_{i} X_{i}^{\mu } +\left(\tilde{\alpha }_{t+1}\tilde{\sigma }_{i}\tilde{\epsilon }_{i}^{\mu } +\tilde{\sigma }_{i+1}\tilde{\epsilon }_{i+1}^{\mu }\right)
\end{align*}
$$

由于$\tilde{\epsilon }_{i}^{\mu } ,\tilde{\epsilon }_{i+1}^{\mu }$都是 Gaussian random variable，其线性组合也是 Gaussian vairable，因此更一般的我们可以写出通项公式

$$
X_{t}^{\mu } =\alpha _{t} X_{0}^{\mu } +\sigma _{t} \epsilon ^{\mu }
$$

假设一个基本上是纯噪声的 $X_{t}^{\mu }$ 可以从目标数据 $X_{0}^{\mu }$ 和一个给定的高斯随机噪声 $\epsilon^{\mu }$ 通过参数为$\{\alpha _{t} ,\sigma _{t}\}$ 演化到 $t$ 来得到。注意这里的参数 $\{\alpha _{t} ,\sigma _{t}\}$ 是已知的，并非待训练参数，不同的选取称为不同的 noise schedule。于是可以使用参数为 $\theta $ 的神经网络进行估计：

$$
\hat{X}_{0}^{\mu } =f_{X}\left( X_{t}^{\mu } ;\{\alpha _{t} ,\sigma _{t}\} ,t;\text{other conditions} ;\theta \right)
$$

或者等价地拟合目标噪声

$$
\hat{\epsilon }^{\mu } =f_{\epsilon }\left( X_{t}^{\mu } ,\{\alpha _{t} ,\sigma _{t}\} ,t;\text{other conditions} ;\theta \right)
$$

我们需要做的就是通过训练数据得到这组参数 $\theta $。最简单的选取是 rectify flow：

$$
X_{t}^{\mu } =( 1-t) X_{0}^{\mu } +t \epsilon ^{\mu }
$$

我们看到实际上$\alpha _{t} ,\sigma _{t}$往往取成连续函数，这就可以定义速度：

$$
\frac{\mathrm{d} X^{\mu }}{\mathrm{d} t} =v^{\mu } =\dot{\alpha }( t) X_{0}^{\mu } +\dot{\sigma }( t) \epsilon ^{\mu }
$$

估计速度也是可行的，再把$\hat{X}^{\mu }$反解出来就可以了。在 rectify flow 的情况下：

$$
v^{\mu } =\epsilon ^{\mu } -X_{0}^{\mu }
$$

也就是做一个匀速直线运动。

Loss function 直接用所谓 $\ell ^{2}$，因为学到的是所有可能的 $X_{0}^{\mu }$ 的条件期望值，而这是我们需要的。

## 生成

现在我们来生成目标数据，也就是反解，首先对正向过程求导

$$
\dot{X}_{t}^{\mu } =\dot{\alpha }( t) X_{0}^{\mu } +\dot{\sigma }( t) \epsilon ^{\mu }
$$

那么

$$
\epsilon ^{\mu } =\frac{\dot{X}_{t}^{\mu } -\dot{\alpha }( t) X_{0}^{\mu }}{\dot{\sigma }( t)}
$$

代回正向过程消掉噪声项，

$$
X_{t}^{\mu } =\alpha _{t} X_{0}^{\mu } +\sigma _{t}\frac{\dot{X}_{t}^{\mu } -\dot{\alpha }_{t} X_{0}^{\mu }}{\dot{\sigma }_{t}}
$$

整理得到（扔掉一堆符号）

$$
\sigma \dot{X} =\dot{\sigma } X+(\dot{\alpha } \sigma -\alpha \dot{\sigma }) X_{0}
$$

让我们想到除法求导公式，两边除以$\sigma ^{2}$，得到

$$
\frac{\mathrm{d}}{\mathrm{d} t}\left(\frac{X}{\sigma }\right) =\frac{\mathrm{d}}{\mathrm{d} t}\left(\frac{\alpha }{\sigma }\right) X_{0}
$$

设$\lambda _{t} =\ln( \alpha _{t} /\sigma _{t})$，再把$X_{0}$用我们的估计代替

$$
\frac{\mathrm{d}}{\mathrm{d} t}\left(\frac{X_{t}}{\sigma _{t}}\right) =\mathrm{e}^{\lambda }\frac{\mathrm{d} \lambda }{\mathrm{d} t}\hat{X}_{0}( X_{t} ,t;\theta )
$$

注意$t$和$\lambda $由于是单调的一一对应，所以两边积分得到

$$
\frac{X_{t_{2}}}{\sigma _{t_{2}}} -\frac{X_{t_{1}}}{\sigma _{t_{1}}} =\int _{\lambda _{1}}^{\lambda _{2}}\mathrm{d} \lambda \mathrm{e}^{\lambda }\hat{X}_{0}( X( t( \lambda )) ,t( \lambda ) ;\theta )
$$

Euler 法数值解一下，假设$\hat{X}_{0}$是由$t_{1}$处的$X( \lambda _{1})$拟合的，那么把他拉出去得到

$$
\frac{X_{t_{2}}}{\sigma _{t_{2}}} -\frac{X_{t_{1}}}{\sigma _{t_{1}}} \approx \left(\frac{\alpha _{t_{2}}}{\sigma _{t_{2}}} -\frac{\alpha _{t_{1}}}{\sigma _{t_{1}}}\right)\hat{X}_{0}( X( t_{1}) ,t_{1} ;\theta )
$$

解出：

$$
X_{t_{2}} \approx \alpha _{t_{2}}\hat{X}_{0}( X( t_{1}) ,t_{1} ;\theta ) +\sigma _{t_{2}} \times \frac{1}{\sigma _{t_{1}}}( X_{t_{1}} -\alpha _{t_{1}}\hat{X}_{0}( X( t_{1}) ,t_{1} ;\theta ))
$$

也就是

$$
X_{t_{2}} \approx \alpha _{t_{2}}\hat{X}_{0}( X( t_{1}) ,t_{1} ;\theta ) +\sigma _{t_{2}}\hat{\epsilon }( X( t_{1}) ,t_{1} ;\theta )
$$

这里我们让 $t_{2} < t_{1}$，也即不断逼近 $t=0$，这样在每个时间点先用NN预测，然后带进上面这个式子求解即可，尤其是取直线更加简单。
