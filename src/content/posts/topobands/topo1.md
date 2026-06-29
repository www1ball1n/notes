---
title: Notes on Topological Band Theory 1
published: 2026-06-28
description: ''
image: ''
tags: [Basics, TopoPhysics, Theory]
category: 'Reading Notes'
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