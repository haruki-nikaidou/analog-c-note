# 迟滞比较器

依赖：

* 简单比较器
* 运算放大器：负反馈放大电路

迟滞比较器设有两个阈值，即上升阈值和下降阈值。这两个阈值定义了一个“迟滞窗口”或“死区”，在这个范围内输入信号的变化不会引起输出状态的改变。当输入信号低于下降阈值时，比较器输出一种状态（如低电平）；当输入信号超过上升阈值时，输出另一种状态（如高电平）。只有当输入信号超过这两个阈值之一时，输出状态才会改变。

### 迟滞比较器的实现

根据这个定义，不难猜测，迟滞比较器是通过反馈实现的。那么，应该如何反馈？

答案是，改变基准点，把输出的一部分反馈到基准点上。当从低电平进入高电平时，基准点降低，这样就需要回退更多（降低更多）才能降低回低电平；当从高电平进入低电平时，基准点升高，这样就需要回退更多（升高更多）才能升高回高电平。

基准点降低等同于提高$$u_+$$段电平（或者降低$$u_{-}$$端电平），而基准点升高等同于降低$$u_{+}$$端电平（或者升高$$u_-$$）端电平。

我们希望，在输出为高电平时，基准点降低；在输出为低电平时，基准点升高。所以，应该把输出反馈到$$u_+$$端。

那么，结构就应该是这样。

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption><p>迟滞比较器的结构</p></figcaption></figure>

左边这种称为顺时针迟滞比较器，右边这种称为逆时针迟滞比较器。

### 迟滞比较器的计算

如果学过[「运算放大器：负反馈放大电路」](../../yun-suan-fang-da-qi/fu-fan-kui-fang-da-dian-lu.md)，那么计算迟滞比较器的参数是很简单的。

以顺时针为例

设正反馈系数为$$k$$，$$k$$越接近1，说明反馈越强烈，迟滞窗口越宽。显然，

$$
k=\frac{R_1}{R_1+R_2}
$$

当输出为高电平时，翻转点为

$$
U_{REF+}=U_Hk+U_{REF}(1-k)
$$

当输出为低电平时，翻转点为

$$
U_{REF-}=U_Lk+U_{REF}(1-k)
$$

两个比较阈值的电压宽度，或者说，窗口电压，为

$$
U_{WD}=U_{REF+}-U_{REF-}=k(U_H-U_L)=\frac{R_1}{R_1+R_2}(V_{CC}+V_{EE})
$$

于是，两种迟滞比较器的输入输出特性就是这样：

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption><p>两种迟滞比较器的输入输出特性</p></figcaption></figure>
