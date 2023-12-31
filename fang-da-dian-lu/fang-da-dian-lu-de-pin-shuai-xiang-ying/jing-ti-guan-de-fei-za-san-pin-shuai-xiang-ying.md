# 晶体管的非杂散频率响应

参考如下图所示的阻容耦合三极管放大电路

<figure><img src="../../.gitbook/assets/image (31).png" alt=""><figcaption><p>阻容耦合放大电路</p></figcaption></figure>

如果说没有C1和C2，那么似乎就不存在阻碍直流的因素了，因此就不存在下限截止频率，或者说$$f_L=0Hz$$

如果说没有旁路电容$$C_L$$，看似就没有阻断高频的作用了，但实际上不是如此。晶体管内部的高频模型中存在3个结电容，它们的存在会降低放大电路的增益；其次，任何两个导体直接，也存在寄生电容，这些都会导致截止频率不能无穷大。

因此，影响放大电路下限截止频率的关键是电路中的隔直电容；影响上限截止频率的是旁路电容。如果没有旁路电容，则需要考虑三极管的高频模型。

### 分析简化

将多个低通模块串联，最终仍然是低通；将多个高通模块串联，最终仍然是高通。其中，中频段增益是各个模块中频段增益的积。这是显然的结论。

串联后的截止频率稍微复杂一些，但基本结论是：

* 越截越窄
* 高通串联后，下限截止频率一定大于每一个的下限截止频率。
* 低通串联后，上限截止频率一定小于每一个的上限截止频率。

更具体地，作为结论

$$
f_{H0}=\frac{1}{K\sqrt{\sum \frac{1}{f_H^2}}}
$$

$$
f_{L0}=K\sqrt{\sum f_L^2}
$$

其中$$K$$是衡量各个模块截止频率差距的量，相差越远，越接近1；当各个模块的截止频率完全相等时，取最大值。

### 拆分与叠加

隔直电容和旁路电容永远都是分开考虑再叠加。

当两种电容同时存在于电路时，电路分析会变得很复杂。为了简化分析，在分析下限截止频率时，只考虑隔直电容，把旁路电容视为开路。在分析上限截止频率时，只考虑旁路电容，而把隔直电容视为断路。

这是因为，隔直电容比旁路电容大得多，因此对于一方，另一方就是短路或者开路。

### 例题

先求解下限截止频率

根据上面的技巧，可以把电路这样分

<figure><img src="../../.gitbook/assets/image (32).png" alt=""><figcaption></figcaption></figure>

显然，这两个电容不能视为短路。

可以看出，左边蓝色的部分是一个低通模块，黄色的部分截止频率为0，红色的部分是另一个低通模块。

根据上面的技巧

$$
\dot{A}_0=\dot{A}_1\dot{A}_2\dot{A}_3=\frac{i_b}{\dot{u}_i}\frac{i_c}{i_b}\frac{\dot{u}_0}{i_c}
$$

对于$$\dot{A}_1$$来说，把电阻并联等效一下，不难得到

$$
\dot{A}_1=\frac{1}{r_{be}}\frac{1}{1+\frac{1}{j\omega (R_B//r_{be}) C_1}}
$$

下限截止频率为

$$
f_{L1}=\frac{1}{2\pi (R_B // r_{be})C_1}
$$

第二部分，显然有

$$
A_{m2}=\beta
$$

以及

$$
f_{L2}=0
$$

第三部分和刚才的第一部分差不多

$$
f_{L3}=\frac{1}{2\pi(R_C+R_L)C_2}
$$

影响上限截止频率的除了三极管高频等效模型以外就那一个旁路电容，所以

$$
f_H=\frac{1}{2\pi(R_C//R_L)C_L}
$$

