## ME3116AM6G

ME3116 是一款内部集成了 MOSFET 的异步整流降 压型稳压器。它在很宽的输入电压范围内（4.75V-40V） 能够提供高达 1A 的负载能力。ME3116 系统采用 PWM 控制模式，具有很好的瞬态 响应和逐周期限流功能。同时，在轻载条件下系统自动切 换到 PFM 模式，保证较高的轻载效率。ME3116 具有过热关断、输入欠压保护、BS 欠压保护 和短路保护。

### 特点

+ 反馈端基准电压 0.8V
+ 输入电压范围 4.75V to 40V
+ 输出电流高达 1A
+ 工作频率 550KHZ
+ 最大效率 90%
+ 短路保护
+ 较低的关断消耗 IQ =0.7 μA（典型）

### 典型电路

![](/img/ME3116.png)

### 输出电压设置

输出电压设定，需要如上图所示将反馈脚和比例电阻连接。反馈电压为 0.8V，因此通过设定电阻比例来调整输出电压，公式为：


$$
V_o = 0.8\times\frac{R1+R2}{R2}
$$

$R2$ 选择范围通常为 $100Ω-10 KΩ$，给定 $R1$ 和 $R2$ 值再求解 $V_o$  ：

$$
R1=R2\times(\frac{V_o}{0.8}-1)
$$

### 前馈电容选择

![](/img/C1.png)

### 输入电容

$VIN$ 和 $GND$ 之间接一个低 ESR 陶瓷电容 ( $CIN$ )，典型值为 $2.2 μF-10 μF$，该电容能阻值较大的输入瞬态电压。

### 电感选择

$$
L=\frac{(VIN-V_o)*V_o}{VIN*I_{RIPPLE}*f_{SW}}
$$

较大电感值可以减少纹波电流，但却增加电导损耗、磁心损耗，作用于电感和开关器件上的电流应力。这样也需要较大的输出电容，以保证相同的输出电压纹波。合理取值是保证纹波电流为输出直流的 30%。由于纹波电流会随着输入电压增加，因此最大输入电压也相应决定了电感取值。电感的直流寄生电阻是关于效率的一个重要参数。较低的直流寄生电阻需要较大的绕组。效率和磁芯尺寸最优折中是电感铜损等于输出电压的 2%。在 ME3116 带载 1A 甚至更大的情况下，大多数应用的电感最佳选择范围是 $6.8μH-15μH$。采用这样的取值，能够保证 ME3116 达到最大电流而电感也不会饱和。这样避免了 ME3116 进入热保护以及短路或长期过载情况下电感一定几率损坏的情况发生。

### 输出电容

输出电容 $Co$ 的选择取决于允许的最大输出电压纹波。恒定频率下的输出纹波，PWM 模式下的近似公式：

$$
V_{RIPPLE}=I_{RIPPLE}*(ESR+\frac{1}{8*f_{SW}*Co})
$$

ESR（寄生电阻）通常决定了输出电压纹波的大小。这里推荐选择低 ESR 的陶瓷电容。推荐电容值在 $22μF-100μF$ 范围选择，其 ESR 需要低于 $0.1Ω$。

### 电压抬升电容

电压抬升电容 $Cboot$，推荐选值为 $0.15μF$ 或大于该值

## 原理图

![SCH_Schematic](/img/SCH_Schematic.png)

## PCB

![3D_PCB](/img/3D_PCB.png)

![DC-DC 5V](/img/DC-DC-5V.jpg)
