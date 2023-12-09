# MOSFET

依赖：

* JFET

<figure><img src="../.gitbook/assets/image (13).png" alt=""><figcaption><p>MOSFET的符号定义</p></figcaption></figure>

MOSFET 的符号定义如上图所示，N沟道的箭头指向栅极，这与$$U_G>U_S$$相反。箭头所在的那一极始终是S极，并且指示了S极的正确电流方向

### 耗尽型MOSFET的特性

耗尽型MOSFET与JFET基本一致，关键指标的定义和公式也相同，唯一的区别是，MOSFET允许$$u_{GS}>0$$。

### 增强型MOSFET的特性

增强型MOSFET的特性基本上和JFET相反。

#### 开启电压

与JFET的关闭电压相反，MOSFET有开启电压$$U_{GSTH}$$，只有$$U_{GS}$$越过了开启电压，MOSFET才能导通，否则电流$$i_D$$为0。

一般MOSFET的开启电压在0.5V到3V之间。

#### 恒流区转移特性

增强型MOSFET有类似JFET的K参数，在恒流区，有近似式

$$
i_D = K(u_{GS}-U_{GSTH})^2
$$

K的单位同样是$$A/V^2$$

#### 可变电阻区的边界

和JFET类似，随着$$U_{GS}$$的增加，沟道大小增加，分界点$$U_{GSdv}$$也在增加，且满足

$$
U_{GSdv}=U_{GS}-U_{GSTH}
$$

其他特性基本相同
