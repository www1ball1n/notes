---
title: Anomolous Hall 的典中典理论，SOC，和有关材料
published: 2026-07-17
description: ''
image: ''
tags: [Basics, TopoPhysics, Theory]
category: 'Learning Notes'
draft: false 
lang: ''
---

# AHE 现象和三种机制
所谓 AHE 当然要从实验上定义，也就是在没有外磁场下，加 $x$ 方向电场有 $y$ 方向电流这个事情。经验上对 AHE 材料，$\rho _{xy}$ 正比于磁化强度 $M$。
$$
\rho _{xy} =R_{0} B+R_{s} M
$$
并且 $R_{s} \gg R_{0}$。在远古 (<1930) 经常作为 smoking gun of FM order，比 dichorism 和 Kerr / Faraday effect 要看的更清楚。

理论上，Luttinger 给出一个无耗散的 intrinsic 机制，现在我们知道就是由于能带的 Berry curvature 导致的，并且要 spin-splitted，这个 intrinsic 和 scattering 没有关系。还有 Smit 提出的 skew scattering 机制，也就是自旋依赖的散射；以及 Berger 提出的 side-jump，也就是自旋依赖的速度拐弯，which is subtle in its concepts。两种 extrinsic 的机制，都可以考虑为自旋劈裂的能带电子在 potential 中运动的结果。三种机制都是存在的，他们有什么特点呢？

![alt text](mechs.png)

Intrinsic 的贡献我们发现就是能带 Berry curvature 的积分，这是 Kubo formula 推出来的，并且成功解释了 Chern insulator 的量子化现象。从而有一个 scaling 关系
$$
\rho _{xy} \varpropto \rho _{xx}^{2}
$$
这个关系在之前的文章中推过了，本质上是由于电阻率张量是电导率张量的逆，从而分母上出现了 $\rho _{xx}^{2}$，也就是：
$$
\sigma _{xy} =\frac{\rho _{xy}}{\rho _{xy}^{2} +\rho _{xx}^{2}} \Longrightarrow \rho _{xy} \approx \sigma _{xy}^{\text{intr}} \rho _{xx}^{2} \varpropto \rho _{xx}^{2} \varpropto \tau ^{-2}
$$

Skew-scattering 由于是 $\sigma _{xy}^{\text{skew}} \varpropto \tau $，导致 $\rho _{xy}^{\text{skew}} \varpropto \tau ^{-1} \varpropto \rho _{xx}$。而 side-jump 发生的 $\sigma _{xy}^{\text{ss}} \varpropto \tau ^{0}$，所以和 intrinsic 是混在一起的，一般性来讲有：
$$
\sigma _{xy} =a\rho _{xx}^{2} +b\rho _{xx} \ ( +c)
$$
通过拟合就可以得到 skew-scattering 和 intrinsic (如果假设 side-jump 很小的话)

下面我们通过 Boltzmann equation 解释为什么两个 extrinsic 是这样的表现：首先来看散射项，两种外在的杂质散射都可以通过对于杂质 potential $U(\mathbf{r})$ 的 spin-dependant scattering 来解释：
$$
H_{\mathbf{k} ,\mathbf{k}^{\prime }}^{\text{dis}} =U_{\mathbf{k} ,\mathbf{k}^{\prime }}\left( 1-i\lambda \mathbf{\sigma } \cdot \left(\mathbf{k} \times \mathbf{k}^{\prime }\right)\right)
$$
skew scattering 表现为 asymmetric transition，因为只有这种 non-reciprocity 才能导致 Hall 电流。这个不能只用 Born approximation，因为 $| H| ^{2}$ 只能给出对称项。必须至少展开到一阶和二阶的干涉项，才可以可以给出反对称的跃迁概率 linear to $\lambda $：
$$
W_{\mathbf{k} ,\mathbf{k}^{\prime }}^{A} =-W_{\mathbf{k}^{\prime } ,\mathbf{k}}^{A}
$$
由于这个跃迁概率同样正比于杂质浓度，因此 skew scattering rate 和 Drude scattering rate 的比值和杂质浓度无关。
$$
\frac{W_{\mathbf{k} ,\mathbf{k}^{\prime }}^{A}}{W_{\mathbf{k} ,\mathbf{k}^{\prime }}^{S}} =\alpha _{\text{skew}}
$$
那么 $j_{\text{skew}} \approx \alpha _{\text{skew}} j_{s}$，而普通电流 $j_{s} =\sigma E\varpropto \tau $，因此便可以大致得到
$$
\sigma _{xy}^{\text{skew}} \varpropto \tau 
$$

而 side-jump 则可以看作是以 $1/\tau $ 的频率 (同样正比于杂质浓度，因此可以用 Drude $\tau $) 给予横向的位移 $\delta y$，但是这需要分布的不平衡。这个不平衡由外加电场导致，量级大约是$\varpropto \tau $，因为在电导的图像中，大概是整个费米面在动量空间向右移动了 $\tau $ 之后再跳回来，所以这个分布的不平衡平均下来$\varpropto \tau $。二者结合得到 $\sigma _{xy}^{\text{ss}} \varpropto \tau ^{0}$ 的依赖。

于是：根据 $\tau $ 的大小，可以分为几个区域。记得普通金属电阻率 $\varpropto \tau ^{-1}$，是 $T$ 和 $T^{5}$ 两个区间。当然也要看 $\tau $ 本身的大小。大概可以写成
$$
\sigma _{xy} =A\tau ^{-2} +B\tau ^{-1} +c
$$
如果 $\tau $ 比较大 / 往往低温，则 skew scattering 主导，good metal regime 是 $\tau ^{-1}$ 主导，还要注意分辨 intrinsic 和 side-jump，如果是 low mobility regime，导电靠 hopping 完成，上面的图像可能不适用了。

# 后期的发展

2000s 前后的一个研究重点是铁磁半导体，textbook case being (Ga, Mn)As。FM 是 RKKY 引导的，并且 scattering independent 项主导，现在人们普遍认为是 intrinsic，有一个 mean field 的估计。但是之后铁磁半导体就僵化了。

GMR 和 colossal MR 出现之后这个又火了一波，集中在氧化物 FM 上面，并且得到了一个新的 AHE 机制就是 spin chirality，也就是磁矩有空间变化，电子经过时积累 Berry phase。比如 manganites, whose transport generally includes hopping btw Mn sites leading to colossal MR. 这个就联系到 skyrmion，也是一个 spin texture，而 spin chirality 就是 more population of L skyrmion v.s. R skyrmion. 

更后面就是 TI，Weyl，TMD 的 valley Hall effect 等等。

# 铁磁性和 SOC 和 spin relaxation

导体 FM 一般是 itinerent 的，最简单的 theory 是 Stoner 给出的那套 mean field 理论。FM semiconductor 里面就是 hole-mediated Mn FM 也就是 RKKY，而 TI 当中是 van Vleck mechanism。

$M(\mathbf{r})$ 的 inhomogeneity 的例子是 skyrmion，其在输运的作用我们上面说了，其实就是给了一个有效磁场，其效果甚至可以达到 1000 T for skyrmions smaller than 10 nm。这个新的机制造成的 Hall effect 叫 topological Hall effect。不过由于 skyrmion 形成了会削弱磁化强度，这个有时候和 AHE 还分不清楚。

我们接下来讲 spin-orbit coupling，注意其真正形式是
$$
H_{\text{SO}} =\frac{\hbar }{4m^{2} c^{2}} \ \mathbf{\sigma } \cdot ( \nabla V\times \mathbf{p})
$$
是 relativistic effect，运动的电子感受到电场变换而来的磁场！这个电场有很多来源，所以这里写的是所有 potential 之和，而不是直接 $\mathbf{L} \cdot \mathbf{S}$ 形式。在原子中 $\nabla V\varpropto \hat{r}$ 所以变化成了 $\mathbf{L} \cdot \mathbf{S}$，适合描述内层电子。但是外层电子并非，其 $\nabla V$ 更像是一个平均场，包含了 intrinsic 的电子贡献，和 extrinsic 的 impurities & phonons. 对于二维我们讲过了 Rashba，more generally it is a momentum-dependant effective magnetic field:
$$
H_{R} =\mathbf{\sigma } \cdot \mathbf{B}(\mathbf{k})
$$
这个形式和 Dyakonov-Perel mechanism of spin relaxation 相关。scalar scattering 之后，$\mathbf{k}\rightarrow \mathbf{k}^{\prime }$，从而感受到不同的有效磁场。这时候需要比较两个 characteristic time，一个是 relaxation time of scattering $\tau $，另一个是 spin precession frequency$\varpropto B$。如果散射很多，$B\ll \tau ^{-1}$，自旋来不及进动，从而 momentum scattering increases the spin lifetime。如果 precession 快于散射，$B\gg \tau ^{-1}$，那么散射会阻碍自旋的寿命。第一个区域比较反直觉，但是在之前的年代，能测到的就只有 DP 这个区间。

另外一种散射机制 Elliott-Yafet 和 spin-dependant scattering 相关，而 DP 是 scalar scattering + SOC 导致的。

再简单讲一句 non-linear AHE，在 few-layer and monolayer WTe $_{2}$ 当中测到。如果 TRS 在，二阶的非线性响应是 Onsager relation 允许的，且一般是 extrinsic 的。如果没有 TRS，可以是 intrinsic，由 Berry curvature dipole $\int _{\mathbf{k}}\mathbf{k} \Omega (\mathbf{k})$ 导致。具体的我们之后看文献遇到了再说。

关于 TI 的部分，慢慢更新 TI 再说。

> 如果还要再补充 SOC，就在这里补充了。