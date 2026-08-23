---
title: Getting to Know Quadratic Residues
published: 2026-08-23
description: ''
image: ''
tags: [数论前置壹]
category: 学习
draft: false 
---

## 二次剩余

### 定义

设 $p$ 是奇素数，$\gcd(a, p) = 1$。若存在 $x$ 使 $x^2 \equiv a \pmod{p}$ 有解，则 $a$ 是模 $p$ 的**二次剩余**（QR），否则为**二次非剩余**（QNR）

### 欧拉判别式

**定理**：

$$
a \text{ 是 mod } p \text{ 的二次剩余} \iff a^{(p-1)/2} \equiv 1 \pmod{p}
$$

$$
a \text{ 是 mod } p \text{ 的二次非剩余} \iff a^{(p-1)/2} \equiv -1 \pmod{p}
$$

**证明**：

在 mod p 下，设 $g$ 是原根，$a \equiv g^k \pmod{p}$，k 是某一个整数

$$
(a^{(p-1)/2})^2 = a^{p-1} \equiv 1 \pmod{p}
$$

所以 $a^{(p-1)/2} \equiv \pm 1 \pmod{p}$

$$
a \text{ 是二次剩余} \iff x^2 \equiv g^k \pmod{p} \text{ 有解} \iff k \text{ 必定是偶数}
$$

当 k 是偶数时：

$$
a^{(p-1)/2} = g^{k(p-1)/2} = (g^{p-1})^{k/2} \equiv 1 \pmod{p}
$$

当 k 是奇数时：

$$
g^{k(p-1)/2} = g^{(p-1)/2} \cdot (g^{p-1})^{(k-1)/2} \equiv g^{(p-1)/2} \pmod{p}
$$

因为 g 是原根，所以 $g^{(p-1)/2} \not\equiv 1 \pmod{p}$（与原根的阶是最小正整数相悖），但是 $(g^{(p-1)/2})^2 \equiv 1 \pmod{p}$，所以：

$$
g^{(p-1)/2} \equiv -1 \pmod{p}
$$

### 勒让德符号

**定义**

$$
\left(\frac{a}{p}\right) = \begin{cases} 0 & p \mid a \\ 1 & a \text{ 是二次剩余} \\ -1 & a \text{ 是二次非剩余} \end{cases}
$$

则根据**欧拉判别式**有：

$$
\left(\frac{a}{p}\right) \equiv a^{(p-1)/2} \pmod{p}
$$

**性质**：具有乘法性

$$
\left(\frac{ab}{p}\right) = \left(\frac{a}{p}\right)\left(\frac{b}{p}\right)
$$

### 二次互反律

**定理**：设 $p, q$ 是不同的奇素数，则有

$$
\left(\frac{p}{q}\right) \cdot \left(\frac{q}{p}\right) = (-1)^{\frac{p-1}{2} \cdot \frac{q-1}{2}}
$$

**证明**：

首先我们需要引入**高斯引理**：对于奇素数 $p$ 和整数 $a$，$\gcd(a, p) = 1$

有：

$$
\left(\frac{a}{p}\right) = (-1)^n
$$

其中 $n$ 是序列 $\{a, 2a, 3a, \ldots, \frac{p-1}{2}a\}$ 中 mod p 的最小正剩余中大于 $\frac{p}{2}$ 的数的个数

再引入一个计数原理：在高斯引理中，若 $a$ 为奇数，则：

$$
\left(\frac{a}{p}\right) = (-1)^{\sum_{x \in A_p} \lfloor \frac{ax}{p} \rfloor}
$$

具体证明不摆出.

则有 对于 $p, q$：

$$
A_p = \{1, 2, 3, \ldots, \frac{p-1}{2}\}, \quad A_q = \{1, 2, 3, \ldots, \frac{q-1}{2}\}
$$

$$
S_1 = \{(x, y) : x \in A_p, y \in A_q, qx > py\}
$$

$$
S_2 = \{(x, y) : x \in A_p, y \in A_q, qx < py\}
$$

对于 $S_1$ 而言：$qx > py \Rightarrow y < \frac{qx}{p}$，则 $y = \lfloor\frac{qx}{p}\rfloor$

所以：

$$
|S_1| = \sum_{x \in A_p} \lfloor\frac{qx}{p}\rfloor
$$

则：

$$
\left(\frac{q}{p}\right) = (-1)^{\sum_{x \in A_p} \lfloor \frac{qx}{p} \rfloor} = (-1)^{|S_1|}
$$

同理：

$$
\left(\frac{p}{q}\right) = (-1)^{\sum_{x \in A_q} \lfloor \frac{px}{q} \rfloor} = (-1)^{|S_2|}
$$

对于任意一对 $(x, y)$，要么 $qx > py$，要么 $qx < py$，所以 $|S_1|, |S_2|$ 瓜分了所有 $(x, y)$ 组成的集合 $A_p \times A_q$

> 如果 $qx = py$，因为 $p, q$ 互质，则必须是 p 整除 x，但是 x 只取 1 到 $\frac{p-1}{2}$，不可能达到。所以 $qx = py$ 不可能发生

又因为：

$$
|S_1| + |S_2| = |A_p| \times |A_q|
$$

所以：

$$
\left(\frac{p}{q}\right) \cdot \left(\frac{q}{p}\right) = (-1)^{\frac{p-1}{2} \cdot \frac{q-1}{2}}
$$

### Jacobi符号

勒让德符号推广到任意的奇整数$n={p_1}{p_2}...p_k$:
$$
\left(\frac{a}{n}\right) = \prod_{i=1}^{k} \left(\frac{a}{p_i}\right)
$$
> **区别**：Jacobi符号中，=-1则a一定是非剩余，但是=1不保证是二次剩余（因子可能抵消）



### 贝祖定理

**定理**：对任意不全为零的整数 $a, b$，存在整数 $x, y$ 使 $ax + by = \gcd(a, b)$。

**证明**：

首先需要引入**良序原理**：自然数集合$N$(或者正整数集合{1,2,3,...})的每一个非空子集，都**一定存在**一个最小的元素

令
$$
S=\{ax+by|x,y\in Z,ax+by>0\}
$$
不难得知S非空，又由于良序原理，所以S中必有一个最小元素，记其为d

则必存在$x_0,y_0$,使得 $d = ax_0+by_0$ 再用a除以d做带余除法：
$$
a=d*q+r,0\leq r<d
$$
代入原式：
$$
r=a-dq=a-(ax_0+by_0)q=a(1-x_0q)+b(-y_0q)
$$
则r也可以写成$a,b$的线性组合，但是r<d，如果r非0，这就与d是最小元素相悖，所以r必等于0，所以$a=dq$，所以$d|a$ 

> 同理证明d整除b

因此，d是a和b的一个公因数

再设c是a和b的任意一个公因数，那么必有
$$
c|(ax_0+by_0)=d
$$
则不难知必有$c\leq d$ 所以d是最大的一个a和b的公因数

### gcd的性质

| 性质                 | 公式                                        |
| -------------------- | ------------------------------------------- |
| 交换律               | $\gcd(a, b) = \gcd(b, a)$                   |
| 结合律               | $\gcd(a, \gcd(b, c)) = \gcd(\gcd(a, b), c)$ |
| GCD与LCM(最小公倍数) | $\gcd(a,b) \cdot \text{lcm}(a,b) = ab$      |
| 线性性               | $\gcd(ca, cb) = c \cdot \gcd(a, b)$         |

### 算术基本定理

**定理**：每个大于 $1$ 的正整数 $n$ 可唯一表示为素数的乘积（不考虑顺序）。

