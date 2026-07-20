# 第三章：存在与唯一性定理
## 3.1 皮卡存在与唯一性定理
### 定理表述
初值问题
$$(E):
\begin{cases}
\displaystyle \frac{dy}{dx}=f(x,y)\\
y(x_0)=y_0
\end{cases}$$
设 $f(x,y)$ 在矩形区域 $R:|x-x_0|\le a,\ |y-y_0|\le b$ 内连续，且关于 $y$ 满足**利普希茨条件**，
则初值问题 $(E)$ 在区间 $I=[x_0-h,\,x_0+h]$ 上**有且仅有一个解**。

其中
$$h=\min\left\{a,\frac{b}{M}\right\},\quad M=\max\limits_{(x,y)\in R}|f(x,y)|$$

### 配套定义
1. **利普希茨条件**
存在常数 $L>0$，使得区域内任意两点满足：
$$|f(x,y_1)-f(x,y_2)|\le L|y_1-y_2|$$

2. **皮卡迭代序列**
$$y_{n+1}(x)=y_0+\int_{x_0}^x f\big(t,y_n(t)\big)dt,\quad x\in I,\ n=0,1,2,\dots$$
迭代初值：$y_0(x)\equiv y_0$

### 例题
求初值问题 $\displaystyle \frac{dy}{dx}=x+y+1,\ y(0)=0$ 的皮卡迭代序列，并取极限求解。

迭代公式：
$$y_{n+1}(x)=y_0+\int_0^x f\big(t,y_n(t)\big)dt,\quad f(x,y)=x+y+1,\ y_0=0$$
化简得
$$y_{n+1}(x)=\frac{x^2}{2}+x+\int_0^x y_n(t)dt$$

逐项迭代：
$$
\begin{align*}
y_1(x)&=y_0+\int_0^x \big(t+y_0+1\big)dt=\frac{x^2}{2}+x\\
y_2(x)&=\frac{x^2}{2}+x+\int_0^x y_1(t)dt
=\frac{x^2}{2}+x+\frac{x^3}{3!}+\frac{x^2}{2}
=x+\frac{x^2}{2}+\frac{x^2}{2}+\frac{x^3}{3!}
\end{align*}
$$

通过数学归纳法假设通项：
$$y_n(x)=\sum_{m=1}^n \frac{x^m}{m!}+\sum_{k=2}^{n+1}\frac{x^k}{k!}$$
$n=0$ 直至 $k=n-1$ 均满足归纳假设,可验证递推关系成立。

令 $n\to\infty$ 取极限：
$$
\begin{align*}
y(x)&=\sum_{m=1}^{\infty}\frac{x^m}{m!}+\sum_{k=2}^{\infty}\frac{x^k}{k!}\\
&=(e^x-1)+(e^x-1-x)\\
&=2e^x-x-2
\end{align*}
$$

核验：$y(0)=0$，求导 $\displaystyle \frac{dy}{dx}=2e^x-1=x+y+1$，完全满足方程与初值条件。

---

## 3.2 佩亚诺存在定理
### 欧拉折线构造
初值问题
$$
\begin{cases}
\displaystyle \frac{dy}{dx}=f(x,y)\\
y(x_0)=y_0
\end{cases}
$$
沿用记号：$M=\max\limits_{(x,y)\in R}|f(x,y)|$，区域 $R:\begin{cases}|x-x_0|\le a\\|y-y_0|\le b\end{cases}$，$h=\min\left\{a,\dfrac{b}{M}\right\}$。

取步长 $\displaystyle h_n=\frac{h}{n}$，节点 $x_k=x_0+kh_n,\ k=0,\pm1,\pm2,\dots,\pm n$。

#### 右区间分段递推
在小区间 $[x_k,x_{k+1}]$ 上：
$$y_k=y_{k-1}+f(x_{k-1},y_{k-1})(x_k-x_{k-1})$$

若 $x_0<x_s<x\le x_{s+1}\le x_0+h$，欧拉折线表达式：
$$\varphi_n(x)=y_0+\sum_{k=0}^{s-1}f(x_k,y_k)(x_{k+1}-x_k)+f(x_s,y_s)(x-x_s)$$

#### 左区间分段递推
若 $x_0-h\le x_{s-1}\le x<x_s<x_0$，欧拉折线表达式：
$$\varphi_n(x)=y_0+\sum_{k=-s+1}^{0}f(x_k,y_k)(x_{k+1}-x_k)+f(x_{-s},y_{-s})(x-x_{-s})$$

### 阿斯克利定理
设闭区间 $I$ 上函数序列 $\{f_n(x)\}$：
1. **一致有界**：$\exists K>0$，对 $\forall x\in I,\ n=1,2,3,\dots$，恒有 $|f_n(x)|<K$；
2. **等度连续**：$\forall \varepsilon>0,\exists \delta=\delta(\varepsilon)$，只要 $x_1,x_2\in I,\ |x_1-x_2|<\delta$，就有 $|f_n(x_1)-f_n(x_2)|<\varepsilon$ 对全部 $n$ 同时成立。

则函数序列 $\{f_n(x)\}$ 必存在一致收敛的子序列。

### 两条引理
1. **引理1**
欧拉折线序列 $\{y=\varphi_n(x)\}$ 在区间 $[x_0-h,x_0+h]$ 上至少存在一个一致收敛子列。
> 证明思路：只需证明欧拉折线序列一致有界+等度连续，套用阿斯克利定理。

2. **引理2**
欧拉折线 $y=\varphi_n(x)$ 在 $[x_0-h,x_0+h]$ 上满足：
$$\varphi_n(x)=y_0+\int_{x_0}^x f\big(t,\varphi_n(t)\big)dt+\delta_n(x)$$
其中 $\displaystyle \lim_{n\to\infty}\delta_n(x)=0,\ |x-x_0|\le h$。

### 佩亚诺存在定理完整内容
若 $f(x,y)$ 在区域 $R$ 内连续，则初值问题
$$(E):
\begin{cases}
\displaystyle \frac{dy}{dx}=f(x,y)\\
y(x_0)=y_0
\end{cases}$$
在区间 $[x_0-h,x_0+h]$ 上**至少存在一个解** $y=y(x)$（$R,h$ 定义同上）。

⚠️ 重要注释
本定理证明只能使用欧拉折线序列，**不能替换为皮卡迭代序列**。

### Müller构造反例
$$(E_0):\quad \frac{dy}{dx}=F(x,y),\quad y(0)=0$$
$$
F(x,y)=
\begin{cases}
0, & x=0,\ -\infty<y<+\infty\\
2x, & 0<x\le1,\ -\infty<y<0\\
\displaystyle 2x-\frac{4y}{x}, & 0<x\le1,\ 0\le y<x^2\\
-2x, & 0<x\le1,\ x^2\le y<+\infty
\end{cases}
$$
$F(x,y)$ 在带状区域 $S:0\le x\le1,\,-\infty<y<+\infty$ 连续，但不满足利普希茨条件，欧拉折线序列不再具备前述收敛性质。

---

## 3.3 解的延伸（延拓定理）
### 直观延拓示例
$$
\begin{cases}
y=x,\ x\in[-1,1]\\
y=\tan x,\ x\in[0,1]
\end{cases}
\xrightarrow{\text{延拓后无法继续向外延伸}}
\begin{cases}
y=x,\ x\in(-\infty,+\infty)\\
y=\tan x,\ x\in\left(-\frac{\pi}{2},\frac{\pi}{2}\right)
\end{cases}
$$

### 核心结论
1. 微分方程解的**最大存在区间一定是开区间**，形式为 $(\alpha,\beta),\ (x_0,+\infty),\ (-\infty,x_0)$；
2. 定义在有界闭区域上的解，一定可以向外延拓，直至抵达区域边界。

### 全局存在定理（不作要求）
设方程 $\displaystyle \frac{dy}{dx}=f(x,y)$，$f(x,y)$ 在带状区域 $S:\alpha<x<\beta,\,-\infty<y<+\infty$ 内连续，且存在非负连续函数 $A(x),B(x)$ 满足
$$|f(x,y)|\le A(x)|y|+B(x),\quad x\in(\alpha,\beta)$$
则该微分方程的每一个解，最大存在区间都是完整区间 $(\alpha,\beta)$。

---

## 比较定理及应用
### 第一比较定理
设 $f(x,y),F(x,y)$ 在区域 $G$ 内连续，且处处满足 $f(x,y)<F(x,y),\ (x,y)\in G$。

记：
- $y=\varphi(x)$：初值问题 $(E_1):\displaystyle \frac{dy}{dx}=f(x,y),\ y(x_0)=y_0$ 的解；
- $y=\Phi(x)$：初值问题 $(E_2):\displaystyle \frac{dy}{dx}=F(x,y),\ y(x_0)=y_0$ 的解；
且 $(x_0,y_0)\in G$。

则解满足严格不等式：
$$
\begin{cases}
\varphi(x)<\Phi(x), & x\in(x_0,b)\\
\varphi(x)>\Phi(x), & x\in(a,x_0)
\end{cases}
$$

### 第二比较定理
设 $f(x,y),F(x,y)$ 在区域 $G$ 内连续，且处处满足 $f(x,y)\le F(x,y),\ (x,y)\in G$。

沿用上面两个初值问题的解：
- $y=\varphi(x)$：$(E_1)$ 的右行最小解、左行最大解；
- $y=\Phi(x)$：$(E_2)$ 的右行最大解、左行最小解。

则解满足非严格不等式：
$$
\begin{cases}
\varphi(x)\le\Phi(x), & x\in[x_0,b)\\
\varphi(x)\ge\Phi(x), & x\in(a,x_0]
\end{cases}
$$

---

## 核心定理对比汇总
| 定理 | 核心条件 | 解存在性 | 解唯一性 |
| :--- | :--- | :--- | :--- |
| 皮卡存在唯一性定理 | $f$ 连续 + 对 $y$ 利普希茨 | 局部存在 | 唯一 |
| 佩亚诺存在定理 | 仅 $f$ 连续 | 局部至少1个解 | 不保证唯一 |
| 解延拓定理 | $f$ 在区域内连续 | 解可向外延拓至边界 | 不涉及唯一性 |
| 比较定理 | 右端函数有大小序关系 | 解互相上下控制 | 不涉及唯一性 |