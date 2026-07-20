# 第二章：初等积分法
## 1、恰当方程法
考虑微分形式方程：
$$P(x,y)dx + Q(x,y)dy = 0$$
若存在二元函数 $\varPhi(x,y)$，满足
$$d\varPhi(x,y) = P(x,y)dx + Q(x,y)dy$$
则隐式函数 $\boldsymbol{\varPhi(x,y)=C}$ 就是该方程的通解。

### 举例
$$2xy^3dx + 3x^2y^2dy = 0$$
观察可得：$d(x^2y^3)=2xy^3dx+3x^2y^2dy$，
因此 $\boldsymbol{x^2y^3=C}$ 就是该方程的通解。

### 判定定理
设方程 $P(x,y)dx+Q(x,y)dy=0$，$P(x,y),Q(x,y)$ 在区域 $R:\alpha<x<\beta,\ r<y<\delta$ 上连续，且偏导数 $\dfrac{\partial P}{\partial y},\dfrac{\partial Q}{\partial x}$ 在 $R$ 内存在且连续，则：
$$Pdx+Qdy=0 \text{ 为恰当方程} \iff \boldsymbol{\frac{\partial P}{\partial y} = \frac{\partial Q}{\partial x}}$$

## 2、变量分离法
仍对方程 $P(x,y)dx+Q(x,y)dy=0$，若可拆分变量：
$$P(x,y)=P_1(x)P_2(y),\quad Q(x,y)=Q_1(x)Q_2(y)$$
方程改写为（$Q_1(x)P_2(y)\neq0$）：
$$\frac{P_1(x)}{Q_1(x)}dx + \frac{Q_2(y)}{P_2(y)}dy = 0$$
两侧分别积分即可求解。

### 例题
$$(x^2-1)(y^2-1)dx + xydy = 0$$

#### ① 定义域 $(y^2-1)x\neq0$
$$\frac{x^2-1}{x}dx + \frac{y}{y^2-1}dy = 0$$
逐项积分：
$$x^2 - 2\ln|x| + \ln|y^2-1| = C$$
整理：
$$\frac{y^2-1}{x^2}e^{x^2}=C_1 \implies y^2=1+x^2e^{x^2}C_1 \quad(C_1\neq0)$$
$C_1=0$ 时 $y^2-1=0$，也包含在解族内。

#### ② 特解补充
$x=0$ 时；$y=\pm1$ 时，$(y^2-1)dx=0 \implies x=C_2$，为方程特解。

## 3、一阶线性微分方程
标准形式：
$$\frac{dy}{dx}+P(x)y=q(x)$$

#### ① 齐次情形 $q(x)\equiv0$
$$\frac{dy}{dx}+P(x)y=0 \iff \frac{dy}{y}+P(x)dx=0$$
积分：
$$\ln|y|+\int P(x)dx=C_1$$
得通解：
$$\boldsymbol{y=Ce^{-\int P(x)dx}}$$

#### ② 非齐次情形 $q(x)\not\equiv0$
变形：
$$dy+P(x)ydx=q(x)dx$$
引入积分因子 $\mu(x)$，两边同乘：
$$\mu(x)dy+\mu(x)P(x)ydx=\mu(x)q(x)dx$$
令左侧为恰当方程，满足恰当条件：
$$\frac{\partial \mu}{\partial x}=\frac{\partial\big(\mu(x)P(x)y\big)}{\partial y}=P\mu$$
分离变量：
$$\frac{d\mu}{\mu}=Pdx \implies \boldsymbol{\mu=e^{\int P(x)dx}}$$
（积分常数取 $C=1$）

代入得：
$$d(\mu y)=\mu q dx$$
积分：
$$\mu y=\int \mu(x)q(x)dx+C$$
整理得一阶线性非齐次方程通解公式：
$$\boldsymbol{y=e^{-\int P(x)dx}\left(C+\int q(x)e^{\int P(x)dx}dx\right)}$$

### 例题
$$\frac{dy}{dx}+\frac{y}{x}=x^3 \quad(x\neq0)$$
变形：
$$dy+\frac{y}{x}dx=x^3dx$$
积分因子：
$$\mu(x)=e^{\int\frac1x dx}=x$$
乘因子：
$$xdy+ydx=x^4dx \iff d(xy)=d\left(\frac{x^5}{5}\right)$$
积分整理：
$$xy=\frac{x^5}{5}+C \implies \boldsymbol{y=\frac{x^4}{5}+\frac{C}{x}}$$

### 线性方程解的性质
1. 齐次方程 $\dfrac{dy}{dx}+P(x)y=0$ 的解要么恒为 $0$，要么恒不为 $0$，解具有整体性；
2. 一阶线性方程给定初值条件时，解唯一。

## 4、初等变换法
#### ① 可换元型 $\boldsymbol{\dfrac{dy}{dx}=f(x+y)}$
令 $u=x+y$，求导：
$$\frac{du}{dx}=1+\frac{dy}{dx}=1+f(u)$$
化为可分离变量方程求解。

#### ② 齐次微分方程
$P(x,y)dx+Q(x,y)dy=0$ 中 $P,Q$ 为同次齐次函数：
$$P(tx,ty)=t^mP(x,y),\quad Q(tx,ty)=t^mQ(x,y)$$
令换元 $u=\dfrac{y}{x}$，代入求解。

#### ③ 伯努利方程
标准形式：
$$\frac{dy}{dx}+P(x)y=q(x)y^n,\quad n\neq0,1$$
两边同乘 $(1-n)y^{-n}$：
$$(1-n)y^{-n}\frac{dy}{dx}+(1-n)P(x)y^{1-n}=(1-n)q(x)$$
换元 $z=y^{1-n}$，则 $\dfrac{dz}{dx}=(1-n)y^{-n}\dfrac{dy}{dx}$，方程化为一阶线性方程：
$$\frac{dz}{dx}+(1-n)P(x)z=(1-n)q(x)$$
套用一阶线性方程解法即可。

## 5、积分因子法
对一般方程 $P(x,y)dx+Q(x,y)dy=0$，寻找积分因子 $\mu(x,y)$，使得
$$\mu Pdx+\mu Qdy=0$$
成为恰当方程。

恰当条件：
$$\frac{\partial(\mu P)}{\partial y}=\frac{\partial(\mu Q)}{\partial x}$$
展开整理：
$$P\frac{\partial \mu}{\partial y}-Q\frac{\partial \mu}{\partial x}=\left(\frac{\partial Q}{\partial x}-\frac{\partial P}{\partial y}\right)\mu$$

#### 特殊情形
1. 若 $\mu$ 仅依赖 $x$、与 $y$ 无关：$\dfrac{\partial \mu}{\partial y}=0$，方程简化为：
$$-Q\frac{d\mu}{dx}=\left(\frac{\partial Q}{\partial x}-\frac{\partial P}{\partial y}\right)\mu$$
2. 若 $\mu$ 仅依赖 $y$、与 $x$ 无关：$\dfrac{\partial \mu}{\partial x}=0$，方程简化为：
$$P\frac{d\mu}{dy}=\left(\frac{\partial Q}{\partial x}-\frac{\partial P}{\partial y}\right)\mu$$

### 例题1
求解：
$$x^3ydx-2y^2dx+x^4dy=0$$
分组整理：
$$\big(x^3ydx+x^4dy\big)-2y^2dx=0$$
$$x^3d(xy)=2y^2dx$$
观察两组积分因子：$\varPhi_1=xy,\varPhi_2=x$，对应积分因子候选 $\mu_1=x^{-3},\mu_2=y^{-2}$。

设总积分因子 $\mu=\mu_1g_1(\varPhi_1)=\mu_2g_2(\varPhi_2)$，即：
$$y^2g_1(xy)=x^3g_2(x)$$
可取 $g_1(xy)=(xy)^{-2}$，得：
$$\mu=\frac1{x^3}(xy)^{-2}=x^{-5}y^{-2}$$

原方程同乘 $\mu$：
$$\big(x^{-2}y^{-1}-2x^{-5}\big)dx+x^{-1}y^{-2}dy=0$$
凑微分：
$$d\left(-\frac1{xy}+\frac12x^{-4}\right)=0$$
积分：
$$\frac12x^{-4}-\frac1{xy}=C$$
整理显式解：
$$\boldsymbol{y=\frac{2x^3}{2Cx^4+1}}$$
额外补充特解 $x=0,y=0$对应的特解。

### 例题2
求解：
$$y(1+xy)dx-xdy=0$$
展开分组：
$$ydx-xdy+xy^2dx=0$$
利用微分公式 $d\left(\dfrac xy\right)=\dfrac{ydx-xdy}{y^2}$，变形：
$$y^2d\left(\frac xy\right)+xy^2dx=0$$
候选积分因子 $\mu_1=y^{-2},\mu_2=x^{-1}y^{-2}$。
令 $\mu=\mu_1g_1\left(\dfrac xy\right)=\mu_2g_2(x)$，取 $g_1\left(\dfrac xy\right)=1$，得积分因子：
$$\mu=y^{-2}$$

方程同乘 $\mu$：
$$(y^{-1}+x)dx-xy^{-2}dy=0$$
凑微分：
$$d\left(\frac xy+\frac{x^2}{2}\right)=0$$
积分得通解：
$$\frac xy+\frac{x^2}{2}=C$$
整理显式解：
$$\boldsymbol{y=\frac{2x}{2C-x^2}}$$