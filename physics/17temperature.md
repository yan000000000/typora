### Temperature

measure temperature on Kelvin scale.

* Room temperature is about 290K, 0K is absolute zero

### Triple point of water

$$
T_{3} = 273.16K
$$

at this temperature, liquid water, solid ice and water vapor can coexist

### 测量未知气体的温度

$$
T = 273.16K(\lim_{gas\rightarrow 0}\frac{p}{p_{3}})
$$

 $p_{3}$ 是温度处在三相点时的压强

### 摄氏度和华氏度

$$
T_{c} = T - 273.15
$$

$$
T_{F} = \frac{9}{5}T_{c} + 32
$$

## thermal expansion（热膨胀）

### 线性膨胀

$$
\Delta L = L\alpha \Delta T
$$

其中 $\alpha$ 是线性膨胀系数

### 体积膨胀

$$
\Delta V = V\beta \Delta T
$$

其中 $\beta$​ 是体积膨胀系数

### 关系

通过计算我们有线性膨胀和体积膨胀之间存在一定关系
$$
\beta = 3\alpha
$$

## 热容

### 热容(heat capacity)

单位温度储存的热量
$$
Q = C\Delta T = C(T_{f}-T_{i})
$$

### 比热容(specific heat)

单位温度，单位质量所储存的热量
$$
Q = cm \Delta T = cm(T_{f}-T_{i})
$$

### 摩尔比热容(molar specific heat)

跟比热容相比把质量改成摩尔了

## 热力学

### 热功

$$
W = \int_{}^{}dW = \int_{}^{}dFx = \int_{}^{}d \ psx = \int_{v_{i}}^{v_{f}}p dV
$$

### 热力学第一定律

$$
\Delta E_{internal} = Q - W
$$

or
$$
d\Delta E = dQ - dW
$$

### 热传导率

$$
P_{cond} =\frac{Q}{t} = kA\frac{T_{H}-T_{C}}{L} 
$$

其中 $A$ 为面积， $L$ 为厚度,  $k$​ 为热导率，只跟材料有关

#### 多材料热传导

同一时间内每种材料内的热传导率是相同的

### 热阻

$$
R = \frac{L}{k}
$$

其中 $L$ 为厚度， $k$ 为热阻

### 电磁波能量传输率

$$
P_{rad} = \sigma \epsilon AT^{4}
$$

其中 $A$ 为表面积， $T$ 为该面积的温度（开尔文），  $\sigma$ 是一个常数 stefan-Boltzmann constant, $\epsilon$ 为表面的发射率（0—1）

## 

### 理想气体状态方程

$$
pV = nRT
$$

我们把一个常数  $k = \frac{R}{N_{A}}$ 代入这个方程，我们有
$$
pV = NkT
$$

### 等温下的功

$$
W = nRTln\frac{V_{f}}{V_{i}}
$$

### root mean square speed

$$
V_{rms} = \sqrt{\frac{3RT}{M}}
$$

注意这里的 $M$ 是指一个分子的质量

### 分子动能

$$
K_{avg} = \frac{1}{2}mv_{avg}^{2}\\
= \frac{1}{2}m(v_{rms}^{2})\\
=\frac{1}{2}m\frac{3RT}{M}
$$

对于 $\frac{m}{M}$, 我们有 $N_{A} = \frac{m}{M}$ ， 所以我们有
$$
K_{avg} = \frac{3RT}{2N_{A}}
$$
令 $k = \frac{R}{N_{A}}$, 我们有
$$
K_{avg} = \frac{3}{2}kT
$$

### 平均自由径

$$
\lambda = \frac{1}{\sqrt{2}\pi d^2N/V}
$$

### 摩尔速度分布

麦克斯韦速度分布定律
$$
P(v) = 4\pi (\frac{M}{2\pi RT})^{\frac{3}{2}}v^{2}e^{-\frac{Mv^{2}}{2RT}}
$$
这里 $M$ 为摩尔质量， $R$ 为气体常量， $T$ 为气体温度， $v$ 是摩尔速度



### 单原子理想气体内能

$$
E_{int} = (nN_{A})K_{avg} = (nN_{A})K_{avg} = (nN_{A})\frac{3}{2}kT\\
=\frac{3}{2}nRT
$$

### 恒容摩尔比热容

我们有
$$
Q = C_{v}n \Delta T
$$
这里 $n$ 为物质的量， $C_{v}$ 为摩尔比热容

将它代入热力学第一定律我们有
$$
\Delta E_{int} = Q-W \\
\Delta E_{int} = C_{v}n\Delta T - W
$$
因为恒容， $W = 0$ 那么摩尔比热容可以表示为
$$
C_{v} = \frac{\Delta E_{int}}{n\Delta T}
$$
由上面我们知道单原子理想气体的内能 $\Delta E_{int} = \frac{3}{2}nRT$ ,代入我们有
$$
C_{v} = \frac{3}{2}R
$$




## 



### 熵的变化量

$$
\Delta S = S_{f}-S_{i} = \int_{i}^{f}\frac{dQ}{T}
$$

