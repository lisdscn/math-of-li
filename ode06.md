# 第六章 线性微分方程组
## 一、齐次与非齐次线性微分方程组
形如
$$
\frac{d\boldsymbol{y}}{dx} = A\boldsymbol{y} + \boldsymbol{f}(x)
$$
- 若 $\boldsymbol{f}(x) \equiv \boldsymbol{0}$：**齐次线性微分方程组**
- 若 $\boldsymbol{f}(x) \not\equiv \boldsymbol{0}$：**非齐次线性微分方程组**

### 引理（齐次解的线性组合）
若 $\boldsymbol{y}(x)=\boldsymbol{y}_1(x),\ \boldsymbol{y}(x)=\boldsymbol{y}_2(x)$ 是 $\displaystyle\frac{d\boldsymbol{y}}{dx}=A\boldsymbol{y}$ 的解，则其线性组合
$$
\boldsymbol{y}=C_1\boldsymbol{y}_1(x)+C_2\boldsymbol{y}_2(x)
$$
仍是 $\displaystyle\frac{d\boldsymbol{y}}{dx}=A\boldsymbol{y}$ 的解（$C_1,C_2$ 为常数）。

记 $S$ 为 $\displaystyle\frac{d\boldsymbol{y}}{dx}=A\boldsymbol{y}$ 全部解构成的集合，$A$ 为 $n$ 阶方阵，则 $S$ 是**$n$ 维线性空间**。

设 $\boldsymbol{y}_1(x),\boldsymbol{y}_2(x),\dots,\boldsymbol{y}_n(x)$ 是 $\displaystyle\frac{d\boldsymbol{y}}{dx}=A\boldsymbol{y}$ 在 $x\in[a,b]$ 上的 $n$ 个线性无关解，则通解：
$$
\boldsymbol{y} = \sum_{i=1}^n C_i \boldsymbol{y}_i(x)
$$
$C_1,C_2,\dots,C_n$ 为任意常数。

### 朗斯基行列式
$$
W(x) = \det\big(\boldsymbol{y}_1(x),\boldsymbol{y}_2(x),\dots,\boldsymbol{y}_n(x)\big) = W(x_0)\exp\left\{\int_{x_0}^x \mathrm{tr}\big[A(s)\big]ds\right\}
$$
结论：齐次微分方程组的解组线性无关 $\iff W(x)\not=0 \iff W(x_0)\not=0$。

### 解矩阵与基解矩阵
设 $Y(x)=(y_{ij}(x))_{n\times n}$ 为 $\displaystyle\frac{d\boldsymbol{y}}{dx}=A\boldsymbol{y}$ 的**解矩阵**，满足矩阵微分方程：
$$
\frac{dY}{dx} = A(x)Y(x)
$$
此时方程组通解：
$$
\boldsymbol{y}_{n\times 1} = Y_{n\times n}\boldsymbol{C}_{n\times 1} = \boldsymbol{\Phi}(x)\boldsymbol{C}_{n\times 1}
$$
其中 $\boldsymbol{C}_{n\times 1}$ 为 $n$ 维常数列向量，$\boldsymbol{\Phi}(x)$ 称为**基解矩阵**。

### 基础示例
$$
\frac{d\boldsymbol{y}}{dt} = A(t)\boldsymbol{y},\quad A(t)=\begin{pmatrix} 0 & 1 \\ -1 & 0 \end{pmatrix}
$$
令 $\boldsymbol{y}=\begin{pmatrix} y_1 \\ y_2 \end{pmatrix}$，则
$$
\begin{cases}
\displaystyle\frac{dy_1}{dt} = y_2 \\[4pt]
\displaystyle\frac{dy_2}{dt} = -y_1
\end{cases}
\iff
\frac{d^2y_1}{dt^2} + y_1 = 0
$$
解得
$$
\begin{cases}
y_1 = C_1\cos x + C_2\sin x \\
y_2 = -C_1\sin x + C_2\cos x
\end{cases}
$$
$C_1,C_2$ 为常数。

基解矩阵：
$$
\boldsymbol{\Phi}(x) = \begin{pmatrix} \cos x & \sin x \\ -\sin x & \cos x \end{pmatrix}
$$
通解：
$$
\boldsymbol{y} = \boldsymbol{\Phi}(x)\begin{pmatrix} C_1 \\ C_2 \end{pmatrix},\quad C_1,C_2\in\mathbb{R}
$$

---

## 二、非齐次线性微分方程组
对方程
$$
\frac{d\boldsymbol{y}}{dx} = A\boldsymbol{y} + \boldsymbol{f}(x)
$$
设 $\boldsymbol{\Phi}(x)$ 是对应齐次方程组 $\displaystyle\frac{d\boldsymbol{y}}{dx}=A\boldsymbol{y}$ 的基解矩阵，则非齐次通解：
$$
\boldsymbol{\varphi}(x) = \boldsymbol{\Phi}(x)\boldsymbol{C} + \boldsymbol{\varphi}^*(x)
$$
其中特解
$$
\boldsymbol{\varphi}^*(x) = \boldsymbol{\Phi}(x)\int_{x_0}^x \boldsymbol{\Phi}^{-1}(s)\boldsymbol{f}(s)ds
$$

### 求解示例
初值问题
$$
\begin{cases}
\displaystyle\frac{dx}{dt} = \frac{2t}{1+t^2}x,\quad x(1)=0 \\[4pt]
\displaystyle\frac{dy}{dt} = -\frac1t y + x + t,\quad y(1)=\frac43
\end{cases}
$$
记 $\boldsymbol{Y}=\begin{pmatrix} x \\ y \end{pmatrix}$，写成标准形式
$$
\frac{d\boldsymbol{Y}}{dt} = A(t)\boldsymbol{Y} + \boldsymbol{f}(t),\quad
A(t)=\begin{pmatrix} \dfrac{2t}{1+t^2} & 0 \\[4pt] 1 & -\dfrac1t \end{pmatrix},\quad
\boldsymbol{f}(t)=\begin{pmatrix} 0 \\ t \end{pmatrix},\quad
\boldsymbol{Y}(1)=\begin{pmatrix} 0 \\ \dfrac43 \end{pmatrix}
$$

1. 解 $x$ 分量：
$$
\frac{dx}{x} = \frac{2t}{1+t^2}dt \implies x = C_1(1+t^2)
$$
$C_1=0$ 满足初值 $x(1)=0$，故 $x(t)\equiv 0$。

2. 代入求 $y$：
$$
t\frac{dy}{dt} + y = t^2 \implies \frac{d(yt)}{dt} = t^2
$$
积分得
$$
yt = \frac{t^3}{3} + C_2 \implies y = \frac{t^2}{3} + \frac{C_2}{t}
$$

3. 套基解矩阵标准流程：
先解齐次方程 $\displaystyle\frac{d\boldsymbol{Y}}{dt}=A(t)\boldsymbol{Y}$ 求基解矩阵 $\boldsymbol{\Phi}(t)$，再代入常数变易公式
$$
\boldsymbol{\varphi}^*(t) = \boldsymbol{\Phi}(t)\int_{1}^t \boldsymbol{\Phi}^{-1}(s)\boldsymbol{f}(s)ds
$$
得到通解后代入初值 $t=1$：
$$
\boldsymbol{Y}(1) = \begin{pmatrix} 2 & 0 \\ \dfrac13 & 1 \end{pmatrix}\begin{pmatrix} C_1 \\ C_2 \end{pmatrix} + \begin{pmatrix} 0 \\ \dfrac13 \end{pmatrix}
= \begin{pmatrix} 0 \\ \dfrac43 \end{pmatrix}
$$
解得 $C_1=0,\ C_2=1$，最终特解
$$
\boldsymbol{Y}(t) = \begin{pmatrix} x(t) \\ y(t) \end{pmatrix} = \begin{pmatrix} 0 \\ \dfrac{t^2}{3} + \dfrac1t \end{pmatrix}
$$

---

## 三、常系数线性齐次方程组 $\boldsymbol{y}'=A\boldsymbol{y}$
### 矩阵指数 $e^{xA}$
定义矩阵指数级数：
$$
e^{xA} = E + \sum_{k=1}^{\infty}\frac{x^k}{k!}A^k
$$
求导性质：
$$
\frac{d}{dx}e^{xA} = A + \sum_{k=1}^{\infty}\frac{x^k}{k!}A^{k+1} = A\left(E+\sum_{k=1}^{\infty}\frac{x^k}{k!}A^k\right) = A e^{xA}
$$
因此齐次方程组 $\displaystyle\frac{d\boldsymbol{y}}{dx}=A\boldsymbol{y}$ 的通解可写为
$$
\boldsymbol{y} = e^{xA}\boldsymbol{C}
$$
当 $A$ 阶数很高时，直接展开 $e^{xA}$ 复杂，采用**若尔当标准形**化简。

### 若尔当标准形分解
对 $n$ 阶方阵 $A$，存在可逆矩阵 $P\ (\det P\not=0)$，使得
$$
A = PJP^{-1}
$$
其中 $J=\mathrm{diag}\{J_1,J_2,\dots,J_m\}$，$J_i$ 为 $n_i$ 阶若尔当块：
$$
J_i=\begin{pmatrix} \lambda_i & 1 & & \\ & \lambda_i & \ddots & \\ & & \ddots & 1 \\ & & & \lambda_i \end{pmatrix}
$$
此时
$$
e^{xA} = P e^{xJ} P^{-1},\quad P e^{xJ} = e^{xA}P
$$
$P e^{xJ}$ 也是 $\boldsymbol{y}'=A\boldsymbol{y}$ 的基解矩阵。

#### 示例
$$
A=\begin{pmatrix} 0 & 1 \\ -1 & 0 \end{pmatrix},\quad A^2=-E,\ A^3=-A,\ A^4=E
$$
拆分级数：
$$
e^{xA} = E\left(\sum_{k=0}^\infty \frac{(-1)^k x^{2k}}{(2k)!}\right) + A\left(\sum_{k=0}^\infty \frac{(-1)^k x^{2k+1}}{(2k+1)!}\right)
$$
即
$$
e^{xA} = \cos x \cdot E + \sin x \cdot A = \begin{pmatrix} \cos x & \sin x \\ -\sin x & \cos x \end{pmatrix}
$$
通解
$$
\boldsymbol{y} = \begin{pmatrix} \cos x & \sin x \\ -\sin x & \cos x \end{pmatrix}\begin{pmatrix} C_1 \\ C_2 \end{pmatrix}
$$

### 待定指数函数法
#### 情形1：$A$ 可对角化（无若尔当块，$J=\mathrm{diag}\{\lambda_1,\dots,\lambda_n\}$）
设 $\lambda_i$ 为特征值，$\boldsymbol{\gamma}_1,\dots,\boldsymbol{\gamma}_n$ 线性无关特征向量，则基解矩阵
$$
\boldsymbol{\Phi}(x) = \big(e^{\lambda_1 x}\boldsymbol{\gamma}_1,\ e^{\lambda_2 x}\boldsymbol{\gamma}_2,\ \dots,\ e^{\lambda_n x}\boldsymbol{\gamma}_n\big)
$$
此时 $P=\boldsymbol{\Phi}(0)$，矩阵指数满足
$$
e^{xA} = \boldsymbol{\Phi}(x)\boldsymbol{\Phi}^{-1}(0)
$$

#### 情形2：$A$ 有重特征值（含高阶若尔当块）
设 $\lambda_i$ 为 $n_i$ 重特征值，$\boldsymbol{\gamma}_0$ 是 $(A-\lambda_i E)^{n_i}\boldsymbol{\gamma}=\boldsymbol{0}$ 的非零解，递推广义特征向量：
$$
\begin{cases}
\boldsymbol{\gamma}_1 = (A-\lambda_i E)\boldsymbol{\gamma}_0 \\
\boldsymbol{\gamma}_2 = (A-\lambda_i E)\boldsymbol{\gamma}_1 \\
\quad\vdots \\
\boldsymbol{\gamma}_{n_i-1} = (A-\lambda_i E)\boldsymbol{\gamma}_{n_i-2}
\end{cases}
$$
对应 $\lambda_i$ 的 $n_i$ 个线性无关解：
$$
\boldsymbol{y} = e^{\lambda_i x}\left(\boldsymbol{\gamma}_0 + \frac{x}{1!}\boldsymbol{\gamma}_1 + \dots + \frac{x^{n_i-1}}{(n_i-1)!}\boldsymbol{\gamma}_{n_i-1}\right)
$$
$\boldsymbol{\gamma}_0,\boldsymbol{\gamma}_1,\dots,\boldsymbol{\gamma}_{n_i-1}$ 为 $n$ 维常数列向量。

### 复特征值示例
初值问题
$$
\frac{d\boldsymbol{y}}{dx}=A\boldsymbol{y}+\boldsymbol{f}(x),\quad \boldsymbol{y}(0)=\boldsymbol{\eta},\quad
A=\begin{pmatrix} 0 & -2 \\ 2 & 0 \end{pmatrix},\quad
\boldsymbol{f}(x)=\begin{pmatrix} 3x \\ 4 \end{pmatrix},\quad
\boldsymbol{\eta}=\begin{pmatrix} 2 \\ 3 \end{pmatrix}
$$
1. 特征方程：
$$
\det(\lambda E - A) = \lambda^2 + 4 = 0 \implies \lambda_1=2i,\ \lambda_2=-2i
$$
2. 特征向量：
$$
A\boldsymbol{\gamma}_1=2i\boldsymbol{\gamma}_1 \implies \boldsymbol{\gamma}_1=\begin{pmatrix} 1 \\ -i \end{pmatrix},\quad
A\boldsymbol{\gamma}_2=-2i\boldsymbol{\gamma}_2 \implies \boldsymbol{\gamma}_2=\begin{pmatrix} 1 \\ i \end{pmatrix}
$$
复基解矩阵
$$
\boldsymbol{\Phi}(x) = \begin{pmatrix} e^{2ix} & e^{-2ix} \\ -i e^{2ix} & i e^{-2ix} \end{pmatrix},\quad
\boldsymbol{\Phi}(0)=\begin{pmatrix} 1 & 1 \\ -i & i \end{pmatrix},\quad
\boldsymbol{\Phi}^{-1}(0)=\frac12\begin{pmatrix} 1 & i \\ 1 & -i \end{pmatrix}
$$
3. 实矩阵指数：
$$
e^{xA} = \boldsymbol{\Phi}(x)\boldsymbol{\Phi}^{-1}(0) = \begin{pmatrix} \cos 2x & -\sin 2x \\ \sin 2x & \cos 2x \end{pmatrix}
$$
4. 常数变易求通解：
$$
\boldsymbol{y} = e^{xA}\boldsymbol{C} + e^{xA}\int_{0}^x e^{-sA}\boldsymbol{f}(s)ds
$$
计算积分项后代入初值 $\boldsymbol{y}(0)=\begin{pmatrix}2\\3\end{pmatrix}$ 得 $C_1=2,\ C_2=3$，最终解
$$
\boldsymbol{y} = \begin{pmatrix} \dfrac{13}{4}\cos2x - 3\sin2x - \dfrac54 \\[6pt] 3\cos2x + \dfrac{13}{4}\sin2x + \dfrac32 x \end{pmatrix}
$$

### 含二重实特征值例题
方程组 $\displaystyle\frac{d\boldsymbol{y}}{dx}=A\boldsymbol{y}$，其中
$$
A=\begin{pmatrix} 3 & 1 & 0 \\ -4 & -1 & 0 \\ -4 & -8 & -2 \end{pmatrix}
$$
1. 特征多项式
$$
\det(\lambda E - A) = (\lambda+2)(\lambda-1)^2=0 \implies \lambda_1=-2,\ \lambda_2=1(\text{二重})
$$
2. 若尔当块阶数判断：$\mathrm{rank}(E-A)=2$，对应若尔当块阶数2；
3. 广义特征向量：
$$
(A-E)^2=\boldsymbol{0},\quad
\boldsymbol{\gamma}_{10}=\begin{pmatrix}0\\3\\-8\end{pmatrix},\ \boldsymbol{\gamma}_{20}=\begin{pmatrix}9\\0\\-28\end{pmatrix}
$$
$$
\boldsymbol{\gamma}_{11}=(A-E)\boldsymbol{\gamma}_{10}=\begin{pmatrix}-3\\6\\0\end{pmatrix},\quad
\boldsymbol{\gamma}_{21}=(A-E)\boldsymbol{\gamma}_{20}=\begin{pmatrix}-18\\36\\-120\end{pmatrix}
$$
4. 基解矩阵
$$
\boldsymbol{\Phi}(x) = \Big(e^x(\boldsymbol{\gamma}_{10}+x\boldsymbol{\gamma}_{11}),\ e^x(\boldsymbol{\gamma}_{20}+x\boldsymbol{\gamma}_{21}),\ e^{-2x}\begin{pmatrix}0\\0\\1\end{pmatrix}\Big)
= \begin{pmatrix} -3xe^x & (9-18x)e^x & 0 \\ (3+6x)e^x & 36xe^x & 0 \\ -8e^x & (-28-120x)e^x & e^{-2x} \end{pmatrix}
$$
通解
$$
\boldsymbol{y} = C_1 e^x\begin{pmatrix} -3x \\ 3+6x \\ -8 \end{pmatrix} + C_2 e^x\begin{pmatrix} 9-18x \\ 36x \\ -28-120x \end{pmatrix} + C_3 e^{-2x}\begin{pmatrix} 0 \\ 0 \\ 1 \end{pmatrix}
$$
$C_1,C_2,C_3$ 为常数。

---

## 四、n 阶高阶线性微分方程化为一阶方程组
只含单未知函数 $y=y(x)$ 的 $n$ 阶线性微分方程：
$$
y^{(n)} + a_1(x)y^{(n-1)} + a_2(x)y^{(n-2)} + \dots + a_{n-1}(x)y' + a_n(x)y = f(x) \tag{1}
$$
### 变量替换
令
$$
y_1=y,\quad y_2=y',\quad \dots,\quad y_n=y^{(n-1)}
$$
记向量 $\boldsymbol{y}=\begin{pmatrix} y_1 \\ y_2 \\ \vdots \\ y_n \end{pmatrix}$，则方程化为一阶线性方程组
$$
\frac{d\boldsymbol{y}}{dx} = A(x)\boldsymbol{y} + \boldsymbol{f}(x)
$$
其中系数矩阵与右端向量：
$$
A(x) = \begin{pmatrix}
0 & 1 & 0 & \dots & 0 \\
0 & 0 & 1 & \dots & 0 \\
\vdots & \vdots & \vdots & \ddots & \vdots \\
0 & 0 & 0 & \dots & 1 \\
-a_n(x) & -a_{n-1}(x) & -a_{n-2}(x) & \dots & -a_1(x)
\end{pmatrix},\quad
\boldsymbol{f}(x) = \begin{pmatrix} 0 \\ 0 \\ \vdots \\ 0 \\ f(x) \end{pmatrix}
$$

### 高阶方程解组的朗斯基行列式
设 $\varphi_1,\varphi_2,\dots,\varphi_n$ 是 $n$ 阶齐次方程 $y^{(n)}+\sum a_i y^{(n-i)}=0$ 的 $n$ 个解，朗斯基行列式
$$
W(x) = \begin{vmatrix}
\varphi_1(x) & \varphi_2(x) & \dots & \varphi_n(x) \\
\varphi_1'(x) & \varphi_2'(x) & \dots & \varphi_n'(x) \\
\vdots & \vdots & & \vdots \\
\varphi_1^{(n-1)}(x) & \varphi_2^{(n-1)}(x) & \dots & \varphi_n^{(n-1)}(x)
\end{vmatrix}
$$
阿贝尔公式：
$$
W(x) = W(x_0)e^{-\int_{x_0}^x a_1(s)ds} = W(x_0)e^{\int_{x_0}^x \mathrm{tr}[A(s)]ds}
$$
判定：
- $W(x)\equiv 0 \iff \varphi_1,\dots,\varphi_n$ 线性相关
- $W(x)\not\equiv 0 \iff \varphi_1,\dots,\varphi_n$ 线性无关

通解：
$$
y = \sum_{i=1}^n C_i \varphi_i,\quad C_i\in\mathbb{R}
$$

### 二阶线性非齐次方程示例
求解
$$
\frac{d^2y}{dx^2} - 2\frac{dy}{dx} + 2y = 4e^x\cos x
$$
1. 化为一阶方程组
令 $y_1=y,\ y_2=y'$，则
$$
\frac{d}{dx}\begin{pmatrix} y_1 \\ y_2 \end{pmatrix}
= \begin{pmatrix} 0 & 1 \\ -2 & 2 \end{pmatrix}\begin{pmatrix} y_1 \\ y_2 \end{pmatrix}
+ \begin{pmatrix} 0 \\ 4e^x\cos x \end{pmatrix}
$$
2. 齐次方程特征方程
$$
\det(\lambda E - A) = \begin{vmatrix}\lambda & -1 \\ 2 & \lambda-2\end{vmatrix} = \lambda^2-2\lambda+2=0 \implies \lambda_1=1+i,\ \lambda_2=1-i
$$
齐次通解
$$
y_h = C_1 e^x\cos x + C_2 e^x\sin x
$$
3. 待定系数求特解
设特解形式 $\varphi(x) = ax e^x\cos x + bx e^x\sin x$，代入方程比较系数得 $a=0,\ b=2$，特解
$$
\varphi(x) = 2x e^x \sin x
$$
4. 原方程通解
$$
y = C_1 e^x\cos x + C_2 e^x\sin x + 2x e^x\sin x
$$

### 常系数高阶方程通用解法
对方程 $y^{(n)}+\sum_{i=1}^n a_i y^{(n-i)}=f(x)$，先解特征方程 $\det(\lambda E-A)=0$ 得到特征值 $\lambda_1,\dots,\lambda_s$，$\lambda_i$ 为 $n_i$ 重根，$\sum n_i=n$。
齐次通解形式：
$$
y_h = \sum_{i=1}^s \left(\sum_{j=0}^{n_i-1} C_{ij} x^j\right)e^{\lambda_i x}
$$
$C_{ij}$ 全部为任意常数。
若特征值为共轭复根 $\lambda=a\pm bi\ (a,b\in\mathbb{R})$，对应实解 $e^{ax}\cos bx,\ e^{ax}\sin bx$。

#### 例题：$y''+4y'+4y=\cos2x$
1. 化为方程组
$$
\frac{d}{dx}\begin{pmatrix} y_1 \\ y_2 \end{pmatrix}
= \begin{pmatrix} 0 & 1 \\ -4 & -4 \end{pmatrix}\begin{pmatrix} y_1 \\ y_2 \end{pmatrix}
+ \begin{pmatrix} 0 \\ \cos 2x \end{pmatrix}
$$
2. 特征方程
$$
\det(\lambda E-A) = \lambda^2+4\lambda+4=(\lambda+2)^2=0 \implies \lambda=-2\ (\text{二重})
$$
齐次通解
$$
y_h = (C_1+C_2 x)e^{-2x}
$$
3. 待定特解，设 $\varphi^*(x)=a\cos2x+b\sin2x$，代入方程比较系数：
$$
8b\cos2x -8a\sin2x = \cos2x \implies a=0,\ b=\frac18
$$
特解
$$
\varphi^*(x) = \frac18 \sin 2x
$$
4. 原方程通解
$$
y = (C_1+C_2 x)e^{-2x} + \frac18\sin2x
$$
$C_1,C_2$ 为任意常数。