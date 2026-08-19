---
title: 冷原子物理 笔记 Chap. 2
published: 2026-08-18
description: ''
image: ''
tags: [AMO]
category: 'Learning Note'
draft: false 
lang: ''
---
# Scattering length

我们先来研究冷原子体系的 two-body interaction，大概有一下三个特点：
- short ranged: 可以近似为 $V(\mathbf{r}) =0$ when $r >r_{0}$
- dilute: 大部分时间，原子间距 $d\gg r_{0}$，由于量子性，de Broglie 波长 $k\sim 1/d$，因此有动能远小于 $r_{0}$ 定义的能量量纲，或者直接写 $k\ll \frac{1}{r_{0}}$
- low energy: 动能远小于 attractive potential 的强度 $\mathcal{E}_{k} \ll V_{0}$

## Phase Shift and scattering length

经过约化质量的处理以后，二体相互作用变成
$$
\left( -\frac{\hbar ^{2}}{2\overline{m}} \nabla ^{2} +V(\mathbf{r})\right) \Psi (\mathbf{r}) =E\psi (\mathbf{r})
$$
暂时先只考虑 Cs 这种 isotropic 的，一个球对称性 potential，因此可以把 $\Psi (\mathbf{r})$ 分波法展开
$$
\Psi (\mathbf{r}) =\sum\limits _{l}\frac{\chi _{kl}( r)}{kr} P_{l}(\cos \theta )
$$
得到径向方程
$$
\frac{\mathrm{d}^{2} \chi _{kl}}{\mathrm{d} r^{2}} -\frac{l( l+1)}{r^{2}} \chi _{kl} +\frac{2\overline{m}}{\hbar ^{2}}( E-V( r)) \chi _{kl} =0
$$
先考虑 $l=0$ 的 s-wave，然后 $r >r_{0}$ 的解是
$$
\chi _{k} =A\sin( kr+\delta _{k})
$$
这个 phase shift $\delta _{k}$ 刻画低能散射的特征，进一步，可以在 $r=r_{0}$ 对 boundary condition，通过 $\chi ^{\prime } /\chi $ 这种操作去掉归一化因子，那么得到：
$$
\frac{\chi ^{\prime }( r< r_{0})}{\chi ( r< r_{0})}\Bigl|_{r=r_{0}} =\frac{k\cos( kr_{0} +\delta _{k})}{\sin( kr_{0} +\delta _{k})} \approx \frac{k}{\tan \delta _{k}}
$$
用了 $kr_{0} \ll 1$。在 $r< r_{0}$ 区域，我们可以假设 $E$ 相对 $V(\mathbf{r})$ 小。因此可以假设右边的东西对 $k$ 近似没有依赖，引入散射长度 $a_{s}$：
$$
\frac{k}{\tan \delta _{k}} =-\frac{1}{a_{s}}
$$
因此低能散射所有的相移都可以由这个散射长度刻画。注意为什么不考虑 $l >0$ 是因为 $\delta _{k} \varpropto k^{2l+1}$ 因此在长波状况下不考虑，而这里显然是长波。