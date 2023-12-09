---
description: 三极管的原理、公式
layout: editorial
---

# 三极管

依赖

* PN结
* 基尔霍夫电流定律
* 欧姆定律
* 能带与势垒（半导体原理）

### 三极管的工作原理

三极管，也称为双极结型晶体管（BJT），是一种用于放大、开关或调制电子信号的半导体器件。它由三个交替的P型和N型半导体材料层组成，形成两个PN结。这三个层分别被称为发射极（Emitter）、基极（Base）和集电极（Collector）。三极管有两种类型：NPN型和PNP型，它们的工作原理相似，但载流子类型和极性相反。

<figure><img src="../.gitbook/assets/image (14).png" alt=""><figcaption><p>三极管的原理和图示</p></figcaption></figure>

以NPN型三极管为例，NPN型三极管由两个N型半导体（发射极和集电极）和一个P型半导体（基极）组成。

电子穿过发射极和基极之间的PN结，进入基极。但因为基极非常薄，大部分电子并不在基极复合，而是继续向集电极移动。集电极和基极之间施加反向电压，形成反向偏置。这样，从基极到集电极的电子流动受到加速。

因此，基极电流的微小变化会导致从发射极到集电极的电流产生较大的变化，从而实现信号的放大。

### 三极管的电流关系

电流定义如下图。

<figure><img src="../.gitbook/assets/image (15).png" alt=""><figcaption><p>三极管的电流定义</p></figcaption></figure>

电流的定义参照于发射极的电流方向。对于NPN型，发射极是流出的，所以，相对地，基极和集电极是流入的。PNP型相反。

对于NPN管，只有基极点位比发射极高，电流才能流出（三极管才能导通）。PNP管则相反。

由于基尔霍夫电流定律，显然有

$$
i_B+i_C=i_E
$$

当晶体管处于放大状态（基极能够提供足够电流）下，集电极电流受控于基极电流，而与$$u_{CE}$$无关。

$$
i_C = \beta i_B
$$

根据上两式，得出

$$
i_E=(1+\beta)i_B=\frac{1+\beta}{\beta}i_C
$$

### 三极管的伏安特性

晶体管有3个脚，一般用两个伏安特性描述。

#### 输入伏安特性

三极管的输入伏安特性是$$i_B$$和$$u_{BE}$$之间的关系（可能受到$$u_{CE}$$的影响）。

一般情况是$$u_{CE}>0$$，此时

$$
i_B=I_S\left(e^{\frac{u_{BE}}{U_T}}-1\right)
$$

其中$$U_T$$为热电压，是一个与热力学温度成正比的值，300T时约为26mV，$$I_S$$称为反向饱和电流，是晶体管的属性。一般认为，当$$u_{BE}>0.7V$$时，$$i_B$$呈现明显的电流。

当$$u_{CE}=0$$时，呈现一个特殊的曲线。

#### 输出伏安特性

三极管输出伏安特性是在一个确定的$$i_B$$下，$$i_c$$和$$u_{CE}$$之间的关系。

理想的三极管的$$i_c$$应该仅与$$i_B$$成正比，而和$$u_{CE}$$无关，但实际上并非接近完美。

实际的三极管中，当$$u_{CE}$$较小时，会出现饱和区，饱和区$$i_C$$电流随$$u_{CE}$$增大而增大，近似为线性。

饱和区的产生主要是由于基极-发射极（B-E）结的正向偏置和基极-集电极（B-C）结的正向或低反向偏置造成的。

在饱和状态下，基极-发射极结被正向偏置，使得大量载流子（电子）能够从发射极注入到基极。不同于正常的放大工作状态（放大区），在饱和区，基极-集电极结也被正向偏置。这种偏置减少了基极和集电极之间的势垒，允许更多的电子从基极流向集电极。

由于两个结都正向偏置，发射极到集电极的电子流大幅增加，直到达到一个点，即使增加集电极到发射极的电压，也不会有更多的电子能流过这个结构，因为电子的流动已经饱和。

在饱和状态下，集电极到发射极的电压很低，这意味着三极管几乎完全导通，电流达到最大值，但电压降低。在这个状态下，三极管不能有效地放大信号，因为它几乎完全导通，表现得更像一个闭合的开关。

当$$u_{BE}$$很小时，三极管不导通，此时几乎没有电流通过。这个区域叫做截止区。这种工作状态在数字电路（如开关操作）中非常重要，但在模拟电路（如放大器）中通常应避免。