---
title: Wolstenholme
published: 2026-08-24
description: 你证不过我你信吗？
image: ''
tags: [数论?前置]
category: 学习
draft: false 
lang: ''
---

## Wolstenholme定理

### 前置知识

**二项式系数**：$\binom{a}{b}$ 表示从a个不同元素里选出b个元素(不考虑顺序)的组合数 类似于$C_n^k$
$$
\binom{n}{k} = \frac{n!}{k!(n-k)!}
$$
**调和级数**：$H_n=\sum_{i=1}^{n}\frac{1}{i}$  在$\pmod{p}$下，$\frac{1}{i}$代表 $i^{-1} \pmod{p}$ 

### 定义

**定理：**
$$
\text{对于素数 } p \geq 5: \binom{2p-1}{p-1} \equiv 1 \pmod{p^3}
$$
**调和级数**等价表述：
$$
\text{对于素数 } p \geq 5: \sum_{i=1}^{p-1} \frac{1}{i} \equiv 0 \pmod{p^2}
$$


**证明：**

我们先证**调和级数**的表述:$\sum_{i=1}^{p-1}\frac{1}{i}\equiv0\pmod{p^2}$

首先将$i\in[1,p-1]$里的数配对为$(i,p-1)$ 则有：
$$
\frac{1}{i}+\frac{1}{p-1}=\frac{p}{i(p-i)}\equiv p*\frac{1}{i(p-i)}\pmod{p^2}
$$

$$
则H_{p-1}=p\sum_{i=1}^\frac{p-1}{2}\frac{1}{i(p-i)}\pmod{p^2}
$$

因为其已经化为含有一个p的表述，所以只需证明后半部分
$$
S=\sum_{i=1}^\frac{p-1}{2}\frac{1}{i(p-i)}\equiv 0 \pmod{p}
$$
因为 $p-i\equiv -i\pmod{p}$ 所以 $i(p-i)\equiv-i^2\pmod{p}$ 所以我们只需要证： 
$$
S=-\sum_{i=1}^\frac{p-1}{2}i^{-2}\equiv 0 \pmod{p}
$$
设$A=\{1,2,3,...p-1\}$，我们知道
$$
\sum_{k=1}^{p-1}k^2=\frac{(p-1)p(2p-1)}{6}\equiv\frac{(-1)p(-1)}{6}\equiv0\pmod{p}
$$
而对于$k\in A,总有k^{-1}\in A$,则当k遍历A时，$k^{-1}$也遍历A

所以
$$
\sum_{k=1}^{p-1}(k^{-1})^2=\sum_{k=1}^{p-1}k^2\equiv0\pmod{p}
$$
再将其分为两段：
$$
\sum_{k=1}^{p-1}k^{-2}=\sum_{k=1}^\frac{p-1}{2}k^{-2}+\sum_{k=\frac{p+1}{2}}^{p-1}k^{-2}
$$
对于后半段，我们令$j=p-k$则有：
$$
\sum_{k=\frac{p+1}{2}}^{p-1}k^{-2}=\sum_{j=1}^{\frac{p-1}{2}}(p-j)^{-2}\equiv\sum_{j=1}^{\frac{p-1}{2}}j^{-2}\pmod{p}
$$
所以
$$
\sum_{k=1}^{p-1}k^{-2}=2\sum_{k=1}^\frac{p-1}{2}k^{-2}\equiv0\pmod{p}
$$
即
$$
\sum_{k=1}^\frac{p-1}{2}k^{-2}\equiv0\pmod{p}
$$
得证.



接下来我们再证**组合数的表述**：$\binom{2p-1}{p-1}\equiv1\pmod{p^3}$
$$
\binom{2p-1}{p-1}=\frac{(2p-1)!}{p!(p-1)!}=\frac{(p+1)(p+2)...(p+p-1)}{1·2·...(p-1)}=\prod_{i=1}^{p-1}\frac{p+i}{i}=\prod_{i=1}^{p-1}(1+\frac{p}{i})
$$
展开连乘式：
$$
S=\prod_{i=1}^{p-1}(1+\frac{p}{i})=1+\sum_{i=1}^{p-1}\frac{p}{i}+\sum_{i<j}\frac{p}{i}·\frac{p}{j}+...
$$
所以我们要证的是$S\equiv1\pmod{p^3}$ 因为S中 $\frac{p}{i}$ 三次及以后的项均含有$p^3$,以及前三项中有一个1，所以我们只需要证明
$$
\sum_{i=1}^{p-1}\frac{p}{i}+\sum_{i<j}\frac{p}{i}·\frac{p}{j}=p\sum_{i=1}^{p-1}\frac{1}{i}+p^2\sum_{i<j}\frac{1}{i}·\frac{1}{j}\equiv0\pmod{p^3}
$$
对于第一部分的$\sum_{i=1}^{p-1}\frac{1}{i}$，恰是我们前面已经证过的调和级数表述，$H_{p-1}\equiv0\pmod{p^2}$,所以$pH_{p-1}\equiv0\pmod{p^3}$

所以我们只需要证明第二部分这个恶心的东西：$p^2\sum_{i<j}\frac{1}{i}·\frac{1}{j}\equiv0\pmod{p^3}$ 

我们需要引入一个恒等式：
$$
(\sum_{k=1}^{p-1}\frac{1}{k})^2=\sum_{k=1}^{p-1}\frac{1}{k^2}+2\sum_{i<j}\frac{1}{ij}
$$

> 具体证明不摆出了，我手打好累

所以我们有
$$
\sum_{i<j}\frac{1}{ij}=\frac{1}{2}({H_{p-1}}^2-\sum_{k=1}^{p-1}\frac{1}{k^2})
$$
因为$H_{p-1}\equiv0\pmod{p^2}$,所以${H_{p-1}}^2\equiv0\pmod{p^4}$,那么自然${H_{p-1}}^2\equiv0\pmod{p}$也成立

另一边$\sum_{k=1}^{p-1}\frac{1}{k^2}\equiv0\pmod{p}$是我们上面已经证过的

所以
$$
\sum_{i<j}\frac{1}{ij}\equiv0\pmod{p},p^2\sum_{i<j}\frac{1}{i}·\frac{1}{j}\equiv0\pmod{p^3}
$$
得证.
