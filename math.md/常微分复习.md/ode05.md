# 第五章：高阶微分方程
## 一、自治微分方程降阶
有一类微分方程（不包含明显自变量），这类方程称为**自治的微分方程**。

如 $n$ 阶自治微分方程：
$$
F\left(y,\frac{dy}{dx},\frac{d^2y}{dx^2},\dots,\frac{d^ny}{dx^n}\right) = 0
$$

令 $z=\displaystyle\frac{dy}{dx}$，则方程化为关于 $z,x$ 的 $n-1$ 阶微分方程：
$$
F\left(y,z,\frac{dz}{dx},\dots,\frac{d^{n-1}z}{dx^{n-1}}\right) = 0
$$

## 二、单摆方程实例
记 $l$：单摆摆长，$x$：偏转角
运动方程：
$$
ml \frac{d^2x}{dt^2} = -mg\sin x \implies \frac{d^2x}{dt^2} + a^2\sin x = 0
$$

两边同乘 $\displaystyle\frac{dx}{dt}$：
$$
\frac{dx}{dt}\frac{d^2x}{dt^2} + a^2\sin x \frac{dx}{dt} = 0
$$

直接积分一次：
$$
\frac12\left(\frac{dx}{dt}\right)^2 - a^2\cos x = -\frac12 C_1
$$
整理得：
$$
\frac{dx}{dt} = \pm\sqrt{2a^2\cos x - C_1}
$$

### 小角度近似（$x$ 很小，$\sin x\approx x$）
方程简化为简谐运动：
$$
\frac{d^2x}{dt^2} + a^2 x = 0
$$

两边同乘 $\displaystyle\frac{dx}{dt}$：
$$
\frac{dx}{dt}\frac{d^2x}{dt^2} + a^2 x \frac{dx}{dt} = 0
\iff
\left(\frac{dx}{dt}\right)^2 + a^2 x^2 = C_1^2 \quad (C_1>0)
$$

分离变量：
$$
\frac{dx}{dt} = \pm\sqrt{C_1^2 - a^2 x^2}
$$

积分求解：
$$
\pm\int \frac{dx}{\sqrt{C_1^2 - a^2 x^2}} = t + C_2
\implies
x = A\sin(at + D)
$$
其中 $A=\displaystyle\frac{C_1}{a}>0,\ D=aC_2$。

> 结论：若不做 $\sin x\approx x$ 近似，单摆周期随振幅改变，**无等时性**。

---

# 三、解对参数与初值的连续依赖性
## 定理（初值扰动连续依赖）
设 $n$ 维向量值函数 $\boldsymbol{f}(x,\boldsymbol{y},\boldsymbol{\lambda})$ 在区域
$$
G:\ |x|\le a,\ |\boldsymbol{y}|\le b,\ |\boldsymbol{\lambda}-\boldsymbol{\lambda}_0|\le c
$$
上连续，初值问题
$$
\begin{cases}
\displaystyle\frac{d\boldsymbol{y}}{dx} = \boldsymbol{f}(x,\boldsymbol{y},\boldsymbol{\lambda})\\
\boldsymbol{y}(0) = \boldsymbol{0}
\end{cases} \tag{E}
$$
且 $\boldsymbol{f}$ 对 $\boldsymbol{y}$ 满足**利普希茨条件**：
$$
\big|\boldsymbol{f}(x,\boldsymbol{y}_1,\boldsymbol{\lambda}) - \boldsymbol{f}(x,\boldsymbol{y}_2,\boldsymbol{\lambda})\big| \le L \big|\boldsymbol{y}_1 - \boldsymbol{y}_2\big|,\quad L\ge 0
$$

记 $M$ 为 $|\boldsymbol{f}(x,\boldsymbol{y},\boldsymbol{\lambda})|$ 在区域 $G$ 上的一个上界，取
$$
h = \min\left\{a,\frac{b}{M}\right\}
$$
则初值问题 $(E)$ 的解 $\boldsymbol{y} = \boldsymbol{\varphi}(x,\boldsymbol{\lambda})$ 在区域
$$
D:\ |x|\le h,\ |\boldsymbol{\lambda}-\boldsymbol{\lambda}_0|\le c
$$
上**连续**。

> 注：$|\boldsymbol{y}|$ 为向量范数，定义
> $$|\boldsymbol{y}| = \max\big\{|y_1|,|y_2|,\dots,|y_n|\big\}$$
> 该定理形式与皮卡存在唯一性定理类似。

## 推论（初值点 $x_0,\boldsymbol{y}_0$ 扰动）
设 $n$ 维向量值函数 $\boldsymbol{f}(x,\boldsymbol{y})$ 在区域
$$
R:\ |x-x_0|\le a,\ |\boldsymbol{y}-\boldsymbol{y}_0|\le b
$$
上连续，且对 $\boldsymbol{y}$ 满足利普希茨条件；初值问题
$$
\frac{d\boldsymbol{y}}{dx} = \boldsymbol{f}(x,\boldsymbol{y}),\quad \boldsymbol{y}(x_0) = \boldsymbol{\eta}
$$
记 $M$ 为 $|\boldsymbol{f}(x,\boldsymbol{y})|$ 在 $R$ 上的上界，$h=\min\left\{a,\displaystyle\frac{b}{M}\right\}$，则解在区域
$$
Q:\ |x-x_0|\le \frac{h}{2},\ |\boldsymbol{\eta}-\boldsymbol{y}_0|\le \frac{b}{2}
$$
上关于 $(x,\boldsymbol{\eta})$ 连续。

## 定理（整体区间上初值连续依赖）
设 $n$ 维向量值函数 $\boldsymbol{f}(x,\boldsymbol{y})$ 在 $Oxy$ 平面有界闭区域 $G$ 连续，对 $\boldsymbol{y}$ 满足局部利普希茨条件。
设 $\boldsymbol{y}=\boldsymbol{\xi}(x)$ 是方程 $\displaystyle\frac{d\boldsymbol{y}}{dx}=\boldsymbol{f}(x,\boldsymbol{y})$ 的一个解，其最大存在区间为 $J$，任取闭区间 $[a,b]\subset J$。

则 $\exists\ \delta>0$，对任意初值 $(x_0,\boldsymbol{\eta})$ 满足
$$
a\le x_0\le b,\quad \big|\boldsymbol{\eta}-\boldsymbol{\xi}(x_0)\big|\le \delta
$$
柯西问题
$$
(E):\ \frac{d\boldsymbol{y}}{dx} = \boldsymbol{f}(x,\boldsymbol{y}),\quad \boldsymbol{y}(x_0) = \boldsymbol{\eta}
$$
的解 $\boldsymbol{y}=\boldsymbol{\varphi}(x,x_0,\boldsymbol{\eta})$ 在闭区域
$$
D_\delta:\ a\le x\le b,\ a\le x_0\le b,\ \big|\boldsymbol{\eta}-\boldsymbol{\xi}(x_0)\big|\le \delta
$$
上连续。

---

# 四、解对初值与参数的连续可微性
（解 $\boldsymbol{y}=\boldsymbol{\varphi}(x,x_0,\boldsymbol{y}_0,\boldsymbol{\lambda})$ 关于 $x_0,\boldsymbol{y}_0,\boldsymbol{\lambda}$ 可微）

仅讨论标准形式方程：
$$
\frac{d\boldsymbol{y}}{dx} = \boldsymbol{f}(x,\boldsymbol{y},\boldsymbol{\lambda}),\quad \boldsymbol{y}(0) = \boldsymbol{0}
$$
（一般初值方程可通过变量变换化为该形式）

## 定理
设 $\boldsymbol{f}(x,\boldsymbol{y},\boldsymbol{\lambda})$ 在区域
$$
G:\ |x|\le a,\ |\boldsymbol{y}|\le b,\ |\boldsymbol{\lambda}-\boldsymbol{\lambda}_0|\le c
$$
上连续，且对 $\boldsymbol{y}$ 有**连续偏微商**；
记 $M$ 为 $|\boldsymbol{f}|$ 在 $G$ 上界，$h=\min\left\{a,\displaystyle\frac{b}{M}\right\}$，则方程的解 $\boldsymbol{y}=\boldsymbol{\varphi}(x,\boldsymbol{\lambda})$ 在区域
$$
D:\ |x|\le h,\ |\boldsymbol{\lambda}-\boldsymbol{\lambda}_0|\le c
$$
上**连续可微**。

## 推论（初值 $x_0,\boldsymbol{\eta}$ 情形）
设 $n$ 维向量函数 $\boldsymbol{f}(x,\boldsymbol{y})$ 在区域
$$
R:\ |x-x_0|\le a,\ |\boldsymbol{y}-\boldsymbol{y}_0|\le b
$$
连续，且对 $\boldsymbol{y}$ 有连续偏导数 $\boldsymbol{f}_y'(x,\boldsymbol{y})$，则初值问题
$$
\frac{d\boldsymbol{y}}{dx} = \boldsymbol{f}(x,\boldsymbol{y}),\quad \boldsymbol{y}(x_0) = \boldsymbol{\eta}
$$
的解 $\boldsymbol{y}=\boldsymbol{\varphi}(x,\boldsymbol{\eta})$ 在区域
$$
D:\ |x-x_0|\le \frac{h}{2},\ |\boldsymbol{\eta}-\boldsymbol{y}_0|\le \frac{b}{2}
$$
上连续可微，其中 $h=\min\left\{a,\displaystyle\frac{b}{M}\right\}$，$M=\sup\limits_R|\boldsymbol{f}|$。